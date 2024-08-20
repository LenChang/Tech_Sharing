> Official Doc: https://docs.python.org/3/library/asyncio-task.html#
# Comparison
| PY | JS
|---|---
| PY is single-process arch with **blocking I/O** | Node.js’s single-threaded architecture and **non-blocking I/O**
| await: make it **non-blocking** | await: make it **blocking**

# Example
## await
```
import asyncio
import time

async def say_after(delay, what):
    await asyncio.sleep(delay)
    print(what)

async def main():
    print(f"started at {time.strftime('%X')}")

    await say_after(1, 'hello')
    await say_after(2, 'world')

    print(f"finished at {time.strftime('%X')}")

asyncio.run(main())
```
## await with "asyncio tasks"
> When you call create_task, the Task is **immediately** scheduled for execution on the even loop. This means, if a context switch takes place after you called create_task for all your coroutines (as in your first example), any number of them may immediately start executing, **without** you having to await them explicitly.
```
...
async def main():
    task1 = asyncio.create_task(
        say_after(1, 'hello'))

    task2 = asyncio.create_task(
        say_after(2, 'world'))

    print(f"started at {time.strftime('%X')}")

    # Wait until both tasks are completed (should take
    # around 2 seconds.)
    await task1
    await task2

    print(f"finished at {time.strftime('%X')}")
...
```

# Reference
- https://www.geeksforgeeks.org/why-node-js-is-a-single-threaded-language/
- https://stackoverflow.com/questions/76107909/when-should-i-use-asyncio-create-task

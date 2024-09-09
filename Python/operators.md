# Overview
| Python               | Javascript                    
| --- |---
| and | &&
| or  | \|\|
| not(...) | !(...)
| *args | ...args|
## Python
### *args
- It will give you **all** positional arguments as a **tuple**
```python
def foo(*args):
    for a in args:
        print(a)        

foo(1)
# 1

foo(1, 2, 3)
# 1
# 2
# 3
```
### **kwargs
- It will give you **all** keyword arguments as a **dictionary**
```python
def bar(**kwargs):
    for a in kwargs:
        print(a, kwargs[a])  

bar(name='one', age=27)
# name one
# age 27
```

# Reference
- [PY: *args && **args](https://stackoverflow.com/questions/36901/what-does-double-star-asterisk-and-star-asterisk-do-for-parameters)
- [JS: ...args](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

> yield is a kind of **return** and it will convert the function as a generator
# Iterables, Iterators and Generators
> Generators = Iterators are part of Iterables
## Iterables
- Everthing you can use ```for...in...``` on is an iterable
### Example
- ```mylist = [x*x for x in range(3)]```
## Generators
- A kind of iterable that you can only iterate over once.
### Example
- ```mylist = (x*x for x in range(3))```

# Case Study
## Trigger the generator manually
```python
def foo():
  print("starting...")
  while True:
    res = yield 4
    print("res:",res)
g = foo()
print(next(g))
print("*"*20)
print(g.send(7))
```
## Trigger the generator by for...in
```python
def nextSquare():
    i = 1
 
    # An Infinite loop to generate squares
    while True:
        yield i*i
        i += 1  # Next execution resumes
        # from this point
 
 
# Driver code to test above generator
# function
for num in nextSquare():
    if num > 100:
        break
    print(num)
```

# Reference
- https://blog.csdn.net/mieleizhi0522/article/details/82142856/
- https://www.geeksforgeeks.org/use-yield-keyword-instead-return-keyword-python/

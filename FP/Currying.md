# Currying
## Definition
> Currying is a transformation of functions that translates a function from callable as f(a, b, c) into callable as f(a)(b)(c). 
> Currying doesn’t call a function. It just transforms it.

> Curring can help us to sepearate *Setting* and *Data*, and then we could make **lazy evaluation**

## Example
```
// num is setting
const add = (num, data) => num + data;

const add = (num) => {
  return (data) => num + data;
};

const addNum1 = add(1); // your setting is "add num 1"
const result = addNum1(3) // data is "3" and your action is "add number 1". So the result is 4
```
## Library
- https://lodash.com/docs/4.17.15#curry
- https://ramdajs.com/docs/#curry

## Sub-topics which is related to Currying
### Lazy evaluation
> Delay your **complicated execution** until you really want it

#### Sample Code
```
// Prepare your setting first
const addNum1 = add(1);
// Do the rest of actions
// ...

// Run it until you need it.
const result = addNum1(100);
```

## Reference
- https://javascript.info/currying-partials
- https://fullstackladder.dev/blog/2020/09/25/mastering-rxjs-10-functional-programming-basic-patterns/

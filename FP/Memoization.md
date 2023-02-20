# Overview
> To execute a method, save its output and return it for future invocations if **input is same** as before
## Sample Code
```
function parseObject(result) {
  const parsedObject = {
    /* Plus some other props */
  }
  let computedValue = null
  Object.defineProperty(parsedObject, 'computedValue', {
    get() {
      if (computedValue) return computedValue
      computedValue = superSlowMethod(this.parameter)
      return computedValue
    }
  })
  
  reutrn parsedObject
}
```
## Library
- _.memoize (lodash)

## Q&A
### What's wrong with this code ?
```
const { memoize } = require('lodash');

const func = (arg1, arg2) => `${arg1} ${arg2}`;
const funcM = memoize(func);

console.dir(funcM('John', 'Doe')); // => "John Doe"
console.dir(funcM('John', 'FooBar')); // => "John Doe" (cache hit)
console.dir(funcM.cache.size); // => 2
```
#### Answer
> Resolver Function
##### The solution
```
const { memoize } = require('lodash');

const func = (arg1, arg2) => `${arg1} ${arg2}`;
const resolver = (arg1, arg2) => JSON.stringify([arg1, arg2]);
const funcM = memoize(func, resolver);

console.dir(funcM('John', 'Doe')); // => "John Doe"
console.dir(funcM('John', 'FooBar')); // => "John FooBar"
console.dir(funcM.cache.size); // => 2
```


# Reference
- https://thoughts.travelperk.com/optimizing-js-with-lazy-evaluation-and-memoization-9d0cd8c30cd4
- https://lodash.com/docs/4.17.15#memoize
- https://javascript.plainenglish.io/advanced-memoization-for-javascript-functions-with-lodash-memoize-12677b07e9bc

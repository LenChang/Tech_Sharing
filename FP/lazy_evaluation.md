# Question: How to solve this problem ?
```
function parseObject(result) {
  return {
    computedValue: superSlowMethod(result.parameter),
    /* Plus some other props */
    /*...*/
  }
}
```
## Issues
- We need to call function: parseObject thouands of times
- We have less chance to call computedValue

## Solution 1
> Break the access flow
```
// Instead of doing this
console.log('The value is: ' + parsedObject.computedValue)

// We would do this
console.log('The value is: ' + superSlowMethod(parsedObject.parameter))
```

## Solution 2 (lazy evaluation)
Key method: `Object.defineProperty`

```
function parseObject(result) {
  const parsedObject = {
    /* Plus some other props */
  }
  Object.defineProperty(parsedObject, 'computedValue', {
    get() {
      return superSlowMethod(this.parameter)
    }
  })  
  reutrn parsedObject
}
```

# Reference
- https://thoughts.travelperk.com/optimizing-js-with-lazy-evaluation-and-memoization-9d0cd8c30cd4

# Agenda
## Overview
> A shallow copy of an object is a copy whose properties share the same references

# Example
## arry.filter()
```
var Arr = [{name:'Learning'},{name:'Questing'}]
var Arr2 = Arr.filter(it=> true);
Arr2[0].name = 'Stack-Over-Flow';
console.log(Arr[0].name) // Stack-Over-Flow
```
### Solution
#### Destructuring assignment
```
const Arr2 = Arr
  .filter(it => true)
  .map(obj => ({ ...obj }));
```
#### lodash - cloneDeep
```
const Arr2 = Arr
  .filter(it => true)
  .map(obj => _.cloneDeep(obj));
```

### Reference
- https://stackoverflow.com/questions/63941282/does-array-filter-create-a-new-array


# Ref Docs
- https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy

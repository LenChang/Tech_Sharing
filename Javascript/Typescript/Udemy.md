# Overview
> https://www.udemy.com/course/understanding-typescript/
- The memo of learning the course: Understanding TypeScript

# The usage which you may forget..
## Tuples
```
let ourTuple: [number, boolean, string];
```
- https://www.udemy.com/course/understanding-typescript/learn/lecture/16888072
#### Ref Docs
- https://www.w3schools.com/typescript/typescript_tuples.php
## unknown
> **unknown** is the stronger restricted **any**
- https://www.udemy.com/course/understanding-typescript/learn/lecture/16888108#content
## never
```
function generateErr (): never {
  throw { msg:'test', errCode:500 }
}
```
- https://www.udemy.com/course/understanding-typescript/learn/lecture/16888110#content

# Clean Up Your Code by Removing ‘if-else’ Statements
> It could be solved by the strategy pattern !!
## if-else
```
function action(ranking){
  if(ranking === 'A'){
    travel()
  }
  else if (ranking === 'B'){
    shopping()
  }
  else if (ranking === 'C'){
    watchTV()
  }
  else if (ranking === 'D') {
    review()
  }
}
```
## switch
```
function action(ranking){
  switch(ranking){
    case 'A':
      travel()
      break
    
    case 'B':
      shopping()
      break
    case 'C':
      watchTV()
      break
    
    case 'D':
      review()
      break
  }
}
```
## Key-value
```
const strategies = {
  'A': travel,
  'B': shopping,
  'C': watchTV,
  'D': review
}
function action(ranking){
  let strategy = strategies[ranking]
  strategy()
}
```
## Map
```
const strategies = new Map([
  ['A', travel],
  ['B', shopping],
  ['C', watchTV],
  ['D', review]
])

function action(ranking){
  let strategy = strategies.get(ranking)
  strategy()
}
```
# Reference
- https://bytefish.medium.com/clean-up-your-code-by-removing-if-else-statements-31102fe3b083
- https://refactoring.guru/design-patterns/strategy

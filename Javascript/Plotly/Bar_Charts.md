# Introduction
- https://plotly.com/javascript/bar-charts/

# Use Case
## Upper & Lower Bound
### Sample Code
```
const data = [{
  ...
  error_y: {
                type: 'data',
                array: [2, 1, 3, 2, 0], // Upper bound errors
                arrayminus: [2, 2, 1, 2, 0], // Lower bound errors
                visible: true,
                color: 'blue',
                width: 20,
                thickness: 6
            },
}];
```

## transparency
### Sample Code
```
const data = [{
  x: ['A', 'B', 'C', 'D', 'E'],
  y: [20, 14, 23, 25, 22],
  type: 'bar',
  marker: {
  	color: 'rgba(255, 0, 0, 0.5)' // Red color with 50% transparency
  }
```

## Adjust the y-axis base
### Sample Code
```
const data = [
 {
    x: ['giraffes', 'orangutans', 'monkeys'],
    y: [20, 14, 23],
    base:[10,-10], // the default offset is 0
    type: 'bar'
  }
];
```
### Reference
- https://plotly.com/javascript/bar-charts/#customizing-individual-bar-base

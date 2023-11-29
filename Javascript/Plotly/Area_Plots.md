# Overview
> fill: 'tozeroy'
- Make a range
# Sample Code
```
var trace1 = {
  x: [1, 2, 3, 4],
  y: [0, 2, 3, 5],
  fill: 'none',
  type: 'scatter'
};

var trace2 = {
  x: [1, 2, 3, 4],
  y: [3, 5, 1, 7],
  fill: 'tonexty',
  type: 'scatter'
};

var data = [trace1, trace2];

Plotly.newPlot('myDiv', data);
```
# Reference
- https://stackoverflow.com/questions/40637215/area-range-with-plotly-js
- https://plotly.com/javascript/filled-area-plots/

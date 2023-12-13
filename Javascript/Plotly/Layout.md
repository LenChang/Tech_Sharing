# Case
## Legend
### The order of legends
> https://plotly.com/javascript/reference/#layout-legend-traceorder
- traceorder
  - Examples: "reversed", "grouped", "reversed+grouped", "normal"
#### Ref
- https://community.plotly.com/t/customizing-the-order-of-legends/12668
- https://stackoverflow.com/questions/56808693/customizing-the-order-of-legends-in-plotly

### Remove the base line y = 0
> https://plotly.com/javascript/reference/#layout-xaxis-zeroline
```
"layout": {
    ...,
    "yaxis": {
      "zeroline": false
    }
  }
```
#### Ref
- https://community.plotly.com/t/how-to-remove-the-axis-lines-in-plotly/41828

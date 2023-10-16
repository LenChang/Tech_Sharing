# Overview
> https://www.npmjs.com/package/highcharts-angular
# Case Study
## General
### Update the chart
```
  <highcharts-chart 
    [Highcharts]="Highcharts"
    [options]="chartOptions"
    [(update)]="updateFlag"
    >
  </highcharts-chart>
```
#### Sample Code
- https://stackblitz.com/edit/highcharts-angular-optimal-way-to-update?file=src%2Fapp%2Fapp.component.html

### Specify a fixed width for column or bar points
> pointWidth
#### Docs
- https://api.highcharts.com/highcharts/plotOptions.columnrange.pointWidth
## BoxPlot
> https://zhuanlan.zhihu.com/p/347067055
- More Samples https://api.highcharts.com/highcharts/series.boxplot
### Draw the outliers on BoxPlot
- https://www.highcharts.com/forum/viewtopic.php?t=45383
### Calculate the info. of BoxPlot
- https://stackoverflow.com/questions/30893443/highcharts-boxplots-how-to-get-five-point-summary
## columnrange
> https://www.highcharts.com/demo/highcharts/columnrange
### Adjust the opacity
- https://api.highcharts.com/highcharts/plotOptions.columnrange.opacity


# Reference
- https://www.npmjs.com/package/highcharts-angular

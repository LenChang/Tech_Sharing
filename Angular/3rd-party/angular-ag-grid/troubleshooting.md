# Formatting
> https://blog.ag-grid.com/formatting-numbers-strings-currency-in-ag-grid/#passing-parameters
- The column definitions for these are as follows:
```
    {
      field: 'number',
    },
    {
      headerName: 'Number Formatted',
      field: 'number',
      valueFormatter: params => params.data.number.toFixed(2),
    },
```
# Cell Comp: Prevent cell comp. affect parent's selection
> e.g. Do something on cell comp. would affect parent's selection
- https://www.w3schools.com/jsref/event_stoppropagation.asp
# Validator: How to make cell edit allow only numbers ?
- https://stackoverflow.com/questions/63820281/ag-grid-cell-edit-allow-only-numbers
```
// The key point is "valueSetter"
{
    headerName: "Age",
    field: "age",
    width: 100,
    editable: true,
    sortable: true,
    filter: 'agTextColumnFilter',
    floatingFilter: true,
    floatingFilterComponentParams: { suppressFilterButton: true },
    valueSetter: (params: ValueSetterParams) => {  //to make sure user entered number only
      var newValInt = parseInt(params.newValue);
      var valueChanged = params.data.age !== newValInt;
      if (valueChanged) {
        params.data.age = newValInt ? newValInt : params.oldValue;
      }
      return valueChanged;
    }
}
```
## Reference
  - https://www.ag-grid.com/javascript-data-grid/value-setters/#value-setter
  - https://www.ag-grid.com/angular-data-grid/cell-editing/
  - https://stackoverflow.com/questions/52710350/ag-grid-better-way-for-validation-row-valuesetter


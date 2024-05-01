# Overview
> [Quick Start](https://ag-grid.com/angular-data-grid/)
- [Custom Components](https://ag-grid.com/angular-data-grid/components/)
  - Registering Custom Components
  - Providing Additional Parameters
  - Child to Parent Communication :star:

# General Case
## READ
### Get all rows and selected rows
> https://stackoverflow.com/questions/50697232/how-can-i-get-all-the-rows-of-ag-grid
- get selected rows
```
api.getSelectedRows()
```
- get all rows
```
getAllRows() {
  let rowData = [];
  this.gridApi.forEachNode(node => rowData.push(node.data));
  return rowData;
}
```

## UPDATE
- [Updating Row Data](https://ag-grid.com/angular-data-grid/data-update-row-data/)
- [Single Row / Cell Updates (Official Docs)](https://ag-grid.com/angular-data-grid/data-update-single-row-cell/)
### Add row(s)
```
// add
this.gridOptions.rowData.push(row)
this.gridApi.setRowData(this.gridOptions.rowData)
```
- Reference
  - https://stackoverflow.com/questions/38505806/add-remove-rows-in-ag-grid

### Remove rows(s)
```
// remove
this.gridOptions.rowData.splice(selectedRow.rowIndex, 1)
this.gridApi.setRowData(this.gridOptions.rowData)
```
- Reference
  - https://stackoverflow.com/questions/38505806/add-remove-rows-in-ag-grid

# Cell Components
> [Official Doc](https://www.ag-grid.com/angular-data-grid/component-cell-renderer/)
## Examples
- [Sample Code](https://www.ag-grid.com/angular-data-grid/component-cell-renderer/)

# Troubleshooting
## Cell Comp: Prevent cell comp. affect parent's selection
> e.g. Do something on cell comp. would affect parent's selection
- https://www.w3schools.com/jsref/event_stoppropagation.asp
## Validator: How to make cell edit allow only numbers ?
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
- Reference
  - https://www.ag-grid.com/javascript-data-grid/value-setters/#value-setter
  - https://www.ag-grid.com/angular-data-grid/cell-editing/

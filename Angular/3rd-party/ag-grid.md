# Problem Collection
## Add / Remove row(s) in ag-grid
```
// add
this.gridOptions.rowData.push(row)
this.gridApi.setRowData(this.gridOptions.rowData)

// remove
this.gridOptions.rowData.splice(selectedRow.rowIndex, 1)
this.gridApi.setRowData(this.gridOptions.rowData)
```
### Reference
- https://stackoverflow.com/questions/38505806/add-remove-rows-in-ag-grid
## How to make cell edit allow only numbers ?
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
### Reference
- https://www.ag-grid.com/javascript-data-grid/value-setters/#value-setter
- https://www.ag-grid.com/angular-data-grid/cell-editing/

# Problem Collection
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

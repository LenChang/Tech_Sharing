# Overview
> [Official Docs](https://github.com/ng-select/ng-select)
- [Demo](https://ng-select.github.io/ng-select#/data-sources)

# Feature
## What's the meaning of [appendTo] ?
> If you embed ng-select into ag-grid cell comp. you may need this to fix your content position
- Append dropdown to body or any other element using css selector. For correct positioning body should have position:relative
- [Doc](https://github.com/ng-select/ng-select?tab=readme-ov-file#step-4-optional-configuration)
  - [Demo](https://github.com/ng-select/ng-select/tree/master/src/demo/app/examples/append-to-example)
## Call a function when [addTag] is used in ng-select
- https://stackoverflow.com/questions/65826059/how-to-call-a-function-when-addtag-is-used-in-ng-select
```
// arrow function
addNewCompany = (term:string) =>{
   console.log(term);
   this.selected=term;
     
}
```

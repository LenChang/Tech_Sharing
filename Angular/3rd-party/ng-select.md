# Overview
- https://github.com/ng-select/ng-select (Main Page)
- https://ng-select.github.io/ng-select#/data-sources (Demo)

# Feature
## Call a function when [addTag] is used in ng-select
- https://stackoverflow.com/questions/65826059/how-to-call-a-function-when-addtag-is-used-in-ng-select
```
// arrow function
addNewCompany = (term:string) =>{
   console.log(term);
   this.selected=term;
     
}
```

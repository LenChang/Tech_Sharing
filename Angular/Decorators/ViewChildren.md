# Overview
> View queries are set before the **ngAfterViewInit** callback is called.
## Sample
### template
```
<div *ngFor="let v of views">
    <customcomponent #cmp></customcomponent>
</div>
```
### component
```
import { ViewChildren, QueryList } from '@angular/core';

/** Get handle on cmp tags in the template */
@ViewChildren('cmp') components:QueryList<CustomComponent>;

ngAfterViewInit(){
    // print array of CustomComponent objects
    console.log(this.components.toArray());
}
```

# Reference
- https://angular.io/api/core/ViewChildren
- https://stackoverflow.com/questions/40165294/access-multiple-viewchildren-using-viewchild

# async/await in ngOnInit
> It is no different than what you had before. ngOnInit will return a Promise and the caller will ignore that promise. This means that *the caller will not wait for everything in your method to finish before it proceeds.* In this specific case it means the view will finish being configured and the view may be launched before **this.data** is set.

## Reference
- https://stackoverflow.com/questions/56092083/async-await-in-angular-ngoninit

# Who's the faster one ? Constructor vs. ngOnInit
> Constructor is part of JS, Angular can't control it directly

```
const instance = new PizzaComponent();

// Angular calls this when it's ready
instance.ngOnInit();
```
>After contructor() is completed, run ngOnInit() 

```
import { Component } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({...})
class PizzaComponent {
  @Input() pizza: Pizza;  

  constructor(
    private route: ActivatedRoute
  ) {
      console.log(this.pizza); // undefined
  }
  
  ngOnInit() {
    console.log(this.pizza); // { name: 'Pepperoni', price: 399 }  
  
    // subscribe when OnInit fires
    this.route.params.subscribe(params => {
      // now we can do something!
    });
  }
}
```
Something you need to take care
- constructor as the place to **wire up your dependencies** and leave it as clean as possible
- **OnChanges** will run before **OnInit**
- ngOnInit phase also includes the first pass of Angular’s Change Detection // **@Input()**

## Reference Docs
- https://ultimatecourses.com/blog/angular-constructor-ngoninit-lifecycle-hook

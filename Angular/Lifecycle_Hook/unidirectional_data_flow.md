# The flow of data are we referring to
## Before ending the JavaScript VM turn, Angular is going to do the following
1. Angular will go through the whole component tree starting at the root component of our application
2. for each component, Angular is going to run the change detection mechanism that is associated with that component and will determine if the component needs to be re-rendered
3. if the component needs to be re-rendered, Angular is going to run its DOM generating function, that produces a new DOM data structure that corresponds to a new version of the component View
4. this process is done from the root of the component tree down until the leaf components of the application
5. during this process for each component several lifecycle methods are called, such as for example ngAfterViewChecked

# how can we avoid such errors?
> We can always defer the data modifications to the next JavaScript VM turn
```
ngAfterViewChecked() {
    setTimeout(() => {
        this.course.description += Math.random();
    });
}
```

# Reference Doc
- https://blog.angular-university.io/angular-2-what-is-unidirectional-data-flow-development-mode/

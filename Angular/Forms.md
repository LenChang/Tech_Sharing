# Introduction
- https://angular.io/guide/forms-overview

# Directive
## NgModel
- [Official Docs](https://angular.io/api/forms/NgModel#description)
### Discussions
#### What's the different between ngModelChange and change events
- https://www.angularjswiki.com/angular/ngmodelchange-change-angular/
> It's the syntactic , they're the same thing
```
<input [(ngModel)]="user.Name"/> is syntactic sugar for
<input [ngModel]="user.name" (ngModelChange)="user.Name = $event"/>
```
> it’s better to follow one single approach. Either use shorthand notation of ngModelChange i.e., [(ngModel)], or define a new ngModelChange function and update the value in that function.
```
<input [ngModel]="user.Name"
       (ngModelChange)="userNamengmodelchange($event)"/>

userNamengmodelchange(value){
    console.log(value);          //Changed Value
    console.log(this.user.Name)  //undefined
    this.user.Name = value; // Update the value here
}
```

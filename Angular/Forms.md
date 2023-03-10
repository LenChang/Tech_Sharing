# Introduction
- https://angular.io/guide/forms-overview

# Directive
## NgModel
- [Official Docs](https://angular.io/api/forms/NgModel#description)
### Discussions
#### What's the different between ngModelChange and change events
- https://www.angularjswiki.com/angular/ngmodelchange-change-angular/
> It's the syntactic sugar
```
<input [(ngModel)]="user.Name"/> is syntactic sugar for
<input [ngModel]="user.name" (ngModelChange)="user.Name = $event"/>
```

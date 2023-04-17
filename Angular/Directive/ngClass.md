# Introduction
> Adds and removes CSS **classes** on an HTML element
- https://angular.io/api/common/NgClass#ngclass

# Example
> ngClass is a kind of property binding, it means that expression can be interpreted as **String/Array/Object**
```
<div [ngClass]="'first second'">
<div [ngClass]="['first', 'second']">
<div [ngClass]="{first: true, second: true, third: true}">
<div [ngClass]="{'first second': true}">
```
## Simple Condition
```
<td [ngClass]="val > 10 ? 'red' : 'green'">{{ val }}</td>
```
## toggle a class based on a condition
> Those are same thing but the final one is ideal
```
<input type="text" [ngClass]="control.isInvalid ? 'error' : ''" />
```
```
<input type="text" [ngClass]="{ error: control.isInvalid }" />
```
```
<input type="text" [class.error]="control.isInvalid" />
```

## Complex Conditions
> Note: you should never use function calls in Angular template expressions [link](https://medium.com/showpad-engineering/why-you-should-never-use-function-calls-in-angular-template-expressions-e1a50f9c0496)
### Before
```
<td [ngClass]="{ low: val >= 0 && val <=5, medium: val > 5 && val <= 10, high: val > 10}">
  {{ val }}
</td>
```
### After
```
<td [ngClass]="className"></td>
```
```
type ClassName = 'low' | 'medium' | 'high';

class MyComponent {
  className: ClassName = 'low';
  
  ngOnChanges(changes: SimpleChanges) {
    if (changes.val) {
      className = mapValToClass(changes.val.currentValue);
    }
  }
  
  private mapValToClass(val: number): ClassName {
    if (val >= 0 && val <= 5) {
      return 'low';
    } else if (val > 5 && val <= 10) {
      return 'medium';
    } else {
      return 'high'
    }
  }
}
```



# Reference
- https://www.freecodecamp.org/news/angular-ngclass-example/

# Overview
> Because Angular cannot predict whether the return value of fullName() has changed, it needs to execute the function every time change detection runs.
- https://medium.com/showpad-engineering/why-you-should-never-use-function-calls-in-angular-template-expressions-e1a50f9c0496

# Solution
## Pure pipes
> A pipe in Angular is pure by default and Angular knows that the pipe’s return value does not change if the pipe’s input does not change.

## Manually calculate the values
> ngOnChanges and if condition

```
@Component({
  template: `
    <p>Welcome {{ fullName }}!</p>
    <div (mousemove)="onMouseMove()">Drop a picture here</div>
`
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class PersonComponent implements OnChanges {
  @Input() person: { firstName: string, lastName: string };
  fullName = '';
  constructor() { }
  ngOnChanges(changes: SimpleChanges) {
    if (changes.person) {
      this.fullName = this.calculateFullName();
    }
  }
  calculateFullName() {  
    return this.person.firstName + ' ' + this.person.lastName;
  }
  onMouseMove() {
    console.log('Mouse was moved');
  }
}
```

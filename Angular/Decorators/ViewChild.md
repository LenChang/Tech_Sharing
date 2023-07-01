# Overview
- Property decorator that configures a view query. The change detector looks for the first element or the directive matching the selector in the view DOM. If the view DOM changes, and a new child matches the selector, the property is updated.
- [Angular Official Docs](https://angular.io/api/core/ViewChild)

# Purpose
- If you wish to gain access to a **DOM element**, **directive** or **component** from a parent component class then you rely on Angular ViewChild.
- it will return the **1st element** that matches. It will match against the template reference selector, directive or component.

# Examples
## Using @ViewChild to inject a reference
### The component
```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent {
  .....

  @ViewChild(ColorSampleComponent)
  primarySampleComponent: ColorSampleComponent;

  .....
}
```

### The DOM element
```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent implements  AfterViewInit {
  .....
  
  @ViewChild('title')
  title: ElementRef;

  ngAfterViewInit() {
    console.log('Values on ngAfterViewInit():');
    console.log("title:", this.title.nativeElement);
  }

  .....
}
```

### Template References
```
@Component({
  selector: 'app-root',
  template: `      
      <ng-template #defaultTabButtons>
          <button class="tab-button" (click)="login()">
            {{loginText}}
          </button>
          <button class="tab-button" (click)="signUp()">
            {{signUpText}}
          </button>
      </ng-template>
`})
export class AppComponent implements OnInit {

    @ViewChild('defaultTabButtons')
    private defaultTabButtonsTpl: TemplateRef<any>;

    ngOnInit() {
        console.log(this.defaultTabButtonsTpl);
    }

}
```

### The DOM element of a component
> The result would be **Component Instance** instead of **Reference**
```
<h2>Choose Brand Colors:</h2>
<color-sample
  [color]="primary"
  #primaryColorSample
  (click)="open()">
</color-sample>
  ... the rest of the AppComponent template ...
```
```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent implements  AfterViewInit {
   ....
   
  @ViewChild('primaryColorSample')
  sample: ColorSampleComponent;

  ngAfterViewInit() {
    console.log('Values on ngAfterViewInit():');
    console.log("sample:", this.sample);
  }

   ....
}
```
### Ref Docs
- https://blog.angular-university.io/angular-viewchild/
- https://www.positronx.io/angular-viewchild-access-child-component/
- https://www.digitalocean.com/community/tutorials/angular-viewchild-access-component
- https://stackoverflow.com/questions/41880420/how-to-get-templateref-of-a-component-in-angular2

# Trouble shooting
## Unidirectional-data-flow-violation error
> The view of Parent & Child initialization are completed before ngAfterViewInit(), you do anything for them isn't workable
```
import ...

@Component({
  ...
  template: `
    ...
    <div class="seconds">{{ seconds() }}</div>
    <app-countdown-timer></app-countdown-timer>
  `,
  ...
})
export class CountdownViewChildParentComponent implements AfterViewInit {

  @ViewChild(CountdownTimerComponent)
  private timerComponent!: CountdownTimerComponent;

  seconds() { return 0; }

  ngAfterViewInit() {
    // Redefine `seconds()` to get from the `CountdownTimerComponent.seconds` ...
    // but wait a tick first to avoid one-time devMode
    setTimeout(() => this.seconds = () => this.timerComponent.seconds, 0);
  }

  start() { this.timerComponent.start(); }
  stop() { this.timerComponent.stop(); }
}
```
### Ref Docs
- https://angular.io/guide/component-interaction#parent-calls-an-viewchild
- https://blog.angular-university.io/angular-2-what-is-unidirectional-data-flow-development-mode/

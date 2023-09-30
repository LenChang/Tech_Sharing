# Overview
## ng-template
> the content of this tag will contain part of a template, that can be then be composed together with other templates in order to form the final component template.
```
<div class="lessons-list" *ngIf="lessons else loading">
  ... 
</div>

<ng-template #loading>
    <div>Loading...</div>
</ng-template>
```

## ng-container
> to avoid creating that extra div when you try to use *ngIf
```
<ng-container *ngIf="lessons">
    <div class="lesson" *ngFor="let lesson of lessons">
        <div class="lesson-detail">
            {{lesson | json}}
        </div>
    </div>
</ng-container>
```

## *ngTemplateOutlet
> This allows us to pass values to variables inside the *ngTemplate*
```
@Component({
  selector: 'app-root',
  template: `      
<ng-template #estimateTemplate let-lessonsCounter="estimate">
    <div> Approximately {{lessonsCounter}} lessons ...</div>
</ng-template>
<!-- either this one -->
<ng-container 
   *ngTemplateOutlet="estimateTemplate;context:ctx">
</ng-container>
`})
<!-- or another one -->
<ng-container 
   <ng-container [ngTemplateOutlet]="estimateTemplate" [ngTemplateOutletContext]="ctx"></ng-container>
</ng-container>
export class AppComponent {

    totalEstimate = 10;
    ctx = {estimate: this.totalEstimate};
  
}
```
```
// The result
Approximately 10 lessons ...
```

# Use Case
## Get template reference directly
> ViewChild and TemplateRef

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
## Get template reference from *ngTemplateOutlet
> @Input, TemplateRef

```
@Component({
  selector: 'app-root',
  template: `      
<ng-template #customTabButtons>
    <div class="custom-class">
        <button class="tab-button" (click)="login()">
          {{loginText}}
        </button>
        <button class="tab-button" (click)="signUp()">
          {{signUpText}}
        </button>
    </div>
</ng-template>
<tab-container [headerTemplate]="customTabButtons"></tab-container>      
`})
export class AppComponent implements OnInit {
...
}
```
```
Component({
    selector: 'tab-container',
    template: `
    
<ng-template #defaultTabButtons>
    
    <div class="default-tab-buttons">
        ...
    </div>
    
</ng-template>
<ng-container 
  *ngTemplateOutlet="headerTemplate ? headerTemplate: defaultTabButtons">
    
</ng-container>
... rest of tab container component ...
`})
export class TabContainerComponent {
    @Input()
    headerTemplate: TemplateRef<any>;
}
```

# Reference
- https://blog.angular-university.io/angular-ng-template-ng-container-ngtemplateoutlet/
- https://medium.com/startit-up/advanced-components-in-angular-41b43556178d

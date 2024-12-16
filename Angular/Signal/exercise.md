> https://angular.dev/playground
# Exercise
```typescript
import {Component,OnInit} from '@angular/core';
import {bootstrapApplication} from '@angular/platform-browser';

@Component({
  selector: 'app-root',
  template: `What's the number of c ?`,
})
export class PlaygroundComponent implements OnInit {
  a = 10;
  b = 20;
  c = this.a + this.b;
  ngOnInit(){
    this.a = 50;
  }
}

bootstrapApplication(PlaygroundComponent);
```

#Completed Exercise
```typescript
import {Component,OnInit, signal, computed} from '@angular/core';
import {bootstrapApplication} from '@angular/platform-browser';

@Component({
  selector: 'app-root',
  template: `What's the number of c ?`,
})
export class PlaygroundComponent implements OnInit {
  a = signal(10);
  b = signal(20);
  c = computed(()=>this.a() + this.b());
  ngOnInit(){
    this.a = signal(50);
  }
}

bootstrapApplication(PlaygroundComponent);
```

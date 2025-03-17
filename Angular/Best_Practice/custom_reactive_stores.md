# Implementation Steps
1. Create a Store Service
2. Define State Methods
3. Inject and Use the Store

# Example
> You can always use rxjs only, signals is the **optional** choice.
```typescript
import { Injectable } from '@angular/core';
import { BehaviorSubject, Observable } from 'rxjs';
import { signal } from '@angular/core';

@Injectable({ providedIn: 'root' })
export class StoreService<T> {
  private state$ = new BehaviorSubject<T>(null!);
  private signalState = signal<T>(null!);

  constructor(private initialState: T) {
    this.setState(initialState);
  }

  setState(newState: T): void {
    this.state$.next(newState);
    this.signalState.set(newState);
  }

  getState(): Observable<T> {
    return this.state$.asObservable();
  }

  select<K extends keyof T>(key: K): Observable<T[K]> {
    return this.state$.pipe(map(state => state[key]));
  }

  // Usage of Signals
  getSignalState(): T {
    return this.signalState();
  }
}

// Usage in a component
@Component({
  selector: 'app-root',
  template: `<div>{{ state | async | json }}</div>`,
})
export class AppComponent {
  state: Observable<any>;

  constructor(private store: StoreService<any>) {
    this.state = this.store.getState();
  }

  updateState() {
    this.store.setState({ key: 'newValue' });
  }
}
```
# Reference
- https://ashishsharma229.medium.com/advanced-angular-techniques-f003bc232a9c

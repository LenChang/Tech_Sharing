# Implementation Steps
1. Create an Event Bus Service
2. Emit Events
3. Subscribe to Events
4. Filter Events

# Example
```typescript
import { Injectable } from '@angular/core';
import { Subject, Observable } from 'rxjs';

@Injectable({ providedIn: 'root' })
export class EventBusService {
  private eventBus$ = new Subject<{ event: string; payload: any }>();

  emit(event: string, payload: any) {
    this.eventBus$.next({ event, payload });
  }

  on(event: string): Observable<any> {
    return this.eventBus$.asObservable().pipe(
      filter(e => e.event === event),
      map(e => e.payload)
    );
  }
}

// Emitting an event
@Component({
  selector: 'app-emitter',
  template: `<button (click)="sendMessage()">Send Message</button>`,
})
export class EmitterComponent {
  constructor(private eventBus: EventBusService) {}

  sendMessage() {
    this.eventBus.emit('customEvent', { message: 'Hello from Emitter!' });
  }
}

// Listening to an event
@Component({
  selector: 'app-listener',
  template: `<p>{{ message }}</p>`,
})
export class ListenerComponent {
  message: string;

  constructor(private eventBus: EventBusService) {
    this.eventBus.on('customEvent').subscribe(data => {
      this.message = data.message;
    });
  }
}
```
# Reference
- https://ashishsharma229.medium.com/advanced-angular-techniques-f003bc232a9c

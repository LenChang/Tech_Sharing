# share
> Returns a new Observable that multicasts (shares) the original Observable
- https://rxjs.dev/api/operators/share
#### WARNING: share() isn't at the end
> In this case, we subscribe to tap twice - and those two tap operators subscribe to share twice.
```javascript
import { interval } from 'rxjs';
import { share, tap } from 'rxjs/operators';

const interval$ = interval(1000).pipe(
  share(),
  tap(() => console.log("Interval Triggered")),
)

interval$.subscribe();
interval$.subscribe();
// we will get two console messages per second
```
#### Example
```javascript
import { interval } from 'rxjs';
import { take, share,finalize } from 'rxjs/operators';

const start = Date.now()

const source$ = interval(1000).pipe(
  take(5),
  finalize(() => console.log(`Source complete. ${Date.now() - start} ms`)), // Execute when the observable completes
  share({ resetOnRefCountZero: true }),
);

const sub1 = source$.subscribe(val => console.log('Sub1:', val));
let sub2

setTimeout(() => {
  sub1.unsubscribe();
  console.log(`Unsubscribe sub1 ${Date.now() - start} m`)
  sub2 = source$.subscribe(val => console.log('Sub2:', val));
}, 4000);

setTimeout(() => {
  sub2.unsubscribe();
  console.log(`Unsubscribe sub2 ${Date.now() - start} ms`)
}, 10000);
```

# shareReplay
> Share source and replay specified number of emissions on subscription
#### WARNING: put shareReplay() before the take()
> According to the explanation above, the shareReplay() won't unsubscribe the source even though the take() has triggered the completion.
```javascript
import { interval } from 'rxjs';
import { shareReplay,take,finalize} from 'rxjs/operators';

const shared$ = interval(1000).pipe(
  finalize(() => console.log(`Source complete`)),
  shareReplay(1),
  take(2),
)
 
shared$.subscribe(x => console.log('sub A: ', x));
shared$.subscribe(y => console.log('sub B: ', y));
// shared$ wouldn't complete <= memory leak
```

## Term Definition
### bufferSize
> BufferSize means the number of items cached and replayed
```javascript
const shared$ = interval(2000).pipe(
  take(6),
  shareReplay(3) // the number "3" is buffer size
);
```
### refCount
> the default value is false, it means that the shareReplay will not unsubscribe the source even the observables count drops to is zero  
```javascript
const shared$ = log('shared', obs$.pipe(
  take(2),
  shareReplay({ bufferSize: 1, refCount: true }) // The source (obs$.pipe(...)) will be unsubscribed from once observables count drops to zero
));
```

# Example
## How does shareReplay() work ?
```javascript
const source$ = interval(1000).pipe(
  shareReplay(2)
);

source$.subscribe(data => {
  console.log(`shareReplay Demo - The first subscribing: ${data}`);
});

setTimeout(() => {
  source$.subscribe(data => {
    console.log(`shareReplay Demo - The second subscribing: ${data}`);
  });
}, 5000);
// shareReplay Demo - The first subscribing: 0
// shareReplay Demo - The first subscribing: 1
// shareReplay Demo - The first subscribing: 2
// shareReplay Demo - The first subscribing: 3
// shareReplay Demo - The first subscribing: 4
// (Replay the lastest 2 times result and continue..)
// shareReplay Demo - The second subscribing: 3
// shareReplay Demo - The second subscribing: 4
// shareReplay Demo - The first subscribing: 5
// shareReplay Demo - The second subscribing: 5
// shareReplay Demo - The first subscribing: 6
// shareReplay Demo - The second subscribing: 6
```
## Https request on Angular Service
```javascript
import { shareReplay } from 'rxjs/operators';
import { Observable } from 'rxjs';
import { HttpClient } from '@angular/common/http';

@Injectable({providedIn: 'root'})
export class CustomerService {
    lang$ = new BehaviorSubject("myDefaultLang");

    data$ = this.lang.pipe(
      switchMap((lang)=> this.http.get(APP_ENDPOINT + '?lang=' + lang)),
      shareReplay(1),
    );

    constructor(private readonly http: HttpClient) {}

    loadData(lang:string) {
      this.lang$.next(lang)
    }
    
    getData() {
      return this.data$;
    }
}
```
# Reference
- https://rxjs.dev/api/operators/shareReplay
- https://blog.angular-university.io/rxjs-error-handling/
- https://stackoverflow.com/questions/63232747/should-i-use-sharereplay-as-the-last-operator

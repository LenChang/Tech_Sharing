# Overview
> Share source and replay specified number of emissions on subscription
- share(): publish() + refCount()
  - publish(): multicast(() => new Subject())
- **shareReplay()**: multicast(() => new ReplaySubject()) + refCount()
## Term Definition
### bufferSize
> BufferSize means the number of items cached and replayed
```
const shared$ = interval(2000).pipe(
  take(6),
  shareReplay(3) // the number "3" is buffer size
);
```
```
const shared$ = log('shared', obs$.pipe(
  shareReplay({ bufferSize: 1, refCount: true }), // the number "1" is buffer size
  take(2)
));
```

## Example
### How does shareReplay() work ?
```
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
### Https request on Angular Service
```
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
- https://fullstackladder.dev/blog/2020/10/15/mastering-rxjs-30-multicast-publish-refcount-share-sharereplay/
- https://stackoverflow.com/questions/68101744/updating-cached-http-request-in-angular-with-rxjs-and-sharereplay
- https://www.bitovi.com/blog/always-know-when-to-use-share-vs.-sharereplay

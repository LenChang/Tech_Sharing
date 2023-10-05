# Overview
> Share source and replay specified number of emissions on subscription
- share(): publish() + refCount()
  - publish(): multicast(() => new Subject())
- **shareReplay()**: multicast(() => new ReplaySubject()) + refCount()  

## Example Cdoe
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
## Example: Https on Angular Service
```
import { shareReplay } from 'rxjs/operators';
import { Observable } from 'rxjs';
import { HttpClient } from '@angular/common/http';

@Injectable({providedIn: 'root'})
export class CustomerService {

    private readonly _getCustomers: Observable<ICustomer[]>;

    constructor(private readonly http: HttpClient) {
        this._getCustomers = this.http.get<ICustomer[]>('/api/customers/').pipe(shareReplay());
    }
    
    getCustomers() : Observable<ICustomer[]> {
        return this._getCustomers;
    }
}

export interface ICustomer {
  /* ICustomer interface fields defined here */
}
```

# Reference
- https://rxjs.dev/api/operators/shareReplay
- https://fullstackladder.dev/blog/2020/10/15/mastering-rxjs-30-multicast-publish-refcount-share-sharereplay/
- https://stackoverflow.com/questions/36271899/what-is-the-correct-way-to-share-the-result-of-an-angular-http-network-call-in-r

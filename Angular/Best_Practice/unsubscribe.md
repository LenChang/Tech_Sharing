# Ways
## unsubscribe()
```
@Component({...})
export class AppComponent implements OnInit, OnDestroy {
    
    subscription: Subscription
    ngOnInit () {
        var observable1$ = Rx.Observable.interval(1000);
        var observable2$ = Rx.Observable.interval(400);
        var subscription1$ = observable.subscribe(x => console.log("From interval 1000" x));
        var subscription2$ = observable.subscribe(x => console.log("From interval 400" x));
        this.subscription.add(subscription1$)
        this.subscription.add(subscription2$)
    }
    ngOnDestroy() {
        this.subscription.unsubscribe()
    }
}
```
## Use Async | Pipe
> async pipe will unsubscribe the observable$ when the AppComponent is destroyed
```
@Component({
    ...,
    template: `
        <div>
         Interval: {{observable$ | async}}
        </div>
    `
})
export class AppComponent implements OnInit {
    observable$
    ngOnInit () {
        this.observable$ = Rx.Observable.interval(1000);
    }
}
```
## Use RxJS take* operators
### take(n)
> 1 is popularly used with the take operator so subscriptions happen once and exit.
```
@Component({
    ...
})
export class AppComponent implements OnInit {
    subscription$
    ngOnInit () {
        var observable$ = Rx.Observable.interval(1000);
        this.subscription$ = observable$.pipe(take(1)).
        subscribe(x => console.log(x))
     }
}
```
### takeUntil(notifier)
```
@Component({...})
export class AppComponent implements OnInit, OnDestroy {
    notifier = new Subject()
    ngOnInit () {
        var observable$ = Rx.Observable.interval(1000);
        observable$.pipe(takeUntil(this.notifier))
        .subscribe(x => console.log(x));
    }
    ngOnDestroy() {
        this.notifier.next()
        this.notifier.complete()
    }
}
```
### takeWhile(predicate)
```
@Component({...})
export class AppComponent implements OnInit {
    ngOnInit () {
        var observable$ = Rx.Observable.interval(1000);
        observable$.pipe(takeWhile(value => value < 10))
        .subscribe(x => console.log(x));
    }
}
```
### Use RxJS first operator
> This operator is like the concatenation of take(1) and takeWhile
#### called with no value // take(1)
```
@Component({...})
export class AppComponent implements OnInit {
    observable$
    ngOnInit () {
        this.observable = Rx.Observable.interval(1000);
        this.observable$.pipe(first())
        .subscribe(x => console.log(x));
    }
}
```
#### called with value // takeWhile(...)
```
@Component({...})
export class AppComponent implements OnInit {
    observable$
    ngOnInit () {
        this.observable$ = Rx.Observable.interval(1000);
        this.observable$.pipe(first(val => val === 10))
        .subscribe(x => console.log(x));
    }
}
```
# Reference
- https://blog.bitsrc.io/6-ways-to-unsubscribe-from-observables-in-angular-ab912819a78f

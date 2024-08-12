# Overview
- Returns an Observable that mirrors the source Observable when the exception of an error is happened.
# Example
```
const request$ = http$.pipe(
        tap(() => console.log("HTTP request executed")),
        map(res => Object.values(res["payload"]) ),
        shareReplay(), // It's the best practice when there are many observables
        retry(errors => {count:5, delay: 2000} )
        catchError(() => of(returnThisIfRetriesAreFailed))
)

request%.subscribe(console.log);
request%.subscribe(console.log);
```

# Reference
- https://rxjs.dev/api/operators/retry
- https://stackoverflow.com/questions/72592177/how-can-i-retry-with-a-delay-in-rxjs-without-using-the-deprecated-retrywhen
- https://blog.angular-university.io/rxjs-error-handling/

# Overview
> Returns an Observable that mirrors the source Observable when the exception of an error is happened.
## Sample
```
of('trigger')
  .pipe(
    switchMap(() => fetchData()),
    retry({count: 5, delay: 2000}),
    catchError(() => of(returnThisIfRetriesAreFailed))
  )
  .subscribe(console.log);
```

# Reference
- https://rxjs.dev/api/operators/retry
- https://stackoverflow.com/questions/72592177/how-can-i-retry-with-a-delay-in-rxjs-without-using-the-deprecated-retrywhen

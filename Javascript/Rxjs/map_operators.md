# Related map operations
> https://rxjs.dev/api/operators

## Problem
```
// the pipe of refresing page
const refresh$ = fromEvent(document.querySelector('#refresh'), 'click');

// the pipe of fetching data from api
const request$ = ajax('https://api.github.com/repos/reactivex/rxjs/issues')
  .pipe(map(response => response.response));

refresh$.subscribe(() => {
  request$.subscribe(result => {
        // refresh page
    ...
  });
})
```
# switchMap, concatMap, mergeMap and exhaustMap
- Projects each source value to an Observable which is merged in the output Observable, and then ...
## switchMap
- Emitting values **only from the most recently** projected Observable.
```
interval(3000).pipe(
  switchMap(() => timer(0, 1000))
).subscribe(data => {
  console.log(data);
});
// 0
// 1
// 2
// 0 (new event happens, then unsubscribes the last Observable)
// 1
// 2
// ...
```

## concatMap
- In a serialized fashion **waiting for each one** to complete before merging the next.
```
interval(3000).pipe(
  concatMap(() => timer(0, 1000))
).subscribe(data => {
  console.log(data);
});
// 0
// 1
// 2
// 3
// 4
// 5
// 6
// (forever...）
```

## mergeMap
- do **nothing**
```
const source1$ = timer(0, 3000);
const getSource2 = (input) => timer(0, 1500)
  .pipe(map(data => `pipe ${input}: ${data}`));

source1$.pipe(
  mergeMap(data => getSource2(data))
).subscribe(result => {
  console.log(result);
});
// pipe 0: 0
// pipe 0: 1
// pipe 1: 0 (new event，new pipe)
// pipe 0: 2
// pipe 1: 1
// pipe 0: 3
// pipe 2: 0 (new event，new pipe)
// pipe 1: 2
// pipe 0: 4
// pipe 1: 3
// pipe 2: 1
```

## exhaustMap
- Only if **the previous projected Observable has completed**
- Both of switchMap and exhaustMap are unsubscribing observable. However the key different is that the switchMap is giving up the previous one, then the exhaustMap is giving up coming ones

# Reference
- https://fullstackladder.dev/blog/2020/10/04/mastering-rxjs-19-switchmap-concatmap-mergemap-exhaustmap/

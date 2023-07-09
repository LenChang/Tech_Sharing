# Overview
> Delay the function execution time until it's actually triggered
## Sample
### Delay the result of new Date()
```
const s1 = of(new Date()); //will capture current date time
const s2 = defer(() => of(new Date())); //will capture date time at the moment of subscription
```
### Lazy promising
> Promise is eager
```
/ This already executing regardless the numbers of handlers
const promise = new Promise(resolve => {
  resolve();
});

// Deferring the creation of the promise until someone subscribes
const promiseDefered = defer(() => {
  return new Promise(resolve => {
    resolve();
  });
});
promiseDefered.subscribe(console.log);
```

#### from vs defer ?
> defer() is delaying the function execution time; from() just make promise to ovservable only

### Get different random number
> Math.random() is eagerly executed
```
// you're going to get the same result
const randNum = of(Math.random());
randNum.subscribe(console.log);
randNum.subscribe(console.log);

const randNum = defer(() => of(Math.random()));
randNum2.subscribe(console.log);
randNum2.subscribe(console.log);

// The same concept as using a function
const randNum = () => of(Math.random());
randNum2().subscribe(console.log);
randNum2().subscribe(console.log);
```


# Reference Docs
- https://netbasal.com/getting-to-know-the-defer-observable-in-rxjs-a16f092d8c09
- https://stackoverflow.com/questions/38764578/rxjs-understanding-defer

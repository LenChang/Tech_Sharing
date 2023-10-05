# Accessing Previous values
> you can pass the original value down the chain or combine the original stream in again

## Problem
```
getUser(email).pipe(
  mergeMap(user => getProducts(user.interests)),
  map(products => {
    // The line below will fail, the user is undefined
    if (user.isPremiumMember) {
      return discountPrices(products);
    } else {
      return products;
    }
  })
);
``` 
### Solution 1 - Pass the values down the chain with a nested pipe and map
> It doesn't follow the FP pattern but still worked
```
getUser(email).pipe(
  mergeMap(user => {
    return getProducts(user.interests).pipe(
      map(products => {
        return {user: user, products: products};
      })
    );
  }),
  map(({user, products}) => {
    // Here we can access both user and products
  })
);
```
### Solution 2 - Nest a combineLatest or forkJoin inside the chain
> It satisfies the FP pattern but doesn't fit rxjs principles
```
getUser(email).pipe(
  mergeMap(user => {
    return combineLatest(
      of(user),
      getProducts(user.interests)
    );
  }),
  map(([user, products]) => {
    // Here we can access both user and products
  })
);
```
### Solution 3 - Divide the chain into several parts, then use combineLatest or forkJoin
> The better way to fit both FP and Rxjs concepts, but will exist a little bit performance issue
```
const user$ = getUser(email);
const products$ = user$.pipe(
  mergeMap(user => getProducts(user.interests))
);
combineLatest(user$, products$).pipe(
  map(([user, products]) => {
    // Here we can access both user and products
  })
); 
```
### Solution 4 - Get the latest original stream with getLatestFrom
> The best way to do it
```
const user$ = getUser(email);
const products$ = user$.pipe(
  mergeMap(user => getProducts(user.interests)),
  withLatestFrom(user$),
  map(([products, user]) => {
    // Here we can access both user and products
  })
);
```


# Reference
- https://medium.com/@snorredanielsen/rxjs-accessing-a-previous-value-further-down-the-pipe-chain-b881026701c1

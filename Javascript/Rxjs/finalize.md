# Definition
> The finalize of rxjs is as similar as finally of try-catch-finally
- An RxJS operator for executing logic when the Observable terminates
# Sample Code
```
this.isLoading = true;
this.someService.fetchDataFromApi()
  .pipe(
    finalize(() => {
      this.isLoading = false;
    })
  )
  .subscribe(
    result => {
      // success
    },
    err => {
      // some error happened
    }
  )
```

# Reference
- https://juristr.com/blog/2019/04/rxjs-finalize-operator/

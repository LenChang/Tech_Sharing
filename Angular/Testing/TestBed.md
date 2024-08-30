# Example
```
...
 TestBed.configureTestingModule({
    providers: [
      MasterService,
      { provide: ValueServiceA, useValue: spyA },
      { provide: ValueServiceB, useValue: spyB },
      {...}
    ]
  });
...
```

# Reference
- [Official Doc](https://v17.angular.io/guide/testing-services#angular-testbed)
- https://stackoverflow.com/questions/42612721/multiple-providers-angular-2-test-bed

# Overview
> 当你准备用来合并的流是那种只会发射一次数据就关闭的流时（比如http请求），就结果而言这三个操作符没有任何区别

## forkJoin
> Wait for Observables to **complete** and then combine last values they emitted; complete immediately if an empty array is passed.
- 会在每个被合并的流都发出**结束信号**时发射一次也是唯一一次数据

## zip
> An Observable of array values of the values emitted at the **same index** from each individual ObservableInput.
- 当每个传入zip的流都发射完毕第一次数据时，zip将这些数据合并为数组并发射出去；当这些流都发射完第二次数据时，zip再次将它们合并为数组并发射。以此类推直到其中某个流发出结束信号，整个被合并后的流结束，不再发射数据

## combineLatest
> Whenever any input Observable emits a value, it computes a formula using the **latest values from all the inputs**, then emits the output of that formula.
- combineLatest与zip很相似，combineLatest一开始也会等待每个子流都发射完一次数据，但是在合并时，如果子流1在等待其他流发射数据期间又发射了新数据，则使用子流最新发射的数据进行合并，之后每当有某个流发射新数据，不再等待其他流同步发射数据，而是使用其他流之前的最近一次数据进行合并

# Reference
- https://segmentfault.com/a/1190000012369871
- [doc: forkJoin](https://rxjs.dev/api/index/function/forkJoin)
- [doc: zip](https://rxjs.dev/api/index/function/zip)
- [doc: combineLatest](https://rxjs.dev/api/index/function/combineLatest)

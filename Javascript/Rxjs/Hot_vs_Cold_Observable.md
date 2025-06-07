# Overview
- A good analogy from real life is YouTube videos. Every viewer of that YT video has their own execution process. This means that they can watch the video whenever they decide. This process is quite similar to how cold observables work. On the other hand, a live stream is something different. It behaves like a hot observable. It is shared between multiple viewers who watch it at the same time.
## Definition
| Hot | Cold |
| -------- | ------- |
| e.g. live radio | e.g. video on demand |
| The data source is created *outside* the observable |The data source is created *inside* the observable|
| Multicast | Unicast |
| Emit values *always*, even if there are no subscribers | Emit values only *when we subscribe to them* |

# Reference
- https://www.decodedfrontend.io/hot-vs-cold-observable-in-rxjs/

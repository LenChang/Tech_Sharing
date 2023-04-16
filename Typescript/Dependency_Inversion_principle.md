# Definition
- Decouple modules from each other and make it **Reusability** and **Testability**
- Depends on abstraction conversion instead of implementation
## dependency Injection
- Inject instance into class by **constructor**
- Deliever and pass some modules of an application to the module which requires them of an application (Angular)

# Example
## dependency inversion
### Function
```
function cc(a:string, b:number, c:()=>number){
...
}
const tmp = cc('aa',11,Math.random)
```
### Class
#### Code without dependency inversion
```
class FileSystem {
  writeToFile(data) {
    // Implementation
  }
}

class ExternalDB {
  writeToDatabase(data) {
    // Implementation
  }
}

class PersistanceManager {
  saveData(db, data) {
    if (db instanceof FileSystem) {
      db.writeToFile(data)
    }

    if (db instanceof ExternalDB) {
      db.writeToDatabase(data)
    }
  }
}
```
#### Code with dependency inversion
```
class FileSystem {
  save(data) {
    // Implementation
  }
}

class ExternalDB {
  save(data) {
    // Implementation
  }
}

class PersistanceManager {
  saveData(db, data) {
    db.save(data)
  }
}
```


## dependency injection
```
interface Logger {
  log(message: string): void;
}

class Counter {
  constructor(
    private logger: Logger,
  ) {}

  public state: number = 0;

  public increase(): void {
    this.state += 1;
    this.logger.log(`State increased. Current state is ${this.state}.`);
  }

  public decrease(): void {
    this.state -= 1;
    this.logger.log(`State decreased. Current state is ${this.state}.`);
  }
}

const couter = new Counter(console);
```


## automatic dependency injection  (Angular)
```
// dependency provider
@Injectable()
class HeroService {}
```
```
// dependency consumer
@Component({
  selector: 'hero-list',
  template: '...',
  providers: [HeroService]
})
class HeroListComponent {}
```
### DI Containers
- https://brandi.js.org/

# Reference Docs
- https://dev.to/vovaspace/dependency-injection-in-typescript-4mbf
- https://angular.io/guide/dependency-injection-overview
- https://dev.to/denisveleaev/5-solid-principles-with-javascript-how-to-make-your-code-solid-1kl5

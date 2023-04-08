# Definition
- Decouple modules from each other and make it **Reusability** and **Testability**
- Deliever and pass some modules of an application to the module which requires them of an application (Angular)
- Depends on abstraction conversion instead of implementation
- Dependency Injection for Class as same as Dependency Inversion of function

# Example
## dependency inversion
```
// it's dependency inversion
function cc(a:string, b:number, c:()=>number){
...
}
const tmp = cc('aa',11,Math.random)
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

# Initializing member variables inline vs in the constructor
## Question: Which is the better way ?
```
@Component({
  selector: 'app-elem',
  templateUrl: './app-elem.component.html',
  styleUrls: ['./app-elem.component.scss'],
})
export class AppElemComponent {

  public isHidden = true;    // <-- initialization inline
  public isVisible: boolean;

  constructor() {
    this.isVisible = true;  // <-- vs initialization in the constructor
  }
}
```
### Answer
- It's a personal style preference
- **Initializing property** inline is more concise
- TypeScript compiler will bring property which is initialized inline into constructor
  - https://www.typescriptlang.org/play/

## Reference
- https://stackoverflow.com/questions/51494083/initializing-variables-inline-during-declaration-vs-in-the-constructor-in-angula

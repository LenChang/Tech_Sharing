# Overview
> Renderer2 is a service used to perform DOM operations in a platform-independent manner, instead of directly manipulating the DOM.
## Example
```
@Component({
  selector: 'app-example',
  template: `
    <button (click)="changeColor()">Change Color</button>
  `,
})
export class ExampleComponent {
  constructor(private elementRef: ElementRef, private renderer: Renderer2) {}

  changeColor() {
    const button = this.elementRef.nativeElement.querySelector('button');
    this.renderer.setStyle(button, 'background-color', 'blue');
    this.renderer.setStyle(button, 'color', 'white');
  }
}
```

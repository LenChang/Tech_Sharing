# Purpose
- To **scale**, **rotate** and ..etc for your elements

## Example (Canvas)
```
// Angular
<canvas #tmpCanvas id="tmpCanvas"></canvas>
```
```
...
// Angular
@ViewChild('tmpCanvas', { static: false }) tmpCanvas: ElementRef<HTMLCanvasElement>;
// ...
this.tmpCanvas.nativeElement.style.transform = 'scale(1.5)';
this.tmpCanvas.nativeElement.style.transformOrigin = 'left top';
// ...
```
# Reference
- https://www.w3schools.com/cssref/css3_pr_transform.php
- https://www.w3schools.com/cssref/css3_pr_transform-origin.php

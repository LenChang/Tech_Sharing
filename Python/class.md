# The comparison between PY and JS
> PY: self vs JS: this
- The **self** should be injected into each method manually; instead **this** is injected into each method automatically

| PY | JS 
|---|---
| [doc](https://docs.python.org/3/tutorial/classes.html) | [doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
| ```def __init__(self, height):```<br>```   self.height = height``` |  ```constructor(height) {``` <br> ```this.height = height;``` <br> ```}```

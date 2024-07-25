# The comparison between PY and JS
> PY: self vs JS: this
- The **self** should be injected into each method manually; instead **this** is injected into each method automatically

| PY | JS | TS
|---|---|---
| [doc](https://docs.python.org/3/tutorial/classes.html) | [doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) | [doc](https://www.typescriptlang.org/docs/handbook/2/classes.html)
| ```def __init__(self, height):```<br>```   self.height = height``` |  ```constructor(height) {``` <br> ```this.height = height;``` <br> ```}``` |
| ```def __init__(self, type):```<br>```   self.__type = type``` | ```#type;```<br>```constructor(type) {``` <br> ```this.#type = type;``` <br> ```}``` | ```private type;```<br>```constructor(type) {``` <br> ```this.type = type;``` <br> ```}``` 
| ```class Student(Person):``` <br> ```  def __init__(self, fname, lname):``` <br> ```    super().__init__(fname, lname)``` | ```class Student extends Person {``` <br> ```  constructor(fname, lname) {``` <br> ```    super(fname, lname);``` <br> ```}}```

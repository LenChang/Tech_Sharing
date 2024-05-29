# Private vs Protected
> Protected methods/members are accessible from inside the class and **extending class** as well.
```
class A {
    private x: number;
    protected y: number;

    constructor(x: number, y: number) {
        this.x = x;
        this.y = y;
    }

    getX() {return this.x;}

    getY() {return this.y;}
}

// [error] Property 'x' is private and only accessible within class A
class B extends A {
    multiply() {return this.x * this.y;}
}
```
## Reference
- https://stackoverflow.com/questions/36843357/typescript-difference-between-private-and-protected-variables

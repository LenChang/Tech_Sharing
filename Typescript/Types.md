# Differences Between Type Aliases and Interfaces
- [docs](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces)
> Type aliases and interfaces are very similar, and in many cases you can choose between them freely. Almost all features of an interface are available in type, the key distinction is that a **type cannot be re-opened to add new properties** vs an interface which is always extendable. 

- Type aliases may not participate in declaration merging, but interfaces can.
- Interfaces may only be used to declare the shapes of objects, not rename primitives. // But type alias can

## Reference
- https://levelup.gitconnected.com/typescript-what-is-the-difference-between-type-and-interface-9085b88ee531

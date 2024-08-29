# Basic Usage
## Set Property
> https://stackoverflow.com/questions/64560390/jasmine-createspyobj-with-properties
```
it("creates a spy object with properties", function() {
  let obj = createSpyObj("myObject", {}, { x: 3, y: 4 });
  expect(obj.x).toEqual(3);
});
```

# Reference
- https://jasmine.github.io/tutorials/spying_on_properties

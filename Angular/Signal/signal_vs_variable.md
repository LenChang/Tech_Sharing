# Overview: Signal vs. a Standard Class Variable
> how the framework tracks changes and updates the user interface
# Examples
## Basic Value Updates
### Derived State (Computed Values)
#### Standard Variable (Manual)
```typescript
count = 0;
doubleCount = 0;

increment() {
  this.count++;
  this.doubleCount = this.count * 2; // Must remember to update this too!
}
```
#### Angular Signal (Automatic)
```typescript
count = signal(0);
// Automatically recalculates only when count changes
doubleCount = computed(() => this.count() * 2); 

increment() {
  this.count.set(this.count() + 1);
  // doubleCount updates itself automatically
}
```
### Side Effects
#### Standard Variable
```typescript
private _count = 0;
set count(val: number) {
  this._count = val;
  console.log('Count changed to:', val); // Manual trigger
}
```
#### Angular Signal
```typescript
count = signal(0);

constructor() {
  effect(() => {
    // Automatically runs whenever this.count() changes
    console.log('Count changed to:', this.count());
  });
}
```

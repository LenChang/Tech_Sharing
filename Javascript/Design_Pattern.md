# Singleton
> Global Access & Data Sharing
```javascript
const Singleton = (function () {
  let instance;
 
  function createInstance() {
    const object = new Object("I am the instance");
    return object;
  }
 
  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    }
  };
})();
 
function run() {
  const instance1 = Singleton.getInstance();
  const instance2 = Singleton.getInstance();
 
  console.log("Same instance? " + (instance1 === instance2));
}
 
run();
```

# Dependency Injection
> Decoupleing your architecture
```javascript
class Logger {
  log(message) {
    console.log(message);
  }
}
 
class UserService {
  constructor(logger) {
    this.logger = logger;
  }
 
  createUser(user) {
    // Logic to create a user
    this.logger.log(`User ${user.name} created.`);
  }
}
 
// Injecting the dependency
const logger = new Logger();
const userService = new UserService(logger);
 
userService.createUser({ name: 'John Doe' });
```

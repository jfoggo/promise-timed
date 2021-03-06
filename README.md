# promise-timed
This module offers a `TimedPromise` class which extends the promise functionality with a timeout.

## Installation
This is a `NodeJS` module and it is available via `npm` (Node-Package-Manager):

`npm install promise-timed`

## Features
- The `TimedPromise` class allows to set a maximum execution time (in ms) via `timeout` parameter.
- If no timeout argument provided (or timeout <= 0), the class will behave just as a usual promise and no timer will be used.

## Documentation
```
let promise = new TimedPromise(executor,timeout=0)
```
INPUT:
- exeutor: (required) promise function with resolve+reject arguments
- timeout: (optional) integer in milliseconds, default=0

OUTPUT:
- promise (rejects an Error in case of timeout)

## Examples
```
// include module
const TimedPromise = require("promise-timed");

// Example 1: Never ending promise rejects after timeout
let executor = (resolve,reject) => { /* do nothing ... */ };
let timeout = 1000; // 1000ms = 1s
new TimedPromise(executor,timeout)
   .then(result => console.log("[*] promise resolved: "+result))
   .catch(error => console.log("[*] promise rejected: "+error));

// Example 2: No timeout argument, works like a usual promise
new TimedPromise((resolve,reject)=>{
   // do some stuff
   resolve();
})
```

## Dependencies
This module has no dependencies.

## License
MIT License

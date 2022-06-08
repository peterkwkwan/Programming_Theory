## Is JS single-threaded?

Javascript is a synchronous, blocking, single threaded language.

This means only 1 operation can be in progress at any given time. Only 1 function can be run at any given time, which blocks other functions from running until the running function has returned.

## How does Async JS work if JS is single-threaded?

Asynchronous means that multiple operations can be happening at the same time.

There are 3 common ways to achieve asynchronous code in JS.

1. callbacks
2. promises
3. async / await

## How does the JS runtime and event loop work?

![Runtime](./assets/JS-runtime.png?raw=true)

## What are closures?

```
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```

When a function references data outside its own scope (i.e. lexical environment), it needs to 'close' that data in a container and store it in the heap memory.

Since the data / variable is stored in heap memory, it can be referenced even after the outer function has been returned.

## Heap Memory vs Call Stack?

Heap Memory

- long lived
- gets cleaned up by garbage collector

Call Stack

- short lived

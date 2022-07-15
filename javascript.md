## Is JS single-threaded?

Javascript is a synchronous, blocking, single threaded language.

This means only 1 operation can be in progress at any given time. Only 1 function can be run at any given time, which blocks other functions from running until the running function has returned.

## What is Execution Context (EC)?

An environment where Javascript code is evaluated and executed. Any code run in JS is inside an EC.

2 main types of Execution Context:

1. Global EC

- default or base EC
- performs 2 tasks: creates a global object (window object) and sets the value of `this` equal to global object

2. Functional EC

- everytime a function is invoked, a brand new EC is created for that function

Execution context has two main parts: Variable Environment & Thread of Execution

![Execution Context](./assets/execution-context.png?raw=true)

## How does the JS runtime and event loop work?

#### The Call Stack

- the single-thread of execution in JS
- each stack frame has its own execution context in the call stack
- the global execution context is the first item that gets added to the call stack
- it is short lived

#### Heap Memory

- long lived
- where all the objects and variable declarations live
- gets cleaned up by garbage collector

#### Event Loop & Message Queue

- Event loop's job is to monitor the call stack and msg queue
- when the call stack becomes empty, event loop will check the msg queue to see if there are any msgs waiting to be executed
- Each msg is associated with a callback fn() or an event

#### Web APIs

- DOMevents, setTimeouts are some of the browser built-in APIs
- callback functions within setTimeouts will get added to the msg/callback queue
- callbacks and event handlers within the queue will eventually get added to the call stack once it is empty

![Runtime](./assets/JS-runtime.png?raw=true)

## How does Async JS work if JS is single-threaded?

Asynchronous means that multiple operations can be happening at the same time.

There are 3 common ways to achieve asynchronous code in JS.

1. callbacks
2. promises
3. async / await

Essentially, these callback functions make use of JS runtime's message/callback queue. Anytime callbacks are added to the message queue, JS executes the remaining callstack stack frames first, before processing the items in the message queue.

## ES6 Job Queue/ Micro-Task queue

- ES6 introduced the concept of job queue/micro-task queue which is used by Promises in JavaScript.
  - the difference between the message queue and the job queue is that the job queue has a higher priority than the message queue
  - this means that promise jobs inside the job queue/ micro-task queue will be executed before the callbacks inside the message queue

```
console.log('Script start');
setTimeout(() => {
  console.log('setTimeout');
}, 0);
new Promise((resolve, reject) => {
    resolve('Promise 1 resolved');
  }).then(res => console.log(res));
new Promise((resolve, reject) => {
  resolve('Promise 2 resolved');
  }).then(res => {
       console.log(res);
       return new Promise((resolve, reject) => {
         resolve('Promise 3 resolved');
       })
     }).then(res => console.log(res));
console.log('Script End');
```

This prints:

```
Script start
Script End
Promise 1 resolved
Promise 2 resolved
Promise 3 resolved
setTimeout
```

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

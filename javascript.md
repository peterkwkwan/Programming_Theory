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

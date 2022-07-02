## Blocks

- defined by wrapping one or more statements inside a curly brace pair `{ }`

## Scope

- each function gets its own scope
- lexical scope rules say that code in one scope can access variables of any scope outside of it

## Values & Types

- types in JS
  - string
  - number
  - boolean
  - null & undefined
  - object
  - symbol
- `typeof`
  - returns the type of the value
  - interesting note: `typeof null` will return 'object'

## Comparing values

- Type <strong>coercion</strong> is the automatic or implicit conversion of values from one data type to another.
- Explicit coercion is when you can see the conversion happening in code

  ```
  var a = "42"
  var b = Number(a)
  console.log(typeof b) // number
  ```

- Implicit is when type conversion happens as a nonobvious side effect

  ```
  var a = "42"
  var b = a * 1
  console.log(a) // "42"
  console.log(b) // 42
  ```

## Falsy values in JS

- "" (empty string)
- 0, -0, NaN
- null
- undefined
- false

## Closures

- a way to "remember" and continue to access a function's scope (variables) even after the function has returned & finished execution
- essentially, the arguments and variables of the outer function's scope can still be accessed within the inner function scope

```
function makeAdder(x){

  function add(y){
    return y + x
  }

  return add;
}

const add10 = makeAdder(10)

const add2 = makeAdder(2)

add10(2)
// 12

add2(2)
// 4
```

## Module Pattern

- common usage of closure in JS is the module pattern
- modules allow us to define private implementation details (variables / functions) that are hidden from the outside world (abstration)
- modules allow us to expose a publicly accessible API that uses the private details

## `this` keyword

- `this` points to an object, but it depends on <strong>how</strong> the function was called
- `this` does NOT point to the function itself, as it is the most common misconception

```
function foo() {
  console.log(this.bar)
}

const bar = "global"


let obj1 = {
  bar: "obj1",
  foo:foo
}

let obj2 = {
  bar: "obj2",
}

---

foo(); // "global"

obj1.foo(); // "obj1"

foo.call(obj2); // "obj2"

new foo(); // undefined

```

1. `this` is set to the global object
2. `this` is set to the obj1 object
3. `this` is set to the obj2 object
4. `this` is set to a brand new empty object

## Prototype

- when referencing a non-existent property on an object, Javascript will automatically use that object's internal prototype link to find that property (its 'parent')
- Prototype chain
  - Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype.
  - By definition, <strong>null has no prototype</strong>, and acts as the final link in this prototype chain.

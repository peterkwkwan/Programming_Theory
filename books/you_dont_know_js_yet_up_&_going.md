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

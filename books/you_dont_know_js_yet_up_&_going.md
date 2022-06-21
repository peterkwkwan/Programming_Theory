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

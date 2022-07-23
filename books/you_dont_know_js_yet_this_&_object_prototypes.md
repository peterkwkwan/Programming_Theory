# Chapter 1

### Confusions around using `this`

1. NOT the function itself

The first common temptation is to assume this refers to the function itself. That's a reasonable grammatical inference, at least.

Consider the following code, where we attempt to track how many times a function (foo) was called:

```
function foo(num) {
	console.log( "foo: " + num );

	// keep track of how many times `foo` is called
	this.count++;
}

foo.count = 0;

var i;

for (i=0; i<10; i++) {
	if (i > 5) {
		foo( i );
	}
}
// foo: 6
// foo: 7
// foo: 8
// foo: 9

// how many times was `foo` called?
console.log( foo.count ); // 0 -- WTF?
```

- When the code executes foo.count = 0, indeed it's adding a property count to the function object foo.
- But for the this.count reference inside of the function, this is not in fact pointing at all to that function object, and so even though the property names are the same, the root objects are different, and confusion ensues.

To fix this 'bug', we need to properly call `foo` with a reference of `this` to itself

```
for (i=0; i<10; i++) {
	if (i > 5) {
		// using `call(..)`, we ensure the `this`
		// points at the function object (`foo`) itself
		foo.call( foo, i );
	}
}

console.log( foo.count ); // 4
```

#### Function.prototype.call()

The call() method calls the function with a given this value and arguments provided individually.

```
function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {
  Product.call(this, name, price);
  this.category = 'food';
}

console.log(new Food('cheese', 5).name);
// expected output: "cheese"
```

2. NOT a function's lexical scope

Another common misconception is that `this` somehow refers to the function's scope.

- scope is not accessible to Javascript code
  - scope is part of the engine's implementation

```
function foo() {
	var a = 2;
	bar();
}

function bar() {
	console.log( this.a );
}

foo(); // ReferenceError: a is not defined
```

- THe above code is attempting to use this to create a bridge between the lexical scopes of foo() and bar(), so that bar() has access to the variable a in the inner scope of foo(). No such bridge is possible.
- You cannot use a this reference to look something up in a lexical scope. It is not possible.

## What's `this`?

- `this` is NOT an author-time binding but a RUNTIME binding.
- It is contextual based on the conditions of the function's invocation. `this` binding has nothing to do with where a function is declared, but has instead everything to do with the <strong>manner in which the function is called.</strong>
- When function is invoked, an `execution context` (EC) with the `this` property created to be used within that EC

# Chapter 2

## `this` all makes sense now!

#### The `call-site`

Call-site is the location in code where a function is called FROM (<strong>not where its delcared</strong>).

- depending on the call-site, it will help us identify what `this` is referring to

Call-stack is also important for us to consider as it determines which function is currently executing.

- The call-site we care about is in the invocation before the currently executing function.

```
function baz() {
    // call-stack is: `baz`
    // so, our call-site is in the global scope

    console.log( "baz" );
    bar(); // <-- call-site for `bar`
}

function bar() {
    // call-stack is: `baz` -> `bar`
    // so, our call-site is in `baz`

    console.log( "bar" );
    foo(); // <-- call-site for `foo`
}

function foo() {
    // call-stack is: `baz` -> `bar` -> `foo`
    // so, our call-site is in `bar`

    console.log( "foo" );
}

baz(); // <-- call-site for `baz`
```

#### Default Binding

By understanding the call-site and call-stack, we can determine where `this` will point to during the execution of a function

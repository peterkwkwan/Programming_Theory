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

Call-site is the location in code where a function is called FROM (<strong>not where its declared</strong>).

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

## Call-site rules

By understanding the call-site and call-stack, we can determine where `this` will point to during the execution of a function.

- we must inspect the call-site and determine which of the following 4 rules applies
- there COULD be multiple rules applying to a single call-site

#### 1. Default Binding

- the default rule that applies when no other rules apply

```
function foo() {
	console.log( this.a );
}

var a = 2;

foo(); // 2
```

When foo() is called, `this.a` resolves to our global variable `a`

- Why? Because in this case, the default binding for this applies to the function call, and so points this at the global object.
- How do we know that the default binding rule applies here? We examine the call-site to see how `foo()` is called. In our snippet, `foo()` is called with a plain, un-decorated function reference. None of the other rules we will demonstrate will apply here, so the default binding applies instead.

#### 2. Implicit Binding

- does the call-site have a context object? A.K.A. owning or containing object

```
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

obj.foo(); // 2
```

The call-site uses the `obj` context to reference the function, so you could say that the `obj` object "owns" or "contains" the function reference at the time the function is called.

- At the point that `foo()` is called, it's preceded by an object reference to `obj`
- Because `obj` is the `this` for the `foo()` call, `this.a` is synonymous with `obj.a`

When there is a context object for a function reference, the implicit binding rule says that it's <strong>that</strong> object which should be used for the function call's `this` binding.

##### Implicitly Lost

One of the most common frustrations that `this` binding creates is when an implicitly bound function loses that binding, which usually means it falls back to the default binding.

```
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

var bar = obj.foo; // function reference/alias!

var a = "oops, global"; // `a` also property on global object

bar(); // "oops, global"
```

Even though `bar` appears to be a reference to `obj.foo`, in fact, it's really <strong>just another reference</strong> to `foo` itself. Moreover, the call-site is what matters, and the call-site is `bar()`, which is a plain, un-decorated call and thus the default binding applies.

The more subtle, more common, and more unexpected way this occurs is when we consider passing a callback function:

```
function foo() {
	console.log( this.a );
}

function doFoo(fn) {
	// `fn` is just another reference to `foo`

	fn(); // <-- call-site!
}

var obj = {
	a: 2,
	foo: foo
};

var a = "oops, global"; // `a` also property on global object

doFoo( obj.foo ); // "oops, global"
```

Parameter passing is just an implicit assignment, and since we're passing a function, it's an implicit reference assignment, so the end result is the same as the previous snippet.

#### 3. Explicit Binding

What if we wanted to force a function to use a particular object for the `this` binding, without using a property function reference on the object?

We can use the function `PROTOTYPE` utility methods such as `call` or `apply`.

```
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2
};

foo.call( obj ); // 2
```

> Invoking foo with explicit binding by foo.call(..) allows us to force its this to be obj.

Since we are directly stating what you want the this to be, we call it _explicit binding_.

#### 4. `new` Binding

In traditional class-oriented languages, "constructors" are special methods attached to classes, that when the class is instantiated with a new operator, the constructor of that class is called. This usually looks something like:

`something = new MyClass(..);`

JavaScript has a new operator, and the code pattern to use it looks basically identical to what we see in those class-oriented languages; most developers assume that JavaScript's mechanism is doing something similar. However, there really is no connection to class-oriented functionality implied by new usage in JS.

First, let's re-define what a "constructor" in JavaScript is. In JS, constructors are __just functions__ that happen to be called with the new operator in front of them. They are not attached to classes, nor are they instantiating a class. They are not even special types of functions. They're just regular functions that are, in essence, hijacked by the use of `new` in their invocation.

When a function is invoked with new in front of it, otherwise known as a constructor call, the following things are done automatically:

1) a brand new object is created (aka, constructed) out of thin air
2) the newly constructed object is `[[Prototype]]`-linked
3) the newly constructed object is set as the `this` binding for that function call
4) unless the function returns its own alternate object, the new-invoked function call will _automatically_ return the newly constructed object.

```
function foo(a) {
	this.a = a;
}

var bar = new foo( 2 );
console.log( bar.a ); // 2
```

### Rule precedence

It should be clear that the default binding is the lowest priority rule of the 4.

Which is more precedent, implicit binding or explicit binding? Let's test it:

```
function foo() {
	console.log( this.a );
}

var obj1 = {
	a: 2,
	foo: foo
};

var obj2 = {
	a: 3,
	foo: foo
};

obj1.foo(); // 2
obj2.foo(); // 3

obj1.foo.call( obj2 ); // 3
obj2.foo.call( obj1 ); // 2
```

Explicit binding takes precedence!

What about `new` binding?

```
function foo(something) {
	this.a = something;
}

var obj1 = {
	foo: foo
};

var obj2 = {};

obj1.foo( 2 );
console.log( obj1.a ); // 2

obj1.foo.call( obj2, 3 );
console.log( obj2.a ); // 3

var bar = new obj1.foo( 4 );
console.log( obj1.a ); // 2
console.log( bar.a ); // 4
```

`new` binding is more precedent than implicit binding!

### Determining `this`

Now, we can summarize the rules for determining this from a function call's call-site, in their order of precedence. Ask these questions in this order, and stop when the first rule applies:

1. Is the function called with `new` (_new binding_)? If so, `this` is the newly constructed object.
> `var bar = new foo()`


2. Is the function called with `call` or `apply` (_explicit binding_)? If so, `this` is the explicitly specified object.
> `var bar = foo.call( obj2 )`


3. Is the function called with a `context` (_implicit binding_), otherwise known as an owning or containing object? If so, this is that context object.
> `var bar = obj1.foo()`


4. Otherwise, default the `this` (default binding). If in strict mode, `this` will be `undefined`, otherwise `this` is the global object.
> `var bar = foo()`


### Lexical `this` (arrow functions)

When using arrow functions, we don't follow the 4 standard `this` rules. Arrow functions adopt the enclosing scope (function or global).

```
function foo() {
	// return an arrow function
	return (a) => {
		// `this` here is lexically adopted from `foo()`
		console.log( this.a );
	};
}

var obj1 = {
	a: 2
};

var obj2 = {
	a: 3
};

var bar = foo.call( obj1 );
bar.call( obj2 ); // 2, not 3!
```

The arrow-function created in `foo()` lexically captures whatever `foo()`s this is at its _call-time_. Since `foo()` was `this`-bound to `obj1`, `bar` (a reference to the returned arrow-function) will also be `this`-bound to `obj1`. The lexical binding of an arrow-function cannot be overridden (even with new!).

A common use-case will be inside callbacks:

```
function foo() {
	setTimeout(() => {
		// `this` here is lexically adopted from `foo()`
		console.log( this.a );
	},100);
}

var obj = {
	a: 2
};

foo.call( obj ); // 2
```

While arrow-functions provide an alternative to using `bind(..)` on a function to ensure its `this`, which can seem attractive, it's important to note that they essentially are disabling the traditional `this` mechanism in favor of more widely-understood lexical scoping. Pre-ES6, we already have a fairly common pattern for doing so, which is basically almost indistinguishable from the spirit of ES6 arrow-functions:

```
function foo() {
	var self = this; // lexical capture of `this`
	setTimeout( function(){
		console.log( self.a );
	}, 100 );
}

var obj = {
	a: 2
};

foo.call( obj ); // 2
```

Instead of the four standard binding rules, ES6 arrow-functions use lexical scoping for `this` binding, which means they adopt the `this` binding from its enclosing function call. They are essentially a syntactic replacement of `self = this` in pre-ES6 coding.

# Chapter 3

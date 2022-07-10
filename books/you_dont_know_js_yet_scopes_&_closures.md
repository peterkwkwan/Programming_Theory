# Chapter 1

## What is Scope?

- all programming languages require some way to store values in variables. How does our program find them?
- there are rules / restrictions for storing these variables in some location
- these set of rules can be known as <strong>scope</strong>
  - begets another question. How and where do these scope rules get set?

## Compilation Theory

- 3 major compilation steps

1. Tokenizing/Lexing
   - breaking up a string of characters into meaningful chunks (called tokens)
2. Parsing
   - taking a stream of tokens and turning it into a tree of nested elements
   - the tree, a.k.a. an "AST" (abstract syntax tree), represents the structure of the program
3. Code-generation
   - the process of taking an AST and turning it into executable code
   - turns the AST into a set of machine instructions

- the JS engine is vastly more complex than just these 3 steps, as are most language compilers
- in JS, the compilation happens mere microseconds before the code is executed!
- to ensure fast performance, JS engines use tricks like JIT (just-in-time) to speed up compilation

## Understanding Scope

- We first need to understand who is in charge of determining scope

<strong>The Cast</strong>

1. Engine
   - responsible for start-to-finish compilation and execution of our JS program
2. Compiler
   - one of engine's friends; handles the dirty work of parsing and code-generation
3. Scope
   - another of engine's friends; collects and maintains a look-up list of all the declared identifiers (variables)
   - enforces a strict set of rules as to how these variables are accessible to the currently executing code

> `let a = 2`

- When we encounter something like the above, we think of it as one statement. However that is not how the Engine sees it.
- Engine sees it as 2 separate statements

  - 1 that Compiler will handle during compilation
  - 1 that the Engine will handle during execution

- The first thing that happens is the Compiler will break it into tokens, which then parses it into an AST
- Compiler then asks Scope if variable `a` already exists for that particular scope collection. If so, Compiler will ignore this declaration and move on. Otherwise, the Compiler will ask Scope to declare a new variable called `a` for that scope collection

- Then Engine will later execute this `a = 2` assignment. The code Engine runs will first ask Scope if there is a variable called `a` in the current scope collection. If so, Engine will use the variable. If not, Engine looks elsewhere (nested scope). If it still cannot be found, Engine will raise an error!

## Nested Scope

- usually we have more than one scope to consider. Scopes can be nested inside other scopes
- if variable cannot be found in the current scope, engine consults the next outer scope, continuing until variable is found or the global scope is reached

## Errors

- if the variable lookup was not successful, this results in a `ReferenceError` being thrown by the Engine
- if the program is NOT running in `Strict Mode`, then the global scope will create a new variable of that name <italic>in the global scope</italic>
  - `Strict Mode` disables this automatic/implicit creation of global variables on error

# Chapter 2

## Lexical Scope & Lex-time

- To recap, the 1st phase of language compiling is `lexing` (tokenizing)
  - lexing examines a string of source code characters and assigns semantic meaning to the tokens
- lexical scope is the scope that is defined at lexing time
  - based on where variables and blocks of scope are written
- no matter where a function is invoked from, its lexical scope is ONLY defined by where the function was declared
  - as such, scope is an `author-time` decision

# Chapter 3

## Function vs Block Scope

- JavaScript has function-based scope
  - each function we declare creates its own scope bubbles
- block scope is anything within curly braces `{ }`
- using `let` allows us to use block scope for variable declaration

## Expression vs Declaration

- Easiest way to distinguish declaration vs expression is the position of the word `function` in the statement
- if `function` is the first thing in the statement, then it is a declaration. Otherwise its an expression

## Anonymous vs Named

Anonymous functions have a few downsides

1. no meaningful name to display on stack traces, which can make debugging difficult
2. no descriptive name which may make code less readable
3. if it needs to reference itself (e.g. recursion, unbinding), it is difficult

# Chapter 4

## Hoisting
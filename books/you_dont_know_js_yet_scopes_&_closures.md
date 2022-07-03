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

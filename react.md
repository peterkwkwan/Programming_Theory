# react

## Describe React Virtual DOM

Virtual DOM is a React concept where a 'virtual' representation of the DOM is kept in memory. This Virtual DOM is synced with the real DOM in a process called reconciliation.

In React, you tell the Virtual DOM what state the UI should be in, and it makes sure the DOM matches that state. Using reconcilitation, only the components/elements that have changed will be updated.

Virtual DOM vs traditional DOM manipulation:

_Traditional DOM_

- With Angular, when we pass dynamic data into our template, Angular creates a 'watcher' to monitor for changes in that data. If the value has changed, then it is re-rendered in the UI. By running all the watchers in document, Angular is finding where there needs to be changes. The process of running these watchers is called "dirty checking".

_Virtual DOM_

- With React, instead of finding where the change took place, React re-renders the whole UI from scratch. However, rendering the entire DOM is expensive. This is where Virtual DOM comes into play. React first re-renders a Virtual DOM, and then compares the changes between the Virtual DOM and actual DOM, only changing the elements that are different.

## What is JSX?

React's own templating language, used to produce React elements. Allows us to use JS code inside HTML. It is neither string nor HTML. It is considered a syntax extension of Javascript

Benefits of JSX:

- power of Javascript
- helps reduce redundant code
- faster development time
- improves readability

## Why can't browsers read JSX?

Because JSX is not valid Javascript, as they are embedded in HTML elements. It is a combination of HTML and JS, and thus not supported by browsers.

In order to help browsers parse our JSX code, we use a transpiler like Babel to convert the JSX into JS objects which becomes valid JS.

JSX was not intended to be understood by browsers, but rather intended to be used by transpilers to transform the JSX into Javascript code.

## React vs Angular vs Vue?

Angular

**Advantages**

- Many built-in tools
  - internationalization (i18n)
  - native TS support
  - Angular CLI
- Better for heavy, complex apps that are enterprise-ready
- Two-way data binding

**Disadvantages**

- Steeper learning curve (developer experience not as good)
- Slower than React (uses watchers and traditional DOM updates)
- More breaking changes

React

**Advantages**

- Lightweight and uses JSX for intuitive JS in HTML
- Faster (uses virtual DOM)
- Easier to learn, better dev experience
- Less breaking changes (FB/Meta uses React internally so they understand pain of version updates)
- Faster development time

**Disadvantages**

- Since it is just a light-weight library, may need to do more initial configuration and external package installations to meet project requirements

Vue

**Advantages**

- Better suited for smaller, less complex apps
- Easiest to learn of the 3
- Supports 1 and 2-way data binding
- Uses HTML templates as well as JSX

**Disadvantages**

- Not as widely adopted in the job market

## One-way data binding vs two-way data binding

Data binding is the method to which we connect ('bind') data to the UI to make it dynamic or 'Reactive' to changes.

One

## What are props? What is state?

## Stateful vs stateless components?

## Describe the React lifecycle

## What are refs? What are some scenarios where you will use refs?

## How often do React components re-render?

## Controlled vs Uncontrolled components?

## What is an HOC?

## What are pure components?

## What are keys and their importance in React?

## What is a reducer?

## What is React Redux? What problems does it solve? Limitations?

## What is React Router?

## What is the `<Switch>` tag used for?

## Conventional routing vs React Router?

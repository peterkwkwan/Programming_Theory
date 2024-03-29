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

### <ins>Angular</ins>

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

### <ins>React</ins>

**Advantages**

- Lightweight and uses JSX for intuitive JS in HTML
- Faster (uses virtual DOM)
- Easier to learn, better dev experience
- Less breaking changes (FB/Meta uses React internally so they understand pain of version updates)
- Faster development time

**Disadvantages**

- Since it is just a light-weight library, may need to do more initial configuration and external package installations to meet project requirements

### <ins>Vue</ins>

**Advantages**

- Better suited for smaller, less complex apps
- Easiest to learn of the 3
- Supports 1 and 2-way data binding
- Uses HTML templates as well as JSX

**Disadvantages**

- Not as widely adopted in the job market

## One-way data binding vs two-way data binding

Data binding is the method to which we connect ('bind') data to the UI to make it dynamic or 'Reactive' to changes.

**One-way binding**

- Data flows in a single direction so whenever data changes in the component, it is reflected in the UI
- A single 'watcher' monitoring for data changes from component
- Since data flows in a single direction to the UI, finding bugs/inefficiencies is more straighforward
- UI can never update the model/data. View can only dispatch events/actions (intention to update), but lets the component/controller handle the update

**Two-way binding**

- Data flows in two directions. Any data changes in the component is reflected in UI, and any changes in UI is reflected in component.
- Two watchers for every state. One monitors the UI, one monitors the data.
- Maybe difficult to trace source of data problems, as you can't control the change detection mechanisms (observables, event chains, etc.)
- Provides illusion of one piece of state, but in fact there are two. Overcomplicates the data update process.

## What are props? What is state?

Props

- used to pass data around in React components
- read-only

State

- data that parent components use to manage and maintain a single-source-of-truth.
- affects the performance of the app, as every state update (and subsequent props passed to children) will re-render the component. State should not be used carelessly

Data flow is unilateral (from parent --> child only)

## Stateful vs stateless components?

A.K.A - Smart vs Dumb components

- difference is that one has state and one does not

- stateful components keep track of the state
- stateful components also have a life-cycle (mount, update, unmount)
- avoid creating stateful components unless necesssary
- stateful component encapsulates all of the interaction logic, while the stateless components take care of rendering data/UI

## Describe the React lifecycle

![React Lifecycle](./assets/lifecycle.PNG?raw=true)

1.  ComponentDidMount
    > `useEffect(() => {. . .}, [])`

- on first load

2.  ComponentDidUpdate
    > `useEffect(() => {. . . }, [dependency])`

- on first load AND when dependency changes

3.  ComponentWillUnmount
    > `useEffect(() => { return () => { . . .} }, [])`

- on component unmounting, right before it re-renders. Used for cleanup function
- useful for remove eventListeners, invalidating timers, canceling network requests, remove subscriptions
- takes callback on the return in useEffect hook

## useEffect vs useLayoutEffect ?

Both very identical, the only key difference being `useLayoutEffect` runs before the browser paints the screen.

- `useLayoutEffect` runs before painting
- `useEffect` runs after painting is completed

Good use case for `useLayoutEffect`

- a DOM mutation that must be visible to the user before the next paint
- sometimes you may find `useLayoutEffect` produces animations that look cleaner and faster than `useEffect`

Most of the time we should be using `useEffect` instead because of faster performance. If the DOM manipulation is expensive, `useLayoutEffect` will halt the browser's painting process.

[useEffect vs useLayoutEffect](https://blog.logrocket.com/useeffect-vs-uselayouteffect-examples/)

## What are refs? What are some scenarios where you will use refs?

Refs are an attribute provided by React to access DOM elements.

Use cases:

1. Change the value of a child component without props
2. Managing focus, text-selection
3. Integrating with 3rd party DOM libraries
4. Store a value/state that needs to persist between renders without causing re-renders itself when it changes
   - great for storing prevState values
5. Access DOM elements (similar to `document.querySelector`)

`React.createRef()` used to create the ref

```
const someRef = React.createRef();
<div ref={someRef} />
```

Notes:

- _Refs will persist between renders of your component_
- does NOT cause re-renders of your components when they change
- ref is an OBJECT that contains a `current` property

**Ref.current**

The current value differs depending on where it is used:

- when used in HTML element, `React.createRef()` receives the underlying DOM element as its **current** property
- if used on class component, receives the **mounted** instance of the component as its **current** property
- cannot be used on function components because they don't have an instance

## How often do React components re-render?

1. When `setState()` is called
2. When `props` change
3. When `forceUpdate()` is called

## Controlled vs Uncontrolled components?

This relates to the stateful-ness of DOM form elements.

<ins>Controlled</ins>

- under control of the React component's state
- does not have its own internal state
- React recommends to use Controlled components whenever possible

<ins>Uncontrolled</ins>

- not controlled by React state and handled by DOM instead
- maintains its own internal state (i.e. keeps source of truth in the DOM)
- uses refs to access values
- b/c they are uncontrolled, lifecycle methods will not affect them, which may produce unexpected results

## What is a HOC?

It is a function that takes a component and returns a new component.

Technique used to reuse logic in React components.

You may have a poor use-case for HOCs if:

- The behavior requires adding a bunch of props to a component.
- The behavior is only used in one component.
- The behavior must be customized for each component which uses it.

You may have a good use-case for HOCs if:

- The behavior is not specific to any single component, but rather applies to many or all components in the app, and
- The behavior doesn’t need to provide a bunch of props to the components that use it.
- Components can be used stand-alone without the behavior from the HOC.
- No custom logic needs to be added to a component being wrapped by the HOC.

## What are pure components?

A function is said to be pure if the return value is determined by its input values only and the return value is always the same for the same input values. It does not rely on data outside of the function or perform side effects.

A React component is said to be pure if it renders the same output for the same state and props.

Features of Pure Components

- prevents re-rendering of the component if props / state is the same
- state and props are shallow compared
- better performance since no unnecessary re-rendering

React Components re-renders in the following scenarios:

1. `setState` is called in Component
2. `props` values are updated
3. `this.forceUpdate()` is called

In the case of Pure Components, the React components do not re-render blindly without considering the updated values of React `props` and `state`. If updated values are the same as previous values, render is not triggered.

## What are keys and their importance in React?

Keys are a special attribute needed when creating a list of elements.

Why keys are important - it helps React **identify which items have changed, are added or removed**

Caveat when using keys:

- don't use index if order of items may change. If order changes and we are using index for keys, the unique ID of each element will change according to the change in index order.
  - This will negatively impact performance and cause issues with component state

## What is React Redux? What problems does it solve? Limitations?

Redux is a state management library, making use of a global store to update/change state. It utilizes events called 'actions' to determine the change/event type.

Redux dispatches actions to reducers to update the state.

Problems that Redux solves:

1. eliminate prop drilling in deeply nested components
2. have a centralized store from which to update and share state
3. Redux DevTools are a good way to debug or test your application state
4. state changes are always predictable --> reducers are pure functions

Cons:

1. Increases complexity of your application by introducing an extra overhead layer
2. More boilerplate code

## What is a reducer?

Are a function that takes the current state and action as arguments, then returns a new state

i.e. `(state, action) => newState`

Each action contains a type (also known as an identifier) and a payload. Next, a reducer accepts the action and changes the state based on the received action type and payload.

Notes about reducers:

- they are pure functions (should return the same result every time, given the same params)
- the only way to change state in Redux

## What is React Router?

Provides client-side routing for React apps.

v6 provides Ranked Routes; essentially React Router will search for the best match (no need to mess with `exact` props or `<Switch>`)

e.g. If you are visiting `https://myapp.com/teams/new`, React Router will render `<NewTeam />` because it's more specific than the `:teamId` parameter.

```
<Routes>
    <Route path="teams/:teamId" element={<Team />} />
    <Route path="teams/new" element={<NewTeam />} />
</Routes>
```

## Conventional routing vs React Router?

Conventional routing steps:

1. User requests for route or URL changes
2. Browser to issue a request to the server of the application for new page
3. Server checks for the pathname in the URL and responds with a new HTML page

- Based on client -- server interaction
- causes whole site to refresh because server responds with new page

![Conventional routing](./assets/conventional-routing.png?raw=true)

React Router (client-side routing) steps:

1. User requests for route or URL change
2. Change is detected by JS
3. Browser displays different component(s) based on new route

- no request is sent to server
- JS in browser handles the routing process (SPA)
- browser history stack can be manipulated by client-side routing

![CLient-side routing](./assets/react-routing.png?raw=true)

[Medium - React Routing vs Conventional Routing](https://medium.com/nerd-for-tech/what-is-the-difference-between-react-router-and-conventional-routing-9b11159d92a4)

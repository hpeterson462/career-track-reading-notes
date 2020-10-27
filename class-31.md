# Articles

## *Building Your Own Hooks*

* Extract component logic into reusable functions
* A custom Hook is a JavaScript function whose name starts with ”use” and that may call other Hooks
  * `function useFriendStatus(friendID) {  const [isOnline, setIsOnline] = useState(null);`
* A custom Hook doesn’t need to have a specific signature
  * We decide what it takes as arguments, and what, if anything, it should return 
* Custom Hooks are a mechanism to reuse stateful logic
  * eg: setting up a subscription and remembering the current value
* Every time you use a custom Hook, all state and effects inside of it are fully isolated
* Since Hooks are functions, we can pass information between them


 ## *Rules of Hooks*

* Don’t call Hooks inside loops, conditions, or nested functions
  * This ensures that Hooks are called in the same order each time a component renders 
* Call Hooks from React function components or custom Hooks


## *The Guide to Learning React Hooks*

* First released in October of 2018, the React hook APIs provide an alternative to writing class-based components
* Benefits:
  * Write clearer and more concise code
  * Can omit the usage of `<>` tags wrapped around areas where we want to consume context, which created unwelcome HTML in our component
* 5 rules:
  * Never call Hooks from inside a loop, condition or nested function
  * Hooks should sit at the top-level of your component
  * Only call Hooks from React functional components
  * Never call a Hook from a regular function
  * Hooks can call other Hooks
* Can call useState as many times as you want
* `useReducer` gives us a powerful way to use reducers without depending on the Redux library as a dependency simply to manage UI state
* React Hooks Reducer, similar to the JavaScript Arrays reducer, returns the accumulation of something (React state)
* Can use `useEffect` with or without cleanup
* `useEffect` tells React that our component needs to do something after the component renders
  * Runs after the first render and after every update 
  * Allows you to split up code based on what it's doing rather than what lifecycle method it's in
* Custom Hooks are JavaScript functions whose names are prefixed with the word use


## *10 React Hooks You Should Have in Your Toolbox*

1) `useArray` Hook
  * This hook is a part of the react-hanger package
  * Installation: `yarn add react-hanger`
  * Import: `import {useArray} from 'react-hanger'`
1) React-use-form-state Hook
  * Simplify managing form state
  * Installation: `npm i react-use-form-state`
1) React-fetch-hook
  * Ajax calls
  * Installation: `npm i react-fetch-hook`
  * `useFetch` hook gets us the data and the `isLoading` state
1) useMedia Hook
  * React sensor hook that tracks the state of a CSS media query
  * An object is provided to the hook, which returns a boolean response
1) React-useportal Hook
  * Render children into a DOM node that exists outside the DOM hierarchy of the parent component
  * Installation: `yarn add react-useportal`
  * Two methods `openPortal` and `closePortal`
1) React-firebase-hooks
  * Installation: `npm i react-firebase-hooks`
  * Wraps around the `firebase.auth().onAuthStateChange()` method to ensure that it is always up to date
  * Parameters: `auth: firebase.auth.Auth`
  * Returns: `AuthStateHook` containing:
    * `initialising`: If the listener is still waiting for the user to be loaded
    * `user`: The `firebase.User`, or `null`, if no user is logged in
1) use-onClickOutside Hook
  * An outside click is a way to know if the user clicks everything but a specific component
  * Dropdown menu or a modal or a dropdown list
1) useIntersectionObserver Hook
  * Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document’s viewport
  * Installation: `npm i react-use-intersection-observer`
1) use-location Hook
  * Gets the location of the browser
1) use-redux Hook
  * Returns the store and dispatch property
  * `dispatch` method is responsible for firing actions that cause changes in the store

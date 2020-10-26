# Articles

## *Hooks at a Glance*

* Hooks are backwards-compatible
* State hook
  * `useState` is a hook that's called inside a function component to add local state to it
  * React preserves state between re-renders
  * `useState` return a pair:
    * the current state value
    * a function from an event handler or somewhere else
  * Similar to `this.setState` in a class, except it doesn’t merge the old and new state together
  * Can use State Hook more than once in a single component
* Hooks are functions that let you “hook into”
  * Hooks let you use React without classes 
    * They don't work inside classes
  * React provides a few built-in Hooks like `useState`
* Effect hook
  * The Effect Hook, `useEffect`, adds the ability to perform side effects from a function component
  * Serves the same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in React classes, but unified into a single API
  *When you call `useEffect`, you’re telling React to run your “effect” function after flushing changes to the DOM
  * Effects are declared inside the component so they have access to its props and state
  * By default, React runs the effects after every render — including the first render
  * Effects may also optionally specify how to “clean up” after them by returning a function
  * Hooks let you organize side effects in a component by what pieces are related
* 2 rules of Hooks:
  * Only call Hooks at the top level - not in loops, conditions, or nested functions
  * Only call Hooks from React function components - not JS functions


## *Using the State Hook*

* Hooks don’t work inside classes
* Can use them instead of writing classes
* A Hook is a special function that lets you “hook into” React features
* Use Hook when you write function component and need to add state
* No `this` - no `this.state`
* Hook state doesn’t have to be an object - can be number or string
*  `useState` returns a pair of values 
  * current state
  * function that updates it
* `const [count, setCount] = useState()` similar to `this.state.count` and `this.setState`
  * variable names in brackets on left side of `=` can be any names
  * Declaring state variables as a pair of `[something, setSomething]` is also handy because it lets us give different names to different state variables if we want to use more than one


## *Using the Effect Hook*

* The Effect Hook lets you perform side effects in function components
* There are two common kinds of side effects in React components:
  * Those that don't require cleanup
    * Run additional code after React has updated the DOM
    * Network requests, manual DOM mutations, and logging
  * Those that require cleanup
    * React performs the cleanup when the component unmounts
    * Cleans up the previous effects before applying the next effects
    * In a React class, you would typically set up a subscription in `componentDidMount`, and clean it up in `componentWillUnmount`
    * Every effect may return a function that cleans up after it
    * This lets us keep the logic for adding and removing subscriptions close to each other
* In React class components, the `render` method itself shouldn’t cause side effects
  * Put side effects into componentDidMount and componentDidUpdate
* Placing useEffect inside the component lets us access the props state variable
  * Hooks embrace JavaScript closures and avoid introducing React-specific APIs where JavaScript already provides a solution
  * `useEffect` runs after every render
* You can use several effects like you can use State Hook more than once
* Hooks let us split the code based on what it is doing rather than a lifecycle method name


## *Hooks API Reference*

* `useState` returns a stateful value and a function to update it
* `useState` does not automatically merge update objects
  * Can replicate this behavior by combining the function updater form with object spread 
  * `useReducer` manages state objects that contain multiple sub-values
* `initialState` argument is the state used during the initial render
* If doing expensive calculations while rendering, you can optimize them with `useMemo`
* `useCallback` will return a memoized version of the callback that only changes if one of the dependencies has changed
* `useRef` returns a mutable ref object whose `.current` property is initialized to the passed argument (`initialValue`)
* `useRef()` creates a plain JavaScript object
* `useImperativeHandle` customizes the instance value that is exposed to parent components when using `ref`

# Articles

## *Context*

* Provides a way to pass data through the component tree without having to pass props down manually at every level
* In a typical React application, data is passed top-down (parent to child) via props
* Designed to share data that can be considered “global”
  * eg: current authenticated user, theme, or preferred language
* Every Context object comes with a Provider React component that allows consuming components to subscribe to context changes
  * Provider component accepts a value prop to be passed to consuming components that are descendants of this Providers
  * Provider can be connected to many consumers
  * Providers can be nested to override values deeper within the tree
    8 All consumers that are descendants of a Provider will re-render whenever the Provider’s `value` prop changes
  * `<MyContext.Provider value={/* some value */}>`
* `contextType` property on a class can be assigned a Context object created by `React.createContext()`
  * Lets you consume the nearest current value of that Context type using `this.context`
* You can only subscribe to a single context using this API
* `<MyContext.Consumer>`
  * Lets you subscribe to a context within a function component
  * Requires a function as a child
  * Receives the current context value and returns a React node
  * Value argument passed to the function will be equal to the value prop of the closest Provider for this context above in the tree
  * If there is no Provider for this context above, the `value` argument will be equal to the `defaultValue` that was passed to `createContext()`
* Context object accepts a `displayName` string property
  * `MyContext.displayName = 'MyDisplayName';`
* To avoid re-render every time the Provider re-renders because a new object is created for `value`, lift `value` into parent's state

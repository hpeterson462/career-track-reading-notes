# Articles

## *setState*

* React components have state
  * render UI based on state
* `setState()` is the only legitimate way to update state after the initial state setup
* Reconciliation: the way React updates the DOM by making changes to the component based on change in state
  * Doesn't necessarily change entire tree, except where root of tree is changed
* When `setState()` triggered, React creates a new tree containing reactive elements in component 
  * tree used to figure out how UI should render
  * will only update parts of the DOM where necessary = React is fast
* React workflow:
  1) component defined
  1) component currently empty
  1) user submits component variable
  1) variable captured and stored by `setState()` as value
  1) reconciliation takes place and React notices change in value
  1) React instructs component to update value and variable is merged in
* Never mutate state directly - will not re-render
  * always use `setState()` to change state
* Can `setState()` to functions 
  * React will queue function calls in order they are made
  * updates entire state when done


## *Lists and Keys*

* `key` is a special string attribute included when creating lists of elements
  * help React identify which items have been changed, added, or removed
  * should be given to elements inside array to give a stable identity
    * if none provided, React will default to indexes as keys
  * must be unique among siblings
  * don't get passed to components


## *Typechecking with PropTypes*

* React has built-in typechecking abilities
* `PropTypes.element` will specify that only a single child can be passed to component as children
* If using Babel transform (` transform-class-properties`), you can declare `defaultProps` as static property within React component
* `defaultProps` used to ensure that `this.props.name` will have value if not specified by parent component


## *Components and Props*

* Components let you split UI into independent, reusable pieces
* Similar to JS functions
* Elements can also represent user-defined components


## *Handling Events*

* React events:
  * Named using camelCase
  * JSX function passed as event handler
  * Can't return false to prevent default behavior
* Provide event listener when element is initially rendered
* Must invoke this callback with `()`


## *Snapshot Testing*

* Renders a UI component, takes a snapshot, then compares it to a reference snapshot file stored alongside the test
* Jest uses pretty-format to make snapshots human-readable
* In Interactive Snapshot Mode, Jest will step you through the failed snapshots one test at a time and give you the opportunity to review the failed output
* Inline snapshots behave identically to external snapshots (.snap files), except the snapshot values are written automatically back into the source code
* Ensure that your snapshots are readable by keeping them focused, short, and by using tools that enforce these stylistic conventions
* Tests should be deterministic
  * Should produce the same results every time on code that hasn't been changed
* Use descriptive snapshot names
  * Describe the expected snapshot content
* All snapshot files should be committed
  * Jest can tell what changed from previous versions
  * Provides context during code review
* Visual regression testing tools take screenshots of web pages and compare the resulting images pixel by pixel
* Snapshot testing values are serialized, stored within text files, and compared using a diff algorithm
* Snapshot files must always represent the current state of the modules they are covering


## *Introducing the React Testing Library*

* Light weight solution for testing React components
*  functions on top of `react-dom` and `react-dom/test-utils`, in a way that encourages better testing practices
* Replacement for enzyme
* Intended for react-dom
* This library is not:
  * A test runner or framework
  * Specific testing framework 
* In your test you'll need to find the `<input />` so you can set its value to something
* `wait` resembles exactly what the users does
* Doesn't have utilities that enable testing implementation details
* Focuses on providing utilities that encourage good testing and software practices
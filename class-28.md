# Articles

## *Architectural Styles and Architectural Patterns*

* Architectural Pattern - a general and reusable solution to an occurring problem in a particular context
  * Understand how the major parts of the system fit together and how messages and data flow through the system
    * Multiple patterns in a single system to optimize each section
* Design Patterns impact a specific section of the code base, Architectural Patterns are high-level strategies that concern large-scale components
* Idiom - a low-level pattern specific to a programming language
  * How to implement particular aspects of the components
* Architectural  Patterns/Styles:
  * Layered 
    * structure programs that can be decomposed into groups of subtasks - eg: Model-View-Controller structure (MVC)
    * 4 layers:
      1) presentation
      1) application
      1) business logic
      1) data access
  * Event-Driven (EDA)
    * organizes a system around the production, detection and consumption of events
    * easily adaptable to complex environments
    * Emitters - an event source and only knows that the event has occurred
    * Consumers - needs to know an event has occurred and it has the responsibility of applying a reaction
  * Domain Driven Design (DDD)
    * object-oriented
    * design software based on the Business Domain
      * sphere of knowledge and activity around which the application logic revolves
    * eases communication and improves flexibility
    * useful when we build complex software where the need for change is determined
  * Pipes and Filters
    * decomposes a task that performs complex processing into a series of separate elements that can be reused
    * can be broken down into a set of independent steps
    * Filters - components that transform or filter data
    * Pipes - components that connects passing data to Filters
    * Pump - components where data is sourced
    * Sink - final target component
  * Microservices
    * creates several tiny programs instead of one big app
    * every service to be completely independent
    

## *Container and Presentation Patterns*

* Splits code into two distinct places:
  1) Containers : are stateful components that contain your business login
    * how things work
    * manage state, fetch data from APIs, setup event handlers, and pass information to other components via props
  1) Presentations : are stateless components that present your data
    * how things look
    * receive props and use those props to render and style DOM
* My App
  * src
    * assets
      * myImg.png
    * components
      * Component Name
        * ComponentName.css
        * ComponentName.jsx
        * ComponentName.test.jsx
    * containers
      * Container Name
        * ContainerName.jsx
        * ContainerName.test.jsx
    * services
      * myService.js
    * index.js


## *Container Component Details*

* Responsible for specifying how a section of our application works
  * Manage state, fetch data from apis, and setup event handlers
* Class Containers
  * 1st popular
  * at that time, state and lifecycle methods only available within class components
  * highlight the dichotomy between container components (classes) and presentational components (functions)
  * created by extending the react `Component` class
  * initialize state in two ways: 
    * class properties
    * inside a constructor
  * `this.setState` to set state
  * `this.setState` merges your update into the previous state ({ …oldState, …newState }) and initiates a re-render
  * can fetch data inside lifecycle methods
    * fetch data with a service function
    * if your component always needs to fetch some data, you can use `componentDidMount` to fetch your data right as your component is mounted
  * `useState` to initialize state
    * should be a JavaScript primitive (string, number, boolean, null, undefined) or a simple array
    * independent state changes, can be done by passing a new value to `setSomeState`
    * State changes that do rely on the previous state, dependent state changes, can be done by passing a function to `setSomeState`
    * Fetching data and setting the fetched data in state is considered a side effect
      * `useEffect` hook to handle side effects
      * 2 arguments:
        * a function that preforms the side effect
        * an array of values that, when changed, trigger the side effect
* Containers as Hooks
  * containers can also be written as custom hooks, rather than as components


## *Presentation Details*

* Specify how a section of our page looks
* Written as functional components
* When passing props, use the `prop-types` package to specify the props our component receives
  * warning message to other devs


## *Functional vs Class-Components in React* 

* Simplest way to define a component in React:
  `class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}`
* Differences between funtional and class Components:
  * Syntax
    * functional - plain JS function that accepts props as argument and returns React element
      * can't use state (stateless components)
      * easier to read and test
      * less code
      * performance boost
    * class - requires you to extend from React.Component and create a render function that returns a React element
      * can use lifecycle hooks and state
      * more code


## *Conditional Rendering*

* Works the same way as JS conditions (if else, &&, etc.)
* Use variables to store elements
* If the condition is true, the element right after && will appear in the output. If it is false, React will ignore and skip it
* Can use ternary (`condition ? true : false`)
* Returning null from a component’s render method does not affect the firing of the component’s lifecycle methods
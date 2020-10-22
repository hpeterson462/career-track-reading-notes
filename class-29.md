# Articles

## *MVC*

* Model View Controller
* Software design pattern 
  * Divides logic into 3 parts:
    * Model
    * View
    * Controller
* Model
  * Central component
  * Manages data, logic and rules of app
* View
  * Presentation of info such as chart, diagram or table
  * Multiple views of the same info are possible
* Controller
  * Accepts input and converts it to commands for the model or view
* MVC has been widely adopted as a design for World Wide Web applications in major programming languages


## *4 Layers of Single Page Applications*

* View
  * Presentational Components
    * receives state through props
    * emit new state through events
  * Container Components
    * receive state from the store
    * supply state to presentational components
    * send new state to the store
* Application Services
  * interpret state
  * orchestrate external operations
* Store
  * holds state
  * state is immutable
  * acts as a publisher
  * notifies Subscribers about state changes
* Domain
  * represents state
* Domain Services
  * encapsulates business logic
  * side-effect free
* State
  * represents every piece of data that changes in an application


## *A Model View Controller Pattern for React*

* Hooks - 2019 React introduced
  * helps pull behavior into common locations and re-use behavior across other components
* MVC is an object-oriented programming (OOP) pattern
* React is a mix of Object Oriented Programming and Functional Programming
* MVC pattern breaks down into 2 parts:
  * Presentation Layer of Controller and View React Components
    * access/knowledge of domain objects and logic
    * categorizing components:
      * controllers - what they know
        * knows how to access and update domain data (app state)
        * knows how to choose and execute domain logic
      * view - what they do
        * doesn't know app state
        * calls hooks for UI-specific cases 
          * accessing context for UI data and behavior
          * syncing prop changes with local state with `useEffect()`
  * UI-Agnostic Data Model


## *Reconcilation*

* React provides a declarative API so that you don’t have to worry about exactly what changes on every update
* A single point in time you can think of the render() function as creating a tree of React elements
* On the next state or props update, that render() function will return a different tree of React elements
* Whenever the root elements have different types, React will tear down the old tree and build the new tree from scratch
* It is important to remember that the reconciliation algorithm is an implementation detail
* If you see yourself alternating between two component types with very similar output, you may want to make it the same type
* Keys should be stable, predictable, and unique
# Articles

## *10 JavaScript Array Methods You Should Know *

1) forEach()
    1) iterate over an array's items
        1) `  const arr = [1, 2, 3, 4, 5, 6];

  arr.forEach(item => {
    console.log(item); // output: 1 2 3 4 5 6
  });`
1) includes()
    1) check if an array includes item passed
        1) `  const arr = [1, 2, 3, 4, 5, 6];

  arr.includes(2); // output: true
  arr.includes(7); // output: false`
1) filter()
    1) creates a new array with only the elements passed 
        1) const arr = [1, 2, 3, 4, 5, 6];

  // item(s) greater than 3
  const filtered = arr.filter(num => num > 3);
  console.log(filtered); // output: [4, 5, 6]

  console.log(arr); // output: [1, 2, 3, 4, 5, 6]
1) map()
    1) creates a new array by calling the provided function in every element
        1)  `const arr = [1, 2, 3, 4, 5, 6];

  // add one to every element
  const oneAdded = arr.map(num => num + 1);
  console.log(oneAdded); // output [2, 3, 4, 5, 6, 7]

  console.log(arr); // output: [1, 2, 3, 4, 5, 6]`
1) reduce()
    1) applies a function against an accumulator and each element in the array to reduce it to a single value
        1) ` const arr = [1, 2, 3, 4, 5, 6];

  const sum = arr.reduce((total, value) => total + value, 0);
  console.log(sum); // 21`
1) some()
    1) checks if at least one of the array's item passed the condition
        1) `const arr = [1, 2, 3, 4, 5, 6];

  // at least one element is greater than 4?
  const largeNum = arr.some(num => num > 4);
  console.log(largeNum); // output: true

  // at least one element is less than or equal to 0?
  const smallNum = arr.some(num => num <= 0);
  console.log(smallNum); // output: false`
1) every()
    1) checks if all array's items passed the condition - if passed, it will return true (else false)
        1) `  const arr = [1, 2, 3, 4, 5, 6];

  // all elements are greater than 4
  const greaterFour = arr.every(num => num > 4);
  console.log(greaterFour); // output: false

  // all elements are less than 10
  const lessTen = arr.every(num => num < 10);
  console.log(lessTen); // output: true`
1) sort()
    1) sort an array's items either ascending or descending order
        1)   const arr = [1, 2, 3, 4, 5, 6];
  const alpha = ['e', 'a', 'c', 'u', 'y'];

  // sort in descending order
  descOrder = arr.sort((a, b) => a > b ? -1 : 1);
  console.log(descOrder); // output: [6, 5, 4, 3, 2, 1]

  // sort in ascending order
  ascOrder = alpha.sort((a, b) => a > b ? 1 : -1);
  console.log(ascOrder); // output: ['a', 'c', 'e', 'u', 'y']
1) Array.from()
    1) change all things that are array-like or iterable into true array (esp when working with DOM) - so you can use other methods like reduce, map, or filter
        1) `  const name = 'frugence';
  const nameArray = Array.from(name);

  console.log(name); // output: frugence
  console.log(nameArray); // output: ['f', 'r', 'u', 'g', 'e', 'n', 'c', 'e']`
1) Array.of()
    1) creates an array from every argument passed into it
        1) ` const lis = document.querySelectorAll('li');
  const lisArray = Array.from(document.querySelectorAll('li'));`


## *A Civilized Guide to JS Array Methods*

* find()
    * returns first element in an array that matches parameter
* map()
  * applies a given function to every item in an array and returns a new array with those values
* filter()
  * removes items from array that don't meet params given
* concat()
  * adds new items to the end of an array
* flatMap()
  * pass a function that returns flattened values into one array
* join()
  * inserts string between each item and returns one joined string
* every()
  * checks every item in an array and matches parameters
* some()
  * checks at least one item in an array that matches parameters
* includes()
  * checks at least one item in array that matches parameter
* reduce()
  * processes each item of an array and modifies value
* forEach()
  * applies given function to every element in an array


## *Class Basic Syntax*

  * Basic class syntax:
    * `class MyClass {
  constructor() { ... }
  method1() { ... }
  method2() { ... }
  method3() { ... }
  ...
}`
* `new MyClass` creates a new object with all listed methods above
* `constructor()` method is automatically called by `new` 
* When `new Class('theirClass')` is called:
  * A new object is created
  * `constructor` runs with given argument and assigns `this.name` to it
* Common mistake is to put a comma between class methods - results in syntax error
* Class - a kind of function
* `class MyClass` creates a function named `MyClass`
  * Stores class methods in `MyClass.prototype`
* Classes can be defined inside another expression
* Classes my include getters/setters
  * `class User {

  constructor(name) {
    // invokes the setter
    this.name = name;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    if (value.length < 4) {
      alert("Name is too short.");
      return;
    }
    this._name = value;
  }

}`
* Write `=` in class definition for old browsers that need a polyfill
* Bind the method to the object in the constructor
  * `class Button {
  constructor(value) {
    this.value = value;
  }
  click = () => {
    alert(this.value);
  }
}`


## *MDN - Classes*

* Classes are a template for creating objects
  * Encapsulate data
  * Built on prototypes
  * "Special functions"
* Class declarations
  * Use `class` keyword with the name of the class
    * `class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}`
  * Hoisted
* Class expressions
  * Can be named or unnamed
  * Name given to a named class expression is local to the class's body
    * `// unnamed
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};`
    * `// named
let Rectangle = class Rectangle2 {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};`
* Body of a class is executed in strict mode
  * Code written here is subject to stricter syntax
* `constructor` method is a special method for creating and initializing an object created with a `class`
  * Can use the `super` keyword to call constructor of the super class
* `static` keyword defines method that is called without instantiating - can't ben called through a class instance
  * Used to create utility functions
  * `this` is undefined inside static method - must rewrite using non-strict mode
  * `class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  static distance(a, b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;

    return Math.hypot(dx, dy);
  }
}`
* `extends` keyword used to create a class as a child of another class
  * `
class Dog extends Animal {
  constructor(name) {
    super(name); // call the super class constructor and pass in the name parameter
  }`
* 


## *MVC Architecture in 5 Minutes*

* Model View Controller is a predictable software design pattern that can be used across many frameworks with many programming languages
* One of the most widely used software design patterns for app and web development
* Separates concerns into 3 buckets:
  * Model
    * Data - stores and manages, often databse
  * View
    * GUI - visual representation of data
  * Controller
    * Brains - converts inputs from view to retrieve/update data
* Benefits:
  * Responsibilities are divided between the client & server
  * Design pattern when planning development
  * Separation of concerns
  * Removes unnecessary dependencies
  * Reuseable without modification
  * Easier to maintain or modify
  * Supports multiple views
  * Each part can be tested independently
* Separation of Concerns - dividing logic up so each bucket can act independently
  * Each team member can work on their piece at the same time
* Loosely Coupled - each piece is independent of each other
  * Organization simple and easy to understand and keeps maintenance easier


# Video

## *MCV in 4 Minutes*

* Patterns make code less complex and easier to work with
* MVC is most popular
* Model
  * Handles data logic
  * Data munging
  * Interacts with database
  * Sends response back to Controller
* Controller
  * Handles request
  * Not much code
  * Sends response/presentation back to user
* View
  * Receives from Controller
  * Handles data presentation
  * Dynamically rendered
  * Sends presentation back to Controller

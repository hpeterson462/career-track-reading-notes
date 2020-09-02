# Articles

## *Quantity Always Trumps Quality*

*  'The works of highest quality were all produced by the group being graded for quantity.'
* Quantity always trumps quality
* Until you've mentally committed to doing it over and over, you will not improve
* If you aren't building, you aren't learning


## *Clean Code - Chapter 1*

* Good code is essential
* Bad code can lead to 'wading' through it
    * Hard to maintain, update, and debug
* Over a year or two, teams that were moving very fast at the beginning of a project can find themselves moving very slow
* As the mess builds, the productivity of the team continues to decrease
* Clean code:
    * Efficient
    * Elegant 
    * Error handling
    * Minimal maintenance 
    * Focused
    * Readability
* As students practice and refine their skill, they often go on to create their own school of thought
    * Each school teaches what is right by their philosophy, but does not invalidate the other schools of thought


## *Red, Green, Refactor*

 * Test-driven development (TDD) 
    * Write tests first
* Focus into three phases:
    * Red — think about what you want to develop
        * Write a test that informs the implementation of a feature
    * Green — think about how to make your tests pass
        * Implement code to make your test pass
    * Refactor — think about how to improve your existing implementation
        * Implement your code better or more efficiently


## *The Cycles of TDD*

* Write one line of a failing test, and then write the corresponding line of production code to make it pass
* Three rules:
    1) Must write failing test before you write production code
    1) Don't write more than one test
    1) Don't write more production code than is sufficient to make current failing test pass
* You can get stuck because not adding enough generality to production code - making tests too specific too quick
* All cycles of TDD should drive towards clean architecture
    * Every hour stop and analyze 


## *MDN - Promises*

* Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value
* Promise is a proxy value 
* State of a Promise:
    * Pending - initial state, neither fulfilled or rejected
    * Fulfilled - operation successfully completed 
    * Rejected - operation failed
* Chained Promises help to further handle promise action:
    * promise.then()
    * promise.catch()
    * promise.finally()


## *MDN - Destructuring Assignment*

* Unpack values from arrays or properties from objects into distinct variables
* Basic variable assignment:
    * `const x = [1, 2, 3, 4, 5];
    const [y, z] = x;`
* Assignment separate from declaration
    * `let a, b;
[a, b] = [1, 2];`
* Default values
    * `let a, b;
[a=5, b=7] = [1];`
* Swapping variables
    * `let a = 1;
let b = 3;
[a, b] = [b, a];`
* The prototype chain is looked up when the object is deconstructed 
    * `let obj = {self: '123'};
obj.__proto__.prot = '456';
const {self, prot} = obj;`


## *MDN - Spread Syntax*

* Allows an iterable (ie: string, array) to be replaced with `...` when several arguments are expected
* Functions:
    * `myFunction(...iterableObj);`
* Arrays:
    * `[...iterableObj, '4', 'five', 6];`
* Object literals
    * `let objClone = { ...obj };`


## *MDN - Rest Parameters*

* Represents an indefinite number of arguments as an array
    * `function f(a, b, ...theArgs) {
  // ...
}`
* Rest parameters vs arguments:
    * Rest parameters are given separate name
    * Arguments contain all arguments passed to function
    * Arguments have additional functionality (callbacks)


# Videos

## *TDD, Where Did It All Go Wrong*

* TDD helps all devs write better code
* 3x more test code than production code
    * Slower when writing tests
    * Break tests when making changes or refactoring code (mocked tests)
* Trigger to writing TDD - when you want software to do something
* Test public API 
    * Write tests only against stable contract (API)
* Module is a capsule that stores public information
* System under test (SUT) is not a class - it's a facade
* Write tests that prove behaviors of in the system work
* Tests run in isolation
* 3 Steps:
    1) Red - write a test that doesn't work
    1) Green - make a test work quickly (committing any sins necessary - Stack Overflow)
    1) Refactor - eliminate all duplications and write good code
* Avoid heavy mocking
* Test behavior not implementations
* Coding pyramid
    1) UI (top)
    1) Integration
    1) Unit Tests (bottom)
* Hexagonal architecture

## *What the Heck is the Event Loop Anyway?*

* JS is single-threaded call stack - one thing runs at a time
* Blocking - stops from processing because something else is running
* Async callbacks fix blocking problem
* Event loop runs first thing in queue once stack is clear
* Async processes faster
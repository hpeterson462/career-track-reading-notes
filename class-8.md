# Articles

## *Express - Routing*

* How app endpoints (URLs) respond to client requests
* Use methods of Express app object that correspond to HTTP methods
* Express supports methods that correspond to all HTTP request methods: get, post, update, delete, patch, option
* Route paths define endpoints at which requests can be made
  * Strings, string patterns, or regular expressions
* Route parameters are named URL segments that are used to capture the values specified at their position in the URL
* Can provide multiple callback functions that behave like middleware to handle a request
  * Written as function, array of functions, or both
* The methods on the response object (res) can send a response to the client and terminate the request-response cycle
* Create chainable route handlers for route path by using `app.route()`
* `express.Router` class to create modular, mountable route handlers


## *Supertest*

* `npm install supertest --save-dev`
* `require('supertest');`
* SuperTest works with any test framework
* Expectations are run in the order of definition


## *Express - Middleware*
* Middleware functions are functions that have access to the request object (`req`), the response object (`res`), and the `next` middleware function in the application’s request-response cycle
* Denoted by a variable named `next`
* Perform tasks:
  * Execute any code
  * Make changes to request and response objects
  * End request-response cycle
  * Call next middleware function in stack
* Route handlers enable you to define multiple routes for a path
* `const router = express.Router()`
* Load router-level middleware by using the `router.use()` and `router.METHOD()` functions
* To skip the rest of the router’s middleware functions, call `next('router')`
* Define error-handling middleware functions with the signature (`err, req, res, next`)
* Use third-party middleware to add functionality to Express apps
* `$ npm install cookie-parser`


## *ExpressJS - Middleware*

* Middleware functions are functions that have access to the request object (req), the response object (res)
* Order of execution matters
* Use middleware before and after route handler
* Body-parser used to parse body of requests which have payloads attached to them
* Cookie-parser used to parse cookie header and populate req.cookies with object keyed by cookie names
* Express-session creates a session middleware with the given options


## *Express - Express - Middleware*

* body-parser `express.bodyParser`
* compression `express.compress`
* connect-rid
* cookie-parser `express.cookieParser`
* cookie-session `express.cookieSession`
* cors
* csurf `express.csurf`
* errorhandler `express.errorHandler`
* method-override `express.methodOverride`
* morgan `express.logger`
* multer `express.bodyParser`
* response-time `express.responseTime`
* serve-favicon `express.favicon`
* session `express.session`
* timeout `express.timeout`
* vhost `express.vhost`
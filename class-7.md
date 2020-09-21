# Articles

## *HTTP*

* Hypertext Transfer Protocol
* Stateless, application-layer protocol for communicating between distributed systems
* Foundation of modern web
* Allows for communication between variety of hosts and clients
* Supports mixture of network configurations
* Doesn't keep state between different message exchanges
* Communication between a host and a client occurs by a request/response pair
* URL - Uniform Resource Locator - heart of web communications
  * URLs reveal the identity of the particular host with which we want to communicate, but the action that should be performed on the host is specified via HTTP verbs
  * Request Verbs:
    * GET
    * POST
    * PUT
    * DELETE
    * HEAD
    * TRACE
    * OPTIONS
  * Server responds with status codes and message payloads
  * Codes:
    * 200s - Successful
    * 200 - ok
    * 202 - accepted
    * 204 - no content - no message body in response
    * 205 - rest content - client needs to reset its document view
    * 206 - partial content - additional headers exact range and content expiration info
    * 300s - Redirection
    * 301 - moved permanently
    * 303 resource temporarily located at new URL
    * 304 - not modified - client should use cached copy
    * 400s - Client Error
    * 400 - bad request - request malformed
    * 401 - unauthorized
    * 403 - forbidden
    * 405 - method not allowed - invalid HTTP verb
    * 409 - conflict - server couldn't complete request because client is trying to modify resource that's newer than client's timestamp (mostly PUT requests)
    * 500s - Server Error
    * 501 - not implemented - server doesn't support requested functionality
    * 503 - service unavailable
  * Message can contain one or more headers - 
    * General
    * Request
    * Response
    * Entity
* Chrome/Webkit inspector to view HTTP communication
* ExpressJS library 
* jQuery Ajax library


## *How DNS Works*

* Computers and other devices communicate using IP addresses to identify each other
* Domain Name System (DNS) brings IP addresses and human names together to get you to your destination
* OS calls resolver if browser and OS both don't know IP address for website
* Resolver is usually Internet Service Provider (ISP) 
  * Knows where to locate root server
    * Top Level Domain (TLD)
* Root server is top of DNS hierarchy
  * operated by 12 independent world organizations
  * each organiZation provides multiple physical servers distributed around the globe
* Each organization provides multiple physical servers distributed around the globe  
  * Country code TLDs. Usually, their 2 letter ISO code
  * Internationalized country code TLDs
  * Generic TLDs: .NET, .ORG, .EDU, etc... 
  * Infrastructure TLDs: .ARPA, mostly used for reverse DNS lookups
* Domain registrar points to authoritative name server
* Extra info attached to response of resolver
  * resolver gets at least one IP address for each name server


## *REST APIs*

* Application Program Interface (API)
  * Contract provided by one piece of software to another
  * Structured request and response
  * Messenger between running software (waiter between guest and kitchen)
* Representational State Transfer (REST)
  * Architecture style for designing networked apps
  * Relies on stateless, client-server protocol (HTTP)
  * Treats server objects as resources that can be created or destroyed
  * Can be used by virtually any programing language
* HTTP Methods
  * GET - retrieve
  * POST - submit
  * PUT - update
  * HEAD - same as GET but no return body
  * OPTIONS - returns supported HTTP methods
  * PATCH - updates partial resources
* Endpoints - URL where api can be accessed by client app
* Authentication may be required
  * OAUTH - access token
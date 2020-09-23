# Articles

## *Authentication*

* User modeling:
  * Behind firewall/password protected:
    * emails, user names, addresses
  * Encrypted (hash algorithm):
    * user passwords - even devs not able to see
  * Info should never be sent to client apps
* Cryptography:
  * Science that studies methods for encoding messages so they can only be read by a person who knows the secret info required to decode
* Hash algorithms:
  * Takes a piece of data and produces a hash that is deliberately difficult to reverse
  * Identical data always produces same hash
  * Server compares hash login with previously stored hashed password to determine authentication
* Cypher algorithms:
  * Takes  a piece of data and a key and produces encrypted data
  * User tokens can be created by associated a random unique string (tokenSeed) with a user account
  * tokenSeed unique to database and can be queried to produce user who made request
* Basic Authorization
  * Common method used to send a username and password in an HTTP request
  * Joined with a ‘:’ then “base64 encoded” and placed after the string ‘Basic ‘
  * Value of Authorization header
  * Server can decode the Basic Authorization header to retrieve the username and password


## *HTTP*

  * Basic access authentication is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request
  * No mechanism to provide confidentiality protection for transmitted items
  * Basic authentication is typically used in conjunction with HTTPS to provide confidentiality

  
## *JSON Web Tokens*

* Securely transmits information between parties as a JSON object
* Used for:
  * Authorizaiton
  * Info Exchange
* Structure - 3 parts separated by dots:
  * Header - 2 parts - type of token & signing algorithm used
  * Payload - contains claims - statements about entity - 3 types
    * registered
    * public
    * private claims
  * Signature - used to verify message wasn't changed along the way
  * `xxxxx.yyyyy.zzzzz`
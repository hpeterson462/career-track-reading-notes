# Articles

## *Why you should use BCrypt to hash passwords*

* Plain text password:
  * Only letters
  * Easy to pose as user by hacker
* One way hash:
  * Server does not store plain text passwords to authenticate user
  * Hackers can continually guess until they gain access
* Salting password:
  *  ‘Salt’ adds a very long string of bytes to the password
  * If a hacker has access to your source code, they will easily be able to find the ‘salt’ string for passwords
* Random ‘salt’ for each user:
  * 'Salt' string created on generation of user account
  * Will increase encryption, but still gain access
* BCrypt:
  * BCrypt hashing function — designed by Niels Provos and David Mazières in 1999
  * Based on the Blowfish block cipher cryptomatic algorithm
  * Using a Key Factor, BCrypt is able to adjust the cost of hashing 
  * BCrypt remains extremely resistant to hacks, especially a type of password cracking called rainbow table
  * Key Factor compensates for these powerful computers and slows down hashing speed


## *Hashing in Action: Understanding bcrypt*

* Never store passwords as plain text - hash instead
* Hashing alone is not sufficient to mitigate more involved attacks such as rainbow tables
* Salting - adding additional random data to the input of a hashing function that makes each password hash unique
* How fast a cryptographic function can calculate a hash has an immediate and significant bearing on how safe the password is
  * Faster calculations mean faster brute-force attacks
* AuthO uses bcrypt algorithm to securely hash and salt passwords
* Original crypt of 1976 could hash fewer than 4 passwords per second, but with growth of technology, a fast computer with optimized software and hardware was capable of hashing 200,000 passwords per second using that function
* Blowfish cipher is a fast block cipher except when changing keys -  parameters that establish functional output of a cryptographic algorithm
* Benefits of bcrypt:
  * Slower algorithm to reduce any benefits attackers may get from faster hardware
  * Requires salt by default 
  * 128-bit salt and encrypts a 192-bit magic value
* Set up of bcrypt:
  1) Function called `EksBlowfishSetup` is used at the desired cost, the salt, and the password to initialize the state of `eksblowfish`
  1) Run key schedule 
    * Performs key derivation - derives set of subkeys from primary (password used as primary)
  1)  Password stretched longer if user password is too short - key stretching
  1) Magic value is the 192-bit value `OrpheanBeholderScryDoubt` - encrypted 64 times using `eksblowfish`
  1) Prefixes are added to indicate usage of bcrypt and its version
  1) Bcrypt achieves the three core properties of a secure password function:
    * pre-image resistant
    * salt space is large enough to mitigate precomputation attacks (ie: rainbow tables)
    * adaptable cost
* Install: 
  * `npm instal bcrypt`
  * On point of entry server file (app.js): 
    * `const bcrypt = require("bcrypt");
const saltRounds = 10;
const plainTextPassword1 = "DFGh5546*%^__90";`
  * `saltRounds` - cost or work factor
* Using the `bycrypt.hash` method, let's see how we can compare a provided password with a created hash


## *Token Storage*

* App that calls APIs on behalf of the user needs access tokens and (optionally) refresh tokens
* Stored server-side or in a session cookie
* Cookie needs to be encrypted and have a maximum size of 4 KB
* Native/mobile apps - store tokens in secure storage given
* Single-page apps - use AuthO to handle token storage
* Browser in-memory - Auth0 recommends storing tokens in browser memory as the most secure option
  *  Web Workers handle transmission and storage of tokens
* Browser local storage - alternative to mechanisms that require retrieving the access token from an iframe and to cookie-based authentication 
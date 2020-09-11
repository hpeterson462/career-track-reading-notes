# Articles

## *Web Scraping with JS and Node.js*

* For Javascript to interact with your browser, the browser provides a Runtime Environment to make it possible to run on server
* Can't manipulate the computer or it's resources directly
* Node.js was created to make JS capable of running client-side and server-side 
  * Google's Chrome's v8 JS Engine and embedded it with C++ program 
* HTTP clients are tools capable of sending a request to a server and then receive a response from it
* Request widely used HTTP client
  * `const request = require('request')
request('https://www.reddit.com/r/programming.json', function (
  error,
  response,
  body
) {
  console.error('error:', error)
  console.log('body:', body)
})`
* Axios is a promise-based HTTP client that runs both in the browser and NodeJS
  * `const axios = require('axios')

axios
	.get('https://www.reddit.com/r/programming.json')
	.then((response) => {
		console.log(response)
	})
	.catch((error) => {
		console.error(error)
	});`
* Async Function
  * `async function getForum() {
	try {
		const response = await axios.get(
			'https://www.reddit.com/r/programming.json'
		)
		console.log(response)
	} catch (error) {
		console.error(error)
	}
}`
* Superagent is another robust HTTP client that has support for promises and the async/await syntax
  * `const superagent = require("superagent")
const forumURL = "https://www.reddit.com/r/programming.json"

// callbacks
superagent
	.get(forumURL)
	.end((error, response) => {
		console.log(response)
	})

// promises
superagent
	.get(forumURL)
	.then((response) => {
		console.log(response)
	})
	.catch((error) => {
		console.error(error)
	})

// promises with async/await
async function getForum() {
	try {
		const response = await superagent.get(forumURL)
		console.log(response)
	} catch (error) {
		console.error(error)
	}
}`
* The simplest way to get started with web scraping without any dependencies is to use a bunch of regular expressions on the HTML string that you receive by querying a webpage using an HTTP client
  * `const htmlString = '<label>Username: John Doe</label>'
const result = htmlString.match(/<label>(.+)<\/label>/)

console.log(result[1], result[1].split(": ")[1])
// Username: John Doe, John Doe`
  * `match()` returns an array that matches regular expression
* Cheerio is an efficient and light library which allows you to use the rich and powerful API of JQuery on the server-side
  * Removes all the DOM inconsistencies and browser-related features and exposes an efficient API to parse and manipulate the DOM
  * Does not:
    * render any parsed or manipulated DOM elements
    * apply CSS or load external resources
    * execute JS
  * `const cheerio = require('cheerio')
const $ = cheerio.load('<h2 class="title">Hello world</h2>')

$('h2.title').text('Hello there!')
$('h2').addClass('welcome')

$.html()
// <h2 class="title welcome">Hello there!</h2>`
  * `const axios = require('axios');
const cheerio = require('cheerio');

const getPostTitles = async () => {
	try {
		const { data } = await axios.get(
			'https://old.reddit.com/r/programming/'
		);
		const $ = cheerio.load(data);
		const postTitles = [];

		$('div > p.title > a').each((_idx, el) => {
			const postTitle = $(el).text()
			postTitles.push(postTitle)
		});

		return postTitles;
	} catch (error) {
		throw error;
	}
};

getPostTitles()
.then((postTitles) => console.log(postTitles));`
  * `getPostTitles()` is an asynchronous function that will crawl forum
* JSDOM is a pure Javascript implementation of the Document Object Model to be used in NodeJS
  * JSDOM creates a DOM
  * `const { JSDOM } = require('jsdom')
const { document } = new JSDOM(
	'<h2 class="title">Hello world</h2>'
).window
const heading = document.querySelector('.title')
heading.textContent = 'Hello there!'
heading.classList.add('welcome')

heading.innerHTML
// <h2 class="title welcome">Hello there!</h2>`
* Puppeteer manipulates the browser programmatically
  * Provides API to control headless version of Chrome by default
  * generate screenshots or PDFs of pages
  * crawl a Single Page Application and generate pre-rendered content
  * automate different user interactions 
  * `const puppeteer = require('puppeteer')

async function getVisual() {
	try {
		const URL = 'https://www.reddit.com/r/programming/'
		const browser = await puppeteer.launch()
		const page = await browser.newPage()

		await page.goto(URL)
		await page.screenshot({ path: 'screenshot.png' })
		await page.pdf({ path: 'page.pdf' })

		await browser.close()
	} catch (error) {
		console.error(error)
	}
}

getVisual()`
* Nightmare
	* High-level browser automation library like Puppeteer, that uses Electron
	* `const Nightmare = require('nightmare')
const nightmare = Nightmare()

nightmare
	.goto('https://www.google.com/')
	.type("input[title='Search']", 'ScrapingBee')
	.click("input[value='Google Search']")
	.wait('#rso > div:nth-child(1) > div > div > div.r > a')
	.evaluate(
		() =>
			document.querySelector(
				'#rso > div:nth-child(1) > div > div > div.r > a'
			).href
	)
	.end()
	.then((link) => {
		console.log('Scraping Bee Web Link': link)
	})
	.catch((error) => {
		console.error('Search failed:', error)
	})`


## *MDN - Document.querySelector()*

* return first element within document that mathces the specified selector or group of selectors
* if no matches found, returns null
* `element = document.querySelector(selectors);`
* parameters - selectors
	* must be a CSS selector string
* `\` to escape special characters


## *MDN - Document.querySelectorAll()*

* returns static NodeList representing a list of document's elements that match the specified group of selectors
* parameters - selectors
	* must be a CSS selector string
* `let matches = document.querySelectorAll("p");`
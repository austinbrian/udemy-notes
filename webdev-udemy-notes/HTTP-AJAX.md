# Web-based Data Exchange
---
## HTTP
**HTTP** paved the way for client-server protocol, allowing our apps to communicate with the outside world.
- Messages sent by a client (usually a web browser) are called *requests*
- Messages sent by the server are called *responses*

There are only a few message types:
- GET : ask a server to get something, server will respond with that request
- POST : do something with this file, add it to your database
- PUT : update an existing piece of data
- DELETE


GET requests return Query String data
POST requests put the data in the body

## JSON
- Syntax for storing and exchanging data; text written in JS object notation
- considered more succinct and useful than XML, which is an essentially similar
- JSON is just text, each entry must be double quotes ""

JSON can be parsed easily by javascript, both to and from javascript objects

```js
var obj = json.parse('{"name":"John","age":30,"city":"New York"}');

var jString = json.stringify(obj);
```

## AJAX
**AJAX** allows you to read from a webserver and update a web page without reloading the entire thing.

It's a technology created by Google, called XHR (XML HTTP Request).

### Fetch
The current way to use AJAX is by using `fetch`.

```js
fetch('my/url').then(response => {
    consle.log(response);
});
```
This means that page updates are a lot quicker, it downloads less data.

**AJAX allows applications to change content dynamically** and it is *everywhere*.

### Promise
Promises result from fetch requests. *Promise* says that it is making a request somewhere over the internet and when it is returned, it will return a *Result*.
- access the value in a promise using a `.then` method
- convert the Response using `response.json()`, and call a `.then` method again.

## Promises, continued
New feature as a part of ES6, replacing callbacks.
A promise is an object that may produce a single value some time in the future. The value can be either a resolved value, or a reason that it's not resolved.

Promises can be in one of three states:
- Fulfilled
- Rejected
- Pending

### Promise Syntax
```js
const promise = new Promise((resolve, reject) => {
    if (true) {
        resolve("Stuff worked");
    } else {
        reject("Error, it broke")
    }
})

// then to evaluate the promise
promise.then(result => console.log(result)); // this will log "Stuff worked"
```

Promises can be chained together, allowing you to execute multiple functions on one returned object.

```js
promise
    .then(result => result + '!')
    .then(result2 => {
        console.log(result2);
    })
// this results in: Stuff Worked!
```

Errors can also be caught by promises using `.catch(() => console.log('error!'))`, which catches any errors above the `catch` statement.

Promises are like event listeners, except that they can only ever succeed or fail *once*. This makes them especially apt for asynchronous success or failure, such as API calls. More interested in reacting to the outcome of things

**Important note**: `fetch` returns a Promise

## Async / Await

Async/await code is syntactic sugar for promises. It allows asynchronous code to look like synchronous code.

The two sets of code block below are equivalent:
```js
movePlayer(100, "Left")
    .then(() => movePlayer(400, 'Left'))
    .then(() => movePlayer(10, 'Right'))
    .then(() => movePlayer(330, 'Left'))


async function playserStart() {
    const firstMove = await movePlayer(100, 'Left'); // pause
    const secondMove = await movePlayer(400, 'Left'); // pause
    await movePlayer(10, 'Right'); // pause
    await movePlayer(330, 'Left'); // pause
}
```
Await can be invoked only when a function is declared as an async function. You can put `await` in front of any function that returns a promise.

The keyword says "pause this function until we've resolved this part" every time. If you assign variables for each of these, then the variables will asynchronously hold the values that should be in each of those.

So these two are equivalent:
```js
fetch('https://jsonplaceholder.typicode.com/users')
    .then(resp => resp.json())
    .then(console.log)

async function fetchUsers() {
    const resp = await fetch('https://jsonplaceholder.typicode.com/users')
    const data = await resp.json();
    console.log(data);
}
```
Let's do one more example, in which we get a range of things. We'll do it using the `Promise.all` syntax, as well as using a set of deconstructed array syntax using async/await.

```js
const urls =[
    'https://jsonplaceholder.typicode.com/users'
    'https://jsonplaceholder.typicode.com/posts'
    'https://jsonplaceholder.typicode.com/albums'
]

Promise.all(urls.map(url =>
    fetch(url).then(resp => resp.json())
)).then(array => {
    console.log('users',array[0])
    console.log('posts',array[1])
    console.log('albums',array[2])
}).catch('oops');


const getData = async function() {
    // use a little ES6 destructuring magic
    const [ users, posts, albums ] = await Promise.all(urls.map(url =>
        fetch(url).then(resp => resp.json())
    ))
    console.log('users',users) // OK since we declared these as variables
    console.log('posts',posts)
    console.log('albums',albums)
}
```
Catching errors, unfortunately, requires you to execute these in try/catch blocks.

```js
const getData = async function() {
    try {
        const [ users, posts, albums ] = await Promise.all(urls.map(url =>
            fetch(url).then(resp => resp.json())
        ))
        console.log('users',users)
        console.log('posts',posts)
        console.log('albums',albums)
    } catch (err) {         // have to pass in the error to the catch
        console.log('oops', err)
    }
```

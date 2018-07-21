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

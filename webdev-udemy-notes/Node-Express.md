# Node.js

Node.js allows you to use a javascript in the terminal.

There are no "window" or "document" objects, but instead there are:
- `global`: gives access to builtin functions (e.g., `setTimeout`)
- `process`: operating system or IDE functions


# Express
Express is a library for Node that helps write servers.

## Express middleware
```js
app.use((req, res, next) => {
    console.log('HELLO') // this is logged to node server, not browser
    next(); // this next allows us to move on to the next as well
})
app.get('/', (req, res) => {
    res.send(
        "<h1>Welcome to express server</h1><br>\
        <h2>'Hello' was sent to the server</h2>"
    )
})
```

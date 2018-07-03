## Modules
What's so wrong with just using `<script>` tags?
1. You have to remember to add them into each new webpage you make.
2. Polluting the global namespace
3. The lack of *dependency resolution*. So you have to make sure that the order of the script tags you add to a page need to declare functions in the order that they will be used by later scripts.

### IIFE
**Immediately Invoked Function Execution** wraps a function in parens, then runs the function. Looks like:
```JavaScript
var myApp = {}

(function() {
    myApp.add = function(a,b) {
        return a+b;
    }
})() // includes a call of the function created here
```
Notice that it calls the function immediately upon creating it. This solves the global namespace problem, as we don't even really bother with naming the function, and it just limits the variable to be `myApp`

### CommonJS + Browserify
This tool analyzes the javascript, finding all the functions, then exports them all to a single file, usually called "bundle.js", which is then called in the `<script>` tag.
```javascript
// js1
module.exports = function add(a,b){
    return a+b;
}

//js2
var add = require("./add");
```

...and there are other ways

### ES6 Webpack
Introduced the keywords `export` and `import`, and can use the destructuring syntax that we introduced in [ES6](ES6.md#Destructuring).
```javascript
//js1
export const add = (a,b) => a+b;
// or
export default function add() {
    return a+b;
}

//js2
import { add } from './add/';
//or
import add from './add/';
```
Put the imports at the top so we know exactly what each file needs.
`export default` is used when you only want to default one thing. Use `export` to send each function to the file.

#### Webpack
Weback is a module bundler, which bundles javascript files. It traverses the dependency tree and moves it into a single file. With Webpack we can use ES6 in all browsers. *This is where we are now, and it's what React uses*

Webpack has a config file that just has a file like 'bundle.js'.


## Resources
- https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/

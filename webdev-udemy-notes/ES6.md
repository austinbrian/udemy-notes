# ES6 and JavaScript
ES6 stands for ECMAScript version 6. Version 5 and Version 6 introduced some new features to JavaScript that are widely used now. 

## Babel
Babel is a Javascript compiler that enables next-generation Javascript. It reads the script line-by-line and then rewrites it into the older version. This means new features are supported using Babel.

## Let and const
We don't really ever need to use `var` ever again.

`let` allows the creation of variables inside an "if" scope.

`const` does not allow for a variable to be updated. If you have anything that's not going to change, it should be `const`.

For instance, if it's going to be a function, you can make it as a `const`.
If you're assigning a variable that might change (like a boolean val), use `let`

## Destructuring
Imagine you have some object with various attributes:
  `const user = { name: "Brian", experience: 40, advanced_degree: false }`
Using this deconstructing syntax, you can assign values out of the object keys. 
So rather than doing this, which is repetitive: 
  ```javascript
  const name = user.name;
  const experience = user.experience;
  let degree  = user.advanced_degree;
  ```
  you can do this:
  ```javascript
  const { name, experience } = user;
  let { advanced_degree } = user;
  ```
  and that is … better? I guess?
  
  Seems like it's useful for react.

## Template Strings
There work like format strings, but they use backticks. Make sure to use the curly braces for the variables within the string. Here is the syntax: 
```javascript
  const name = "Sally"; 
  const age = 34; 
  const pet = "fish"; 
  
  const greeting = `Hello ${name}, are you ${age-5}? That's a nice ${pet}.`
  ```
You can calculate things within the string.


## Default Argument
Work just like python default args.

## One last type
**Symbol** - (uses `let`) creates a unique 

## Arrow functions
Change the function syntax to take away the curly braces where there is only one return. 

So instead of:
```javascript
function exponentiation(a,b) {
    return a**b;
    }
```
you can do this all on one line, using `const`:
`const exp = (a,b) => a**b;`

But if you need more than one line, you can always use the curly braces like so: 
```javascript
    const whereAmI = (username, location) => {
        if (username && location) {
            return "I am not lost";
        } else {
            return "I am totally lost!":
        }
    }
```
   


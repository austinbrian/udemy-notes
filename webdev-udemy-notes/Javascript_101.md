# Javascript 101
Javascript is a way to build in actions for websites. ECMAScript is an interchangeable name for it.

## Types
- Number
- String
- Boolean


### Double vs triple equals
In Javascript, `==` and `===` mean two slightly different things. Double equals means JS will try to coerce types, *then* evaluate. So `77=='77'` evaluates as `true`. 

Conversely, the `===` checks for both type and value equality, with no conversions. This will evaluate `77==='77'` as `false`. It is a better metruc to use as a test of equality, in general.

#### Other "falsy" values
Under coerced types, other values will evaluate as equivalent: 
`false == 0 == ''` <-- boolean false and 0 are equivalent, as is empty string
`null == undefied` <-- null and undefined are only equal to themselves and each other; they return false against any other number
`NaN` <-- Not a Number doesn't even evaluate as true with itself

## Variables
Variables need to start with a letter, dollar sign, or underscore
- multi-word variables typically use camelCase 
- `prompt()` asks for user input, returns a string 
- `Number("77")` converts a string number to a number 

## Expressions 
Semicolons indicate the end of an expression. 

```javascript
var name = "Billy"
if (name === "Billy") {
    alert("hi Billy);
    } else if  (name === "Susy") {
    alert("hi Susy");
    } else {
        alert("hmmm I don't know you");
    }
```

#### Conditional logical operators
- **||** means "OR"
- **&&** means "AND"
- **!** negates, meaning "NOT"

## Javascript in the browser
Use the `<script src="FILL ME IN"></script>` tag, and fill in the source. 
Use `console.log("String to fill in")` to print to the console log, rather than, say doing an alert. 

## Functions
- **Function declaration**
  ```javascript
  function sayHello() { 
      console.log("Hello");
  }
  ```
  - Remember to call the function like `sayHello();`

- **Function expression**
  ```javascript
  var sayBye = function() {
      console.log("Bye");
  }
  ```
  - Note that the function itself doesn't really have a name -- it is just assigned to the `sayBye` variable; it is referred to as an anonymous function.
- Function arguments enable extensibility
- **Arguments** -- functions can have arguments and they get called with arguments
- **Parameters** -- the values that are fed into arguments

## Data Structures
- **Arrays** - like python lists, start at 0
  `var n_array = ["tiger", "cat", "bear", "bird"]`
  - Arrays with mixed types are less performant
  - Can create arrays of arrays
  - `n_array.shift()` returns the first element of the array, and takes it out of the list
  - `n_array.pop()` returns the last element of the array, pops it off the list
  - `n_array.push('new_element')` returns the new length of the array after adding 'new_element' to the end of the array
  - `n_array.concat(['new','items'])` adds those items onto the end of the array, but needs to be assigned to the variable because it doesn't change in-place
  - `n_array.sort()` returns a sorted array
- **Objects** - collections of property, like python dictionary
  `var user = {name:"John",age:34,hobby:"Soccer",isMarried:false}`
  - supports both dot notation (`user.name`) and bracket notation (`user['age']`)
  - Arrays are really just objects with numbered keys
  - Ojects can also include functions -- these are methods

## Loops
```javascript

var todos = [
  "clean room",
  "brush teeth",
  "exercise",
  "study",
  "eat"
];

for (var i=0; i < todos.length; i++) {
  console.log(todos[i], i) 
}

var counterOne = 0;
while (counterOne <10) {
  console.log(counterOne);
  counterOne++; // if you want to subtract, use `--`
}

var counterTwo = 10;
do {
  console.log(counterTwo);
  counterTwo--;
} while (counterTwo > 0);

todos.forEach(function(todo, i) { 
  console.log(todo, i); 
}) // Kind of works like enumerate

// Alternately, declare your function outside
function logTodos(todo, i) { 
  console.log(todo, i); 
} 
todos.forEach(logTodos)
```


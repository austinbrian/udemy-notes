# Advanced Topics
---
## Advanced Arrays
You can't just assign an array to be 2 * n for all n as a new array. Instead, you have to call `push` like you would have to call `list.append(n)` in python.

```JavaScript
const array = [1,2,10,16]

const double = []
const newArray = array.forEach((num) => {double.push(num*2)})
```

But there are better ways. Namely, `map`, `filter`, and `reduce`. Whenever you feel the urge to do a for loop in the future, you probably want to use one of these instead.

### Map
The way to do the above without using the kind of dumb repetitive for-loop syntax is by mapping the function over the array with `map`.

If you want to apply a change, use the `map`, but if you want to do other things, like write to the console, you might need `forEach`. `forEach` does a bunch of actions that aren't as limited, but have a lot more side-effects.

**REMEMBER** that you have to return something from map

```JavaScript
const mapArray = array.map((num) => {
    return num*2
});
```
Also, if you're only taking in a single parameter, you can drop the parameter parens. If you're only returning a single value/line, you can drop the curly braces and return, using the arrow function shortcut syntax. So the above turns into:
```javascript
const mapArray = array.map(num => num*2);
```

### Filter
As the name suggests, we can filter our array on a condition.

```JavaScript
const filterArray = array.filter(num => {
    return n>5
});
```
The same type of shortcut we used before holds true.


### Reduce
You can do filtering and mapping with reduce. Here's a simple example.
```javascript
const reduceArray = array.reduce((acccumulator, num) => {
    return accumulator +num
}, 0)

```
- **num** is the iteration value of the list
- **accumulator** (sometimes listed as "acc") somewhere to store the information that happens in the body of a function as we iterate. So in the above example, we're adding each value to the acccumulator parameter, starting at 0 (the final parameter, which is the starting point).

This is the same as if we started with a counter in a for loop, then added to the counter as we went. Nice.


## Advanced objects
Reference type, context, and instantiation.

### Scope vs Context
**Scope** is created when it sees curly braces. Anything inside them is a private little world that isn't available to parent scope.

**Context** is a question about where in an object you are.
- uses `this`

What `this` means is "what is the object environment that we are in right now"
- aka, what is to the "left" of the dot

### Instantiation
This uses the class object, but with `this` basically in place of python's `self`.

The constructor method initializes the object (like an `init`).
```javascript
class Player {
    constructor(name, type) {
        this.name = name;
        this.type = type;
    }
    introduce() {
        console.log(`Hi I am ${this.name}, I'm a ${this.type}`)
    }
}

```

You can also extend a class (like subclassing). Whenever you extend a class, you use `super` to access the base class's initializations.

```JavaScript
class Wizard extends Player {
    constructor(name, type) {
        super(name,type)
    }
    play() {
        console.log(`YAAASS I'm a ${this.type} Wizard`)
    }
}
```
And then to instantiate the classes, use `new` before them.
```javascript
const wizard1 = new Wizard('Veronica','Dark Magic')
const wizard2 = new Wizard('Betty','Executioner')
```


## ES7
ES7 just adds two new things to the programming language.
- **includes** returns `true` when a value is in an array; works for both strings and arrays:  
    `"Hellooo".includes('o');` will return `true`
- **exponential operator** is the `**` method:  
    `2**3;` will return `8`

## ES8
A couple new functions.
- **string padding** will pad either the start (`.padStart(n)`) or the end (`.padEnd(n)`) such that the full string has `n` characters. If `n` is less than the total number of characters than the string, it will return just the string.
- **trailing commas** makes it so if you define a function, you can leave a comma at the end of the last parameter without it creating problems.
- **Object methods** call the keys and values in various ways:
    - `Object.keys(obj)` generates an array of the keys of an object
    - `Object.values(obj)` generates an array of the values of an object
    - `Object.entries(obj)` generates an array of key, value pair for *each* key-value pair in an object

## Async / await
(Return to this in a future video)

## Debugger
Put `debugger;` into the code somewhere, and when the code hits the debugger, it will step into the debugger console in the window. From there, you can select step through to move through the code line-by-line.

## Call stacks
Javascript is single-threaded. So it has one call stack -- first-in, last out.

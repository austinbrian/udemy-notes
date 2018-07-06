# React
---
React is like a bread machine - you can throw a bunch of components in and get out something nice.
The key thing react does is *change the view* of the DOM in predictable ways that are easy to scale and easy to manage.

Can be used in:
- mobile devices
- desktop applications
- web applications (of course)

## Introduction
Takes really small indivisible pieces and combines them into progressively larger components.
- So for instance, if there is a back button built from a react component, can reuse that.
- And a navigation bar that is composed of several react components can similarly be used across a range of things

### One Way Data Flow
Data flows from top to bottom, and never the other way around. If the children know about a data change, only *their children* would know about the change, never the parents.
- a DAG

### Virtual DOM
The virtual DOM is a JavaScript object that describes the current state of the website. We give that site to the React bot and the bot will take care of DOM manipulation for you. So the virtual DOM is a copy of what is in the browser in a Javascript object, and react, under the hood, changes the view.

### React ecosystem
- React packages in npm
- Can use with Node
- Webpack, Babel both work with it

---
## Building our first react app
We can now use `import` syntax since react is running webpack under the hood, so we can bring in any packages we want.

### ReactDOM
This is the glue for websites, so it will provide ways to manipulate the DOM. Could also have, for example, ReactNative, that powers mobile apps.

## Render
All react apps must render something. So that will likely be the function call of the class instantiation. Like so:
```JavaScript
class Hello extends Component {
    render() {
        return (
            <div>
                <h1>Hello World</h1>
                <p>If you want a multi-line return, wrap it in parens so the whole expression is evaluated.</p>
            </div>
        );
    }
}
// to call it elsewhere, you have to export
export default Hello;
```

## Tachyons
A useful styling library.
Load using `npm install tachyons`

## JSX
HTML-like text written in JavaScript. Has the idea that *components*, rather than filetypes, should be severable.

Underneath the hood, react uses JSX to change the virtual DOM. For instance:
```js
class Hello extends Component {
    render() {
        return (
            <div className='f1 tc'> // JSX uses "className"
                <h1>Hello World</h1>
                </div>
        );
    }
}
```
JSX uses `className` rather than the HTML "class" because `class` is a reserved Javascript keyword.

## State
State is an object that describes your application as it relates to the data flow into and out of components at any given time.

**Props** are simply things that come out of state.
    STATE ---> PROPS

- State usually lives in the parent component, so it can pass to children.
- When you create events to change state, `event.target.value` will return the value of the event.
- As a rule, if you are making your own functions within a React class, you should use the arrow function syntax.
- Components with state are sometimes called "smart components"

## REST APIs

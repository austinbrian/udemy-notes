# CSS

The very basic outline for all CSS is as follows:   
```css
Selector {
    Property: value;
}
```

Insert a link to the css styles in the `<head>` section of the html file.
  `<link rel="stylesheet" type="text/css" href="style.css">`
  - Atom makes this work by typing "link" then TAB

## CSS Properties
Recommended resource: [CSS tricks](https://css-tricks.com)

### body
  background-image: url(insert url);
  background-size: cover;

**display** -- inline-block sets up items in a div to be across


## Resource for Colors
[paletton.com](http://paletton.com) -- gives you complementary color suggestions with hex code / RGB

### RGB
ex:
  `border: 5px solid rgb(255, 0, 0)` will create a 5-pixel border that is all red

`rgba(255,0,0,0.5)` adds an alpha term, which will create some transparency
- 1 is totally solid, 0 is totally invisible

## CSS Selectors
The class attribute can be used to identify types of CSS objects. [Reference here](https://www.w3schools.com/cssref/css_selectors.asp)

- **.class** -- identifies sets of styles using the `class="exampletext"` attribute in a stylesheet
  `.exampletext { color:black;}`
- **#.id** -- identifies sets of styles using the `id="identifier1"` attribute
  `#identifier1 { background-color:aliceblue;}`
- **'*'** -- hard to bold that one, but it means everything, usually at the top, but it doesn't seem super useful?
- **element** -- just that element, which makes sense
- **element, element2** -- apply the same style to both these elements
- **element element2** -- apply this style to element2s that are within element
- **element > element2** -- apply this to all element2s that have a parent of element
- **element + element2** -- select any element2 that is exactly *after* element

#### Each of these comes right after the element
So you'll type something like `.exampletext:hover`
- **:hover** -- apply after you hover over it
- **:focus** -- apply when it's in focus
- **:last-child** -- apply to only the last child in a div (usually in a div)
- **:first-child** -- apply to only the first child
- **!important** -- overrules the cascading part of the style sheet (not recommended)

### Ranking of cascade
- Specificity
- Importance
- Source order

## Box model
If I save some divs as class "boxmodel"
```html
<div class="boxmodel">A</div>
<div class="boxmodel">B</div>
<div class="boxmodel">C</div>
```
Then style them in CSS

```css
.boxmodel {
    border: 5px solid red;
    display: incline-block;
    padding: 5px 20px 5px 20px; /* Always goes top, right, bottom, left (clockwise) */
    margin: 0px 20px; /* First is top/bottom, second is left/right */
}
```

## px vs em vs pt
Start with pixels, so you can make a font, say 20 pixels high (or pt, using standard font points)
`p {font-size: 20px}`

But then if you find yourself with a span that you want to be different
`<p>Lorem <span>ipsum</span> dolor sit amet</p>`   

Let's say you want that span to be twice the size, so you can use `em`
`span {font-size: 2em}`


# Advanced CSS topics
---
## Critical Render Path
- The path that a browser takes to render a website:
  - html
  - then css
  - any outside APIs (like fonts) that the CSS calls
- CSS being unloaded will block the website from rendering
- Might suggest keeping CSS files relatively small, or minifying them


## Flexbox
- **justify-content** -- how spread you want the elements to be (the main axis), and where you want to start from
  - *flex-start* -- to the left, to the left
  - *flex-end* -- to the right, to the right
  - *space-between* -- edges pushed to the outside margin
  - *space-around* -- same amount of space around each element
- **align-items** -- aligns flex items along the cross axis
  - *flex-start* -- top of the container
  - *flex-end* -- bottom of the container
- **flex-direction** -- orientation of the items
  - *row*
  - *column*
  - *row-reverse*
  - *column-reverse


Resources:
- https://darekkay.com/dev/flexbox-cheatsheet.html

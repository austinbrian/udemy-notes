# Document Object Model
## DOM Selectors
These three are a little older, but super useful
- **getElementsByTagName**
- **getElementsByClassName** -- uses the class, similar to the way CSS does
- **getElementByID** -- uses the #id to grab the element
These are more modern
- **document.querySelector('h1')** -- can select property, but only grabs the first one
- **document.querySelectorAll('p')** -- gets all the paragraph tags, in this case
- **document.querySelectorAll('h1','p')** -- gets all the h1 and p tags

### Setting new attributes
- **document.getAttribute** -- have to select an attribute, or you can use it in conjunction with queryselector, like so:
  `document.querySelector('li').getAttribute('id')`
- **document.setAttribute** -- similarly, you can use this to set new attributes

### Changing Styles
- style.{property} //ok
- className //best
- classList //best

- classList.add
- classList.remove
- classList.toggle //Toggles between true and false

innerHTML //DANGEROUS

parentElement
children

#### It is important to CACHE selectors in variables

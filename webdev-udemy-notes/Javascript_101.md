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

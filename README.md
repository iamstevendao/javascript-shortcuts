# Javascript Shortcuts
**Easy** and **short** syntaxes in Javascript which are **less common**, get updated whenever I see a new one.

## Table of Contents
- [Use + to convert String to Number](#use--to-convert-string-to-number)
- [Spread syntax (...)](#spread-syntax-)
- [Template literals (\` \`)](#template-literals--)
- [Number Truncation](#number-truncation)
- [Short syntax for Object Properties Initializer](#short-syntax-for-object-properties-initializer)
- [Short syntax for Method Definitions on Objects Initializers](#short-syntax-for-method-definitions-on-objects-initializers)

## Use + to convert String to Number
```js
+'3' === 3
+'3' === Number(3)
```
where I saw it: [learnyoumongo](https://github.com/evanlucas/learnyoumongo)

## Spread syntax (...)
Super powerful one with a fully detailed explanation at [moz://a](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

Examples:
```js
var parts = ['shoulders', 'knees']; 
var lyrics = ['head', ...parts, 'and', 'toes']; 
// ["head", "shoulders", "knees", "and", "toes"]

var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2]; // arr1 = arr1.concat(arr2);
```

## Template literals (\` \`)
Probably appears around ES5 and 6  
Provides another way to write multi-line strings:
```js
console.log('string text line 1\n' +
            'string text line 2');
console.log(`string text line 1
             string text line 2`);
// same result:
// "string text line 1
// string text line 2"
```
And another way to put variables straight away in the string:
```js
// in ES5:
var str = 'Hello world!, ' + first + ' ' + last + '.'
// now:
var str = `Hello world!, ${first} ${last}.`
```
There's more at [moz://a](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

## Number Truncation
Truncate a floating point number to its integral part, completely dropping the fractional part.
```js
// ES6
console.log(Math.trunc(42.7)) // 42
console.log(Math.trunc( 0.1)) // 0
console.log(Math.trunc(-0.1)) // -0

// ES5
function mathTrunc (x) {
    return (x < 0 ? Math.ceil(x) : Math.floor(x));
}
console.log(mathTrunc(42.7)) // 42
console.log(mathTrunc( 0.1)) // 0
console.log(mathTrunc(-0.1)) // -0
```
Credits: [es6-features](http://es6-features.org/#NumberTruncation)

## Short syntax for Object Properties Initializer
Available from ES6, more at [moz://a](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)
```js
var obj = { x, y } // == { x: x, y: y }
```

## Short syntax for Method Definitions on Objects Initializers  
It is a shorthand for a function assigned to the method's name, starts with ECMAScript 2015, read more at [moz://a](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions)  
Before:
```js
var obj = {
  foo: function() {
    /* code */
  },
  bar: function() {
    /* code */
  }
};
```
In ECMAScript 2015:
```js
var obj = {
  foo() {
    /* code */
  },
  bar() {
    /* code */
  }
};
```
I found it while doing the tutorial app of [Meteor](https://www.meteor.com/tutorials/blaze/creating-an-app)

made with &#x2764; by [Steven](https://github.com/iamstevendao).

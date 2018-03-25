# Javascript Shortcuts
**Easy** and **short** syntaxes in Javascript which are **less common**, get updated whenever I see a new one.

## Table of Contents
- [Use + to convert String to Number](#use--to-convert-string-to-number)
- [Spread syntax (...)](#spread-syntax-)
- [Template literals (\` \`)](#template-literals--)
- [Number Truncation](#number-truncation)
- [Short syntax for Object Properties Initializer](#short-syntax-for-object-properties-initializer)
- [Short syntax for Method Definitions on Objects Initializers](#short-syntax-for-method-definitions-on-objects-initializers)
- [Self Executing Anonymous Functions](#self-executing-anonymous-functions)
- [Use Array Destructuring to swap variables values](#use-array-destructuring-to-swap-variables-values)
- [Bookmarked from airbnb]()

## Use + to convert String to Number
```js
+'3' === 3 // true
+'3' === Number(3) // true
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

## Self Executing Anonymous Functions
This is not very strange one, since we see a lot in the JQuery, AngularJS files...
```js
// create an anonymous function and call it straight away
(function(){
  console.log('Hello World!');
})();
// => Hello World!

// with parameters
(function(a){
  console.log(a === window); //Returns 'true'
})(window);
// pass 'window' as the parameter to call the anonymous function 
```
Check out [this blog](http://markdalgleish.com/2011/03/self-executing-anonymous-functions/) for more!

## Use Array Destructuring to swap variables values
This shorthand is a part of [Destructuring Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment), released in ES6
```js
let a = 1;
let b = 3;
let c = 5;

[a, b, c] = [b, c, a];
console.log(a); // 3
console.log(b); // 5
console.log(c); // 1
```
## Bookmarked from airbnb
- [3.8](#objects--rest-spread) Prefer the object spread operator over [`Object.assign`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) to shallow-copy objects. Use the object rest operator to get a new object with certain properties omitted.

  ```js
  // Use spread syntax to deep-copy, and to remove unwanted properties
  const original = { a: 1, b: 2 };
  const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }
  // _.emit() replacement
  const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
  ```
  
- [4.5](#arrays--mapping) Use [Array.from](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/from) instead of spread `...` for mapping over iterables, because it avoids creating an intermediate array.

  ```javascript
  // bad
  const baz = [...foo].map(bar);

  // good
  const baz = Array.from(foo, bar);
  ```

- [15.5](#comparison--switch-blocks) Use braces to create blocks in `case` and `default` clauses that contain lexical declarations (e.g. `let`, `const`, `function`, and `class`). eslint: [`no-case-declarations`](https://eslint.org/docs/rules/no-case-declarations.html)

  > Why? Lexical declarations are visible in the entire `switch` block but only get initialized when assigned, which only happens when its `case` is reached. This causes problems when multiple `case` clauses attempt to define the same thing.

  ```javascript
  // bad
  switch (foo) {
    case 1:
      let x = 1;
      break;
    case 2:
      const y = 2;
      break;
    case 3:
      function f() {
        // ...
      }
      break;
    default:
      class C {}
  }

  // good
  switch (foo) {
    case 1: {
      let x = 1;
      break;
    }
    case 2: {
      const y = 2;
      break;
    }
    case 3: {
      function f() {
        // ...
      }
      break;
    }
    case 4:
      bar();
      break;
    default: {
      class C {}
    }
  }
  ```
- [18.4](#comments--actionitems) Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are `FIXME: -- need to figure this out` or `TODO: -- need to implement`.

- [18.5](#comments--fixme) Use `// FIXME:` to annotate problems.

  ```javascript
  class Calculator extends Abacus {
    constructor() {
      super();

      // FIXME: shouldn’t use a global here
      total = 0;
    }
  }
  ```

- [18.6](#comments--todo) Use `// TODO:` to annotate solutions to problems.

  ```javascript
  class Calculator extends Abacus {
    constructor() {
      super();

      // TODO: total should be configurable by an options param
      this.total = 0;
    }
  }
  ```
  
- [22.2](#coercion--strings)  Strings: eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

  ```javascript
  // => this.reviewScore = 9;

  // bad
  const totalScore = new String(this.reviewScore); // typeof totalScore is "object" not "string"

  // bad
  const totalScore = this.reviewScore + ''; // invokes this.reviewScore.valueOf()

  // bad
  const totalScore = this.reviewScore.toString(); // isn’t guaranteed to return a string

  // good
  const totalScore = String(this.reviewScore);
  ```

## Useful methods
```js
export const camelCaseToLabel = function (camelCase) {
  // Capitalize a sentence in camel case: 'helloWorld' => 'Hello world'
  // Split words by the camel case
  const word = camelCase.replace(/([A-Z])/g, match => ` ${match.toLowerCase()}`);
  // Capitalize the first character
  return word[0].toUpperCase() + word.slice(1);
};
```

made with &#x2764; by [Steven](https://github.com/iamstevendao).

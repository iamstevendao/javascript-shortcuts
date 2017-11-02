# Javascript Shortcuts
Easy and short syntax in Javascript which are less common, get updated whenever I see a new one.

## Use + to convert String to Number
```js
+'3' === 3
+'3' === Number(3)
```
where I saw it: [learnyoumongo](https://github.com/evanlucas/learnyoumongo)

## Spread syntax (...)
Super powerful one with a fully detailed explanation at [Mozilla/Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

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
There's more at [Mozilla/Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

made with :heart: by [Steven](https://github.com/iamstevendao).
# Javascript Shortcuts
Neccessary and short syntax in Javascript which are less common, get updated whenever I see a new one.

## Use + to convert String to Number
```js
+'3' === 3
+'3' === Number(3)
```
where I saw it: [learnyoumongo](https://github.com/evanlucas/learnyoumongo)

## Spread syntax
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

made with :heart: by [Steven](https://github.com/iamstevendao).
# Currying

## Exercício 01

Crie uma função que substitua todas as vogais de um texto por "asterisco" usando currying.

Dica: ```str.replace(/[aeiou]/ig, '*');```


## Exercício 02

```
var _ = require('ramda');


// Exercise 1
//==============
// Refactor to remove all arguments by partially applying the function.

var words = function(str) {
  return _.split(' ', str);
};

// Exercise 1a
//==============
// Use map to make a new words fn that works on an array of strings.

var sentences = undefined;


// Exercise 2
//==============
// Refactor to remove all arguments by partially applying the functions.

var filterQs = function(xs) {
  return _.filter(function(x) {
    return match(/q/i, x);
  }, xs);
};


// Exercise 3
//==============
// Use the helper function _keepHighest to refactor max to not reference any
// arguments.

// LEAVE BE:
var _keepHighest = function(x, y) {
  return x >= y ? x : y;
};

// REFACTOR THIS ONE:
var max = function(xs) {
  return _.reduce(function(acc, x) {
    return _keepHighest(acc, x);
  }, -Infinity, xs);
};


// Bonus 1:
// ============
// Wrap array's slice to be functional and curried.
// //[1, 2, 3].slice(0, 2)
var slice = undefined;


// Bonus 2:
// ============
// Use slice to define a function "take" that takes n elements from the beginning of the string. Make it curried.
// // Result for "Something" with n=4 should be "Some"
var take = undefined;
```
# Composing

## Exercício

```js
<!-- <script src="https://cdnjs.cloudflare.com/ajax/libs/ramda/0.22.1/ramda.min.js"></script> -->
<!-- <script src="https://raw.githubusercontent.com/openexchangerates/accounting.js/master/accounting.min.js"></script> -->

var R = require('ramda'); <!-- nodejs -->
var accounting = require('accounting'); <!-- nodejs -->

// Example Data
var CARS = [{
  name: 'Ferrari FF',
  horsepower: 660,
  dollar_value: 700000,
  in_stock: true,
}, {
  name: 'Spyker C12 Zagato',
  horsepower: 650,
  dollar_value: 648000,
  in_stock: false,
}, {
  name: 'Jaguar XKR-S',
  horsepower: 550,
  dollar_value: 132000,
  in_stock: false,
}, {
  name: 'Audi R8',
  horsepower: 525,
  dollar_value: 114200,
  in_stock: false,
}, {
  name: 'Aston Martin One-77',
  horsepower: 750,
  dollar_value: 1850000,
  in_stock: true,
}, {
  name: 'Pagani Huayra',
  horsepower: 700,
  dollar_value: 1300000,
  in_stock: false,
}];

// Exercise 1:
// ============
// Use R.compose() to rewrite the function below. Hint: R.prop() is curried.
var isLastInStock = function(cars) {
  var last_car = R.last(cars);
  return R.prop('in_stock', last_car);
};

// Exercise 2:
// ============
// Use R.compose(), R.prop() and R.head() to retrieve the name of the first car.
var nameOfFirstCar = undefined;


// Exercise 3:
// ============
// Use the helper function _average to refactor averageDollarValue as a composition.
var _average = function(xs) {
  return R.reduce(R.add, 0, xs) / xs.length;
}; // <- leave be

var averageDollarValue = function(cars) {
  var dollar_values = R.map(function(c) {
    return c.dollar_value;
  }, cars);
  return _average(dollar_values);
};


// Exercise 4:
// ============
// Write a function: sanitizeNames() using compose that returns a list of lowercase and underscored car's names: e.g: sanitizeNames([{name: 'Ferrari FF', horsepower: 660, dollar_value: 700000, in_stock: true}]) //=> ['ferrari_ff'].

var _underscore = R.replace(/\W+/g, '_'); //<-- leave this alone and use to sanitize

var sanitizeNames = undefined;


// Bonus 1:
// ============
// Refactor availablePrices with compose.

var formatNumber = function(numero) {
  return '$ ' + new Intl.NumberFormat().format(numero);
};

var availablePrices = function(cars) {
  var available_cars = R.filter(R.prop('in_stock'), cars);
  return available_cars.map(function(x) {
    return formatNumber(x.dollar_value);
  }).join(', ');
};


// Bonus 2:
// ============
// Refactor to pointfree. Hint: you can use _.flip().

var fastestCar = function(cars) {
  var sorted = R.sortBy(function(car) {
    return car.horsepower;
  }, cars);
  var fastest = R.last(sorted);
  return fastest.name + ' is the fastest';
};
```
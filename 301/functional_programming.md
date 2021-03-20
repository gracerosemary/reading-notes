## [Concepts of Functional Programming in Javascript](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)  

> What is functional programming?
Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — Wikipedia

### Pure functions  

- deterministic: same results are returned if it's given the same arguments
    - no external or global objects passed in
    - no altering the value of variables → always returns the same results
- does not cause observable side effects
    - mutability is discouraged in functional programming
    - ex: modifying a global object or a parameter passed by reference
- functions are isolated and unable to impact other parts of the system
- stable, consistent, predictable → easier to test

> Given a parameter A → expect the function to return value B
Given a parameter C → expect the function to return value D

### Impure functions

- uses objects that are not passed as a parameter to the function (ex. global objects being passed into a function)
- functions that read external files → file's contents can change
- functions that rely on random number generator

### Immutability

> Unchanging over time or unable to be changed.

- state of the data cannot change after it's created
- need to create a new object with a new value if you want to change an immutable object
- recursion: handle mutability in iterations
    - keeps variables immutable

### Referential transparency

> pure functions + immutable data = referential transparency

- referentially transparent: function produces same result for the same input
- memoize: optimization technique to speed up programs by storing results of function calls and returning cached results for same inputs

    ```jsx
    const sum = (a, b) => a + b;
    // call it with these parameters
    sum(3, sum(5, 8));
    // sum(5, 8) equals 13 and function will always result in 13 so we can memoize:
    sum(3, 13);
    ```

### Functions as first-class entities

- functions are treated as values AND used as data
    - can combine different functions to create new functions with new behavior
- able to refer to it from constants and variables
- can pass it as a parameter to other functions
- can be returned as a result from other functions

```jsx
const sum = (a, b) => a + b;
const subtraction = (a, b) => a - b;

// f argurment to process a & b
const doubleOperator = (f, a, b) => f(a, b) * 2;

// pass sum & subtraction functions & create new behavior
doubleOperator(sum, 3, 1); // 8
doubleOperator(subtraction, 3, 1); // 4
```

### Higher-order functions

- functions that either:
    - takes one or more functions as arguments
    - returns a function as its result
    - ex: code above ^ takes an operator function as an argument and uses it

### Reduce

- receives a function and a collection
- returns a value created by combining the items

```jsx
let shoppingCart = [
  { productTitle: "Product 1", amount: 10 },
  { productTitle: "Product 2", amount: 30 },
  { productTitle: "Product 3", amount: 20 },
  { productTitle: "Product 4", amount: 60 }
];

const sumAmount = (currentTotalAmount, order) => currentTotalAmount + order.amount;

// function to handle the amount sum and pass it as an argument to the reduce function
const getTotalAmount = (shoppingCart) => shoppingCart.reduce(sumAmount, 0);

getTotalAmount(shoppingCart); // 120
```

```jsx
const getAmount = (order) => order.amount;
const sumAmount = (acc, amount) => acc + amount;

// use map to transform the shoppingCart into a collection of amount values
// use reduce function with sumAmount function
function getTotalAmount(shoppingCart) {
  return shoppingCart
    .map(getAmount)
    .reduce(sumAmount, 0);
}

getTotalAmount(shoppingCart); // 120
```

## [Refactoring JavaScript for Performance and Readability](https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec)  

- throw an error so that problems can be spotted
- hash function: used to map a given key to a location in the hash table
    - uses Maps an Sets under the surface
- separate some logic and reduce the lines of code

### Strategies

Return early from functions:

```jsx
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}

// Refactor into ->

function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}
```

Cache variables so functions can be read like sentences:

```jsx
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    for (let j = 0; j < continents[i].length; j++) {
      for (let k = 0; k < continents[i][j].tags.length; k++) {
        if (continents[i][j].tags[k] === name) {
          return continents[i][j].id;
        }
      }
    }
  }
}

// Refactor into ->

function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    const group = continents[i]; // This code becomes self-documenting
    for (let j = 0; j < group.length; j++) {
      const tags = group[j].tags;
      for (let k = 0; k < tags.length; k++) {
        if (tags[k] === name) {
          return group[j].id; // The core of this nasty loop is clearer to read
        }
      }
    }
  }
}
```

Check for Web APIs before implementing your own functionality:

```jsx
function cacheBust(url) {
  return url.includes('?') === true ?
    `${url}&time=${Date.now()}` :
    `${url}?time=${Date.now()}`
}

// Refactor into ->

function cacheBust(url) {
  // This throws an error on invalid URL which stops undefined behaviour
  const urlObj = new URL(url);
  urlObj.searchParams.append('time', Date.now); // Easier to skim read
  return url.toString();
}
```
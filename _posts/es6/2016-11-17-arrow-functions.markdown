---
layout: post
title:  "Arrow Functions"
date:   2016-11-17 18:45:15
categories: es6
---
Benefits for using Arrow Functions:

1. More concise than regular functions
2. implicit returns (one liner functions)
3. does not rebind the value of 'this' (will return window instead)
4. Works well in callback situations


```javascript
const foods = ['coffee', 'oatmeal', 'fruit'];

// Note: map() - takes in an array, runs a function on each item and outputs a new array
// Non-Arrow Function syntax
const breakfast = foods.map(function(food) {
  return `I had ${food} for breakfast`;
});
// Arrow function syntax
const breakfast = foods.map((food) => `I had ${food} for breakfast`);

// Simple example on Arrow function
const sayMyName = (name) => {
  alert(`Hello ${name}!`)
}

sayMyName('Matt');
```

When not to use arrow functions:

```javascript
// When you really need `this`
const button = document.querySelector('#pushy');
button.addEventListener('click', function() {
  console.log(this); // this binds to button NOT window
  this.classList.toggle('on');
});
// When you need a method to bind to an object
const person = {
  points: 23,
  score() {
    console.log(this);
    this.points++;
  }
}
// When you need to add a prototype method
class Car {
  constructor(make, colour) {
    this.make = make;
    this.colour = colour;
  }
}

```

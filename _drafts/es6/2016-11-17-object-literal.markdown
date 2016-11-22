---
layout: post
title:  "Object Literals"
date:   2016-11-17 18:51:20  
categories: es6
---

```javascript
// When inserting vars into an object
const make = 'VW';
const model = 'Golf';
const year = 2016;

const car = {
  // you can still use this syntax:
  name: make,
  // New in ES6: when same var name used for prop
  // use this shorter syntax: (instead of model:model)
  model,
  year,
  // adding an array
  similar: ['Hugo', 'Mini']
};

  console.log(car);

// Methods inside of an object
const modal = {
  create() {
    // use this syntax in ES6
  },
  open: function() {
    // instead of this.
  }
}
```

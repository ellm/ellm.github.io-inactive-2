---
layout: post
title:  "Destructuring"
date:   2016-11-17 18:47:53
categories: es6
---

## Destructuring
- good for deeply nested data (API)

```javascript
const matt = {
  first: 'Matt',
  last: 'Ell',
  links: {
    twitter: 'matthewell',
    web: 'matthewell.com'
  }
}
// Destructing Example 1: Makes variables available from object
const {twitter, web} = matt.links;
// > twitter
// < matthewell

// Destructing Example 2: Makes renamed variables available from object
const {twitter: mytwitter, web: myweb} = matt.links;
// > myweb
// < matthewell.com

// Destructing Example 3: Destructure Window Object
//
// const {innerHeight, innerWidth } = window;
// console.log(innerHeight, innerWidth);

// Destructure Window Object and assign to new const
//
const {innerHeight: height, innerWidth: width } = window;
console.log(height, width);

// Destructing Example 4: Swapping values
let inRing = 'Hulk Hogan';
let onSide = 'The Rock';

console.log(inRing, onSide);
[inRing, onSide] = [onSide, inRing];
console.log(inRing, onSide);
```

---
layout: page
title: JavaScript
permalink: /notes/javascript
---

### Videos
[Philip Roberts: What the heck is the event loop anyway? | JSConf EU 2014](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

### Async

- `Async` tags load the scripts while the rest of the page loads, but this means scripts can be loaded out of order. Basically, lighter files load first. This might be fine for some scripts, but can be disastrous for others.

- The `defer` attribute loads your scripts after your content has finished loading. It also runs the scripts in order. Just make sure your scripts run so late without breaking your site.

Ref:
- https://www.html5rocks.com/en/tutorials/speed/script-loading/
- http://www.aaronpeters.nl/blog/why-loading-third-party-scripts-async-is-not-good-enough

### Rules for writing functions

* See: https://rainsoft.io/the-art-of-writing-small-and-plain-functions/

* As a general rule, your functions should not be longer than 20 lines of code. Smaller - better.

* Because functions are actions, the name should contain at least one verb. For example deletePage(), verifyCredentials(). To get or set a property, use the standard set and get prefixes: getLastName() or setLastName().

* ES2015 implements a nice module system, that clearly suggest that small functions are a good practice.


### OOP Design Pattern

``` javascript
myJsObject.init();
var myJsObject = {
    init: function () {
        // add things todo on init
    }
};
```

### Sequentially Loop through Elements And Apply A Class

``` javascript
(function(){
    var myEles = document.querySelectorAll(".myEle"), i = 1;
    Array.prototype.forEach.call(myEles, function(myEle) {
        setTimeout(function(){ myEle.classList.add("visible") }, 700*i)
        i++;
    })
})();
```


### Looping through iterables

``` javascript
// forOf
for (variable of iterable) {
  // works in IE Edge +
}
// forEach loop
Array.prototype.forEach.call(iterable, (variable) => {
  // works in IE11+
});
```



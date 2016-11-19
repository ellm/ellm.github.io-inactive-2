---
layout: page
title: JavaScript
permalink: /notes/javascript
---

### Videos
[Philip Roberts: What the heck is the event loop anyway? | JSConf EU 2014](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

### stopPropagation()

prevent event bubbling up to parent element.
```html
<a href="#" class="parent">
  <a href="#" class="child">Child</a>
</a>
```

```javascript
// Parent
$('.parent').click(e) {
  e.preventDefault();
}
// Child
$('.child').click(e) {
  // stopPropagation() will not allow event to bubble up to run preventDefault()
  e.stopPropagation();
}
```

### Async

- `Async` tags load the scripts while the rest of the page loads, but this means scripts can be loaded out of order. Basically, lighter files load first. This might be fine for some scripts, but can be disastrous for others.

- The `defer` attribute loads your scripts after your content has finished loading. It also runs the scripts in order. Just make sure your scripts run so late without breaking your site.

Ref:
- https://www.html5rocks.com/en/tutorials/speed/script-loading/
- http://www.aaronpeters.nl/blog/why-loading-third-party-scripts-async-is-not-good-enough

### DOM

_Getting Info_

``` javascript
// inspect the type of object or primitive
typeof undefined === 'undefined';

```

_Selecting Nodes_

``` javascript
// I want to know the amount of nodes
console.log(parentElment.children.length);
// I want to select a specific child node
console.log(parentElment.childNodes.item(1));
// I want to select a specific child node
console.log(parentElment.querySelector('*:nth-child(2)'));
```

### Rules for writing functions

* See: https://rainsoft.io/the-art-of-writing-small-and-plain-functions/

* As a general rule, your functions should not be longer than 20 lines of code. Smaller - better.

* Because functions are actions, the name should contain at least one verb. For example deletePage(), verifyCredentials(). To get or set a property, use the standard set and get prefixes: getLastName() or setLastName().

* ES2015 implements a nice module system, that clearly suggest that small functions are a good practice.

### How to fire a script after page load

Today I came across a situation where my script to resize the height of an element was firing too early. I essentially needed a way to make sure the script did not execute until all elements on the page were loaded and would then calculate the height of my targeted element.

So, I found :
``` javascript
$(window).load(function(){
// Scripts here
});
```

Different from the more popular `$(document).ready()` where scripts fire when the DOM is "ready". The `$(window).load()` event is fired as soon as the window DOM element and all it's containing elements have been loaded. Including all objects like images, scripts and iframes.

It can be included anywhere in your script and it will not fire until after all containing elements have been completely loaded.

One caveat with the containing script is it can be VERY obvious that the script loads after everything else and the load can look a bit sloppy. This is a very minor detail.

### How to attach events to dynamic html elements / Event binding on dynamically created elements

``` javascript
$('body').on('click', 'a.myclass', function() {
    // do something
});
```

The body tag is used here as the example had no closer static surrounding tag, but any parent tag that exists when the .on method call occurs will work. http://stackoverflow.com/questions/1359018/in-jquery-how-to-attach-events-to-dynamic-html-elements

### Open a link in a new window using JS

``` javascript
$('#foo').click(function (event) {
    event.preventDefault();
    window.open(url, '_blank'); // will prevent Google Chome popup error
});
```

### Fire a click event only one time

``` javascript
$( "#foo" ).one( "click", function() {
  alert( "This will be displayed only once." );
});
```

### Fire scripts after page load

``` javascript
$(window).load(function(){
// Scripts here
});
```

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

### Execute JS only on Specific Page

```javascript
// Look for body class
$(function(){
  if($('body').is('.PageType')){
    //add dynamic script tag  using createElement()
    OR
    //call specific functions
  }
});

// OR

// Check Element Length
if ( $( "#myDiv" ).length ) {
    // Act on
}
```

### Link Directly to jQuery UI Accordion Panel from External Page

Problem: You need to link directly to a accordion pane (Page B) from a link that on a separate page (Page A). When the Page B loads, the accordion pane should open and appear at the top of the page. Let's see how this can be done. **Step 1:** On Page A you have a link that takes the following form (assuming we are using PHP):

```html
<href="http://www.example.com/sample.php?id=1#ui-id-1">Link to External Accordion</a>;
```

There is a lot going on in this link. Here is the breakdown: ``?id=1`` is going to be sent to Page B through the [HTTP Request Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers). We will use the PHP reserved variable [$_GET](http://php.net/manual/en/reserved.variables.get.php) to retrieve the value `id` on Page B which will open the corresponding accordion panel. ``#ui-id-1`` will be passed as the [Fragment Identifier](http://en.wikipedia.org/wiki/Fragment_identifier). This will find the element on the page with the corresponding id (example: `<h3 id="ui-id-1">`) and jump down to that element. **Step 2:** On Page B you will have your [jQuery UI accordion](https://jqueryui.com/accordion/). This should needs to be initialized:

```javascript
$( ".accordion" ).accordion( {
collapsible: true, //Whether all the sections can be closed at once. Allows collapsing the active section.
heightStyle: "content" // Allows accordion to keep their native height
});

```

**Step 3:** Finally, we need the code that will find the desired accordion panel, jump down to it and then open it! Here is how it is done:

```php
<?php if ( isset( $_GET['id'] ) && !empty( $_GET['id'] ) ): ?>
```

``` javascript
jQuery(document).ready(function($) {
$( ".contact-accordion" ).accordion({active: });
}); //jQuery
```

The code is pretty simple. First, we check to make sure that we are coming from Page A by testing to see if the `$_GET['id']` has a value and is not empty. If it is not, we load a script to set the active property in the accordion to the ID. In our example, we will get a value of "1". Remember that the jQuery UI accordion uses index values so the first panel will be "0". Do you have suggestions on my code or perhaps, a better way? I'd like to hear your thoughts!

### Fire a script after user is n% down the page

``` javascript

/**
 * Throttler
 * Primarily used to execute functions over set
 * intervals of time.
 *
 * @param callback
 * @param wait
 * @returns {Function}
 */
function hsThrottle( callback, wait ) {
    var time, go = true;
    return function() {
        if ( go ) {
            go = false;
            time = setTimeout( function() {
                time = null;
                go = true;
                callback.call();
            }, wait );
        }
    }
}

// Open Overlay after reaching 25% of page
// Use a slight throttle for performance
var fbScrollHandler = hsThrottle( function() {
    // "this" is window object
    var currY = $( this ).scrollTop(); // cache current vertical (y) position
    var postHeight = $( this ).height(); // cache window height
    var scrollHeight = $( '.wrap' ).height(); // cache page wrapper height (if it does not take up the entire height page.)
    // percentage calculate y position percentage
    var scrollPercent = ( currY / ( scrollHeight - postHeight ) ) * 100;

    // Fire modal when scroll percentage is at 25%
    if ( scrollPercent >= 25 ) {
        // fire script
    }
}, 50 );

// fire throttle function on user scroll
$( window ).on( 'scroll', fbScrollHandler );

```

### Check if a value is undefined

```javascript
if ( typeof foo === "undefined" ) {
    // foo is undefined.
    // foo var exists and it's undefined

}

```

Note: Contrary to common belief, "undefined" is NOT a keyword in JavaScript and can in fact have a value assigned to it.

### Check if a variable has a truthy value

``` javascript
if ( value ) {
// will evaluate to true if:
    // null
    // undefined
    // NaN
    // empty string ("")
    // 0
    // false
}
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

### Check For Rendered Facebook Like Button

```javascript
var fbButtonRendered = function() {
  return $( '.fb-like' ).is( '[fb-xfbml-state="rendered"]' );
}
```

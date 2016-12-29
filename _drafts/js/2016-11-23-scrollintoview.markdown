---
layout: post
title:  "scrollIntoView()"
date:   2016-11-23 17:12:30
categories: js
---

`scrollIntoView()` will jump to an `id` on the page and has very good _basic_ [browser support](https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView). 

It works like this:

```javascript
ele = document.getElementById('id');
ele.scrollIntoView();
```

Other methods of accomplishing this include:

```javascript
// This method will alter the URL. Not so great...
ele = document.getElementById('id');
window.location.hash = ele;

// This method requires jQuery
ele = document.getElementById('id');
$(document.body).animate({
    'scrollTop': $(ele).offset().top
}, 2000);
```

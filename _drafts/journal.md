---
layout: page
title: Journal
permalink: /notes/journal
---

# Journal

## 2016-12-29

CSS variables are define as `--myVar: #fff;`. CSS variables are used on different properties: `var(--myVar)`.

Set a fallback for JS variables by doing:

```javascript
const myVar = document.querySelector('div') || '';
// will fallback to an empty string if div does not exist. 
```

- Good for taking control of variable values
- avoiding `undefined` errors

---

## 2016-12-28

Use `setInterval` to run a function automatically for a set amount of time. 

```javascript
setInterval(myFunc, 1000); // run myFunc every 1 second
```

---

## 2016-12-27

Breaking out of functions early using `return`. When a value returns null or you are looking to only return something specific, set up a `if` statement to catch it early. 

```javascript
listenerCallbackExample () {
    const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
    if (! audio) return; // stop function from running any further.
    // if 'audio' returns null we want to stop the function from running any further. 
}
```
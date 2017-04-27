---
layout: post
title:  "iOS Browser Bugs"
date:   2017-04-25
categories: bugs
---

You will likely find these bugs in both Safari and Chrome because iOS Chrome is forced to use Apple’s WebView. However, some of these bugs may only occur in one of the two.

## Flexbox percentage height bug

Given the following markup:

```html 
<div class="flex-container">
  <div class="flex-child"></div>
  <div class="flex-child"></div>
  <div class="flex-child"></div>
</div>
```

`.flex-child` appears collapsed when using percentage based `height` and `.flex-container` has it's `flex-direction` set to `column`.

For the time being, my work around is to set `flex-container` to not use `flex-direction` and instead use `flex-wrap: wrap`. Additionally, setting `flex-child` to have 100% `width`. These two changes give you a similar effect and work across browsers and devices. 

[Demo](https://codepen.io/ellm/pen/vmgGPE)

I've also submitted this bug to [flexbugs](https://github.com/philipwalton/flexbugs/issues/217) for discussion.

## `position:fixed` bug

On iOS using the CSS `postition:fixed` on a container such as a modal pop-up creates some strange results when an input field is within it.

Creating the bug goes as follows:

1. Tap inside the text field within a fixed container.
2. The native IOS keyboard slides up on screen and simultaneously the body text scrolls.

This scrolling can be undesirable, especially on article pages where a user is likely to be moved away from their current reading position. [Stackoverflow](http://stackoverflow.com/questions/39626302/ios-chrome-safari-unwanted-scrolling-when-focusing-an-input-inside-the-modal/40033422#40033422) has a detailed write up on this bug as well as a patch that seems to do the trick. Essentially, the work around is to capture the users scroll position and return them to that point after form submission.

## Prevent a page from scrolling

Toggle a class with `overflow: hidden`. This will work for most browsers but not IOS. 

```css
html.modal-active,
body.modal-active {
    overflow: hidden;
}
```

For IOS, some javascript is needed to prevent scrolling on a touch screen. The technique used in this [blog post](https://benfrain.com/preventing-body-scroll-for-modals-in-ios/) seems to do the trick nicely by preventing body scroll on the `touchmove` event.

## `click` event does not fire

If you add a `click` event to a non-form element (i.e. `<div>, <span>`), iOS does not register the event. This is not the case with elements such as `<button>`. This bug is mainly due to event bubbling as described in [this quirksmode article](https://www.quirksmode.org/blog/archives/2014/02/mouse_event_bub.html). Surprisingly, the fix is not using JS but using CSS.

```css
div {
    cursor: pointer 
}
```

Adding `cursor: pointer` to the non-form element gives the browser just the information it needs to fix the issue. 

## Use JS to detect an iOS device

Not really a bug but helpful in fixing oddities in iOS 

```javascript
if (/iPad|iPhone|iPod/.test(navigator.userAgent) && !window.MSStream) {
    // scripts will only apply to devices with iOS user agent.
    // Note: desktop browsers can still fake their user agent
}
```
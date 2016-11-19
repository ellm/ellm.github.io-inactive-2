---
layout: page
title: Internet Explorer Hell
permalink: /notes/ie-hell
---

Printing IE 11

When trying to print in IE11, modern CSS may crash the browser. I was not able to identify the exact styles that causes the issue however, the following fixed it:

- make sure to add `media="screen"` to styles all that that apply to being viewed on screen
    + `<link rel="stylesheet" type="text/css" media="screen" href="#">`
    + `@media screen{...}`
- makes sure to add `media="print"` to styles that are for print
    + `<link rel="stylesheet" type="text/css" media="print" href="#">`
    + `@media print{...}`

- using the keyword `only` such as `only screen` or `only print` will ensure that styles will not be always loaded and uses the media query.
- Make sure that the `print` and `screen` styles are loaded separately.
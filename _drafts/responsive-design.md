---
layout: page
title: Responsive Web Design
permalink: /notes/rwd
---

# Responsive Images

## srcset

Format is as follows:

``` html
<img src="small.jpg" srcset="small.jpg 400w, medium.jpg 768w, large.jpg 1024w" alt="Responsive Image" />
```

*   Note sizes are ordered smallest to largest.
*   small.jpg will be loaded if `srcset` is not supported.
*   400w, 768w, etc. should represent the width of the image. This number is used by the browser to determine which image to load.

**Support:**

*   Currently, not supported by IE, Opera and older Android browsers (http://caniuse.com/#search=srcset)
*   Use PictureFill (https://github.com/scottjehl/picturefill) for better browser support

**How it works:**

*   Browser automatically detects the correct image size to load in.

**Links:**

*   https://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/
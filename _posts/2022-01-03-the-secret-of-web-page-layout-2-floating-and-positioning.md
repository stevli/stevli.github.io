---
layout: post
title: "The Secret of Web Page Layout (2): Floating and Positioning"
---

The Secret of Web Page Layout (2): Floating and Positioning
===

Through the `display` attribute introduced in the previous article, we can already complete the layout of the web page. For a specific element, we can still continue to adjust the display position of the element through the `float` and `position` attributes.

## Floating

Floating means placing a specific element at the left or right of the container, while all other elements continue to be arranged in the remaining space according to the container's layout settings. We can use the `float` attribute to set whether an element is floating.

- `float: left;` Float the element to the left.
- `float: right;` Float the element to the Right.
- `float: none;` (Default value) The element does not float.

## Positioning

Use the `position` attribute to set the position of an element more flexibly.

- `position: static;` (Default value) The element is displayed in its normal position.
- `position: absolute;` The element is displayed exactly at the position defined by `left` and `top`.
- `position: fixed;` The element is displayed exactly at the position defined by `left` and `top` based on the browser viewport. So when we scroll the page, the element doesn't scroll with it.
- `position: sticky;` Element is displayed in its normal position. When it scrolls up to the position defined by `left` and `top` based on the browser viewport, it stops and doesn't continue to move. When we scroll down the page back to its original position, it will resume scrolling with the page.
- `position: relative;` The element still occupies the position where it should be displayed, but the actual displayed position is slightly offset according to `left` and `top`.

Except the default static positioning, the `position` attribute needs to work with the `left` and `top` attributes For example:

```
.menu {
  position: fixed;
  top: 50px;
  left: 10px;
}
```

The above css code can fix the element in the upper left corner of the browser without moving or disappearing as we scroll the page.

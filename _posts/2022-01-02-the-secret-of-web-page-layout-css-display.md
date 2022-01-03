---
layout: post
title: "The Secret of Web Page Layout: css::display"
---

The Secret of Web Page Layout: css::display
===

The browser displays a web page very much like a page in a book. The content is divided into paragraphs, and the words in each paragraph is arranged from left to right. When one line is full, it will automatically switch to the next line. In web page design, this default web page layout is called **normal flow**.

## Normal Flow

The browser divides various elements into two categories through the **display** property of CSS. The display attribute of elements such as `<div>`, `<h1>` is set to `block` by default; the display attribute of other elements such as `<a>`, `<span>` is set to `inline` by default.

- `display: none` Don't show this element.
- `display: block` This element is displayed on a new line (like a paragraph).
- `display: inline` Continuing the previous element, this element is displayed on the same line (like a word).
- `display: inline-block` We can change the display size of the block elements by setting the `width` and `height` attributes. But this is not possible for inline elements, their display size is automatically calculated by the browser. The use of the combination, `display: inline-block`, can continue to display the elements as inline elements and set their size at the same time.


---
layout: post
title: "The Secret of Web Page Layout: display Attribute of CSS"
---

The Secret of Web Page Layout: display Attribute of CSS
===

The browser displays a web page very much like a page in a book. The content is divided into paragraphs, and the words in each paragraph is arranged from left to right. When one line is full, it will automatically switch to the next line. In web page design, this display layout is called **normal flow**.

## Normal Flow

The browser divides various elements into two categories through the **display** attribute of CSS. The display type of elements such as `<div>`, `<h1>` is set to `block` by default; the display type of other elements such as `<a>`, `<span>` is set to `inline` by default.

We can manually modify the display type of any element.

- `display: none` Don't show this element.
- `display: block` This element is displayed on a new line (like a paragraph).
- `display: inline` Continuing the previous element, this element is displayed on the same line (like a word).

We can change the display size of the block elements by setting the `width` and `height` attributes. But this is not possible for inline elements, their display size is automatically calculated by the browser. The use of the combination, `display: inline-block`, can continue to display the elements as inline elements and set their size at the same time.

## display Attribute of Container Elements

HTML uses a language structure that can be nested. In other words, some elements such as `<div>`, `<p>` can be used as containers for other elements.

The default display layout within these container elements is also **normal flow**. We can manually set the inner display layout of these container elements. These layout types are inherited from the `block` type. That is to say, as the element itself, these container elements are displayed as block elements.

## Table Layout

The earliest container display layout is `table`. The element itself is displayed as a block element, and the elements inside it are displayed as a table composed of rows and columns.

- `display: table` As a container element, internal elements of this element will be displayed in table format.
- `display: table-caption` This element is displayed as the table header.
- `display: table-row` This element is displayed as a table row.
- `display: table-column` This element is displayed as a table column.
- `display: table-cell` This element is displayed as a table cell.

There are two things to note here. First of all, the table layout is considered an outdated layout, and its functions can be replaced by the grid layout described below; secondly, HTML defines a set of elements, which are set by default for these display types, so we can directly use them to compose a table layout. For example:

- `table { display: table }`
- `caption { display: table-caption }`
- `tr { display: table-row }`
- `th { display: table-cell; font-weight: bold; }` Usually used as a column cell, displayed in bold font
- `td { display: table-cell }` Usually used as a data cell

## Grid Layout

The more flexible container display layout is `grid`, which has basically replaced `table` now. A grid element is also made up of rows and columns. When we define the internal layout of a container as `grid`, we can also define the number and size of rows and columns, for example:

```
.container {
    display: grid;
    grid-template-columns: 2fr repeat(2, 1fr);
    grid-template-rows: 100px auto;
    grid-gap: 10px;
}
```

The css code above defines a grid class, where the `grid-template-columns` and `grid-template-rows` define three columns and two rows, respectively. The size of each column or row can be fractional (`2fr`), size (`100px`) or automatic (`auto`), and `repeat` can be used to define several rows or columns of the same size.

All elements inside this container will be arranged from left to right in the first row, and the second row will be arranged after the first row is full. But we can also specify an element to be placed at a specified position, for example:

```
.cell_1 {
    grid-row: 1;
    grid-column: 2;
}
.cell_2 {
    grid-row: 2;
    grid-column: 2 / 3;
}
```

In this way, the element of class `cell_1` will be placed in the first row and second column, and element of class `cell_2` will occupy both the second and third columns of the second row.

## Flex Layout

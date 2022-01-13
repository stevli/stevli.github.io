---
layout: post
title: "The Secret of Web Page Layout (1): display Attribute of CSS"
---

The Secret of Web Page Layout (1): display Attribute of CSS
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

All elements inside this container will be arranged from left to right in the first row, and the second row will be arranged after the first row is full. The flexibility of `grid` is that we can easily place an element at any specified position, just like:

```
.cell-1 {
    grid-row: 1;
    grid-column: 2;
}
.cell-2 {
    grid-row: 2;
    grid-column: 2 / 3;
}
```

In this way, the element of class `cell-1` will be placed in the first row and second column, and element of class `cell-2` will occupy both the second and third columns of the second row.

## Flex Layout

The latest layout is `flex` which can be understood as a grid layout without setting an explicit number of rows and columns. By default, all elements in the flex container are arranged sequentially from left to right. If we enable the wrap attribute (default is nowrap), the elements are automatically arranged in the second row after the first row is filled.

We set a container to use flex layout by setting `display: flex` and adjust the arrangement of elements inside the container by setting the attributes like `flex-direction` and `flex-wrap`. For example:

```
.flex-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: stretch;
}
```

The above css code can set a block element as a flex container, and set the direction of the elements to be arranged in rows, after the first row is full, it will be automatically arranged in a new row. At the same time, the elements in each row will be stretched to fill the space of the whole column.

#### flex-direction

- `flex-direction: row;` (Default value) Set the elements to be arranged in row, and in the same direction as the text direction (left to right in most cases).
- `flex-direction: row-reverse;` Set the elements to be arranged in row, and in the **opposite** direction as the text direction.
- `flex-direction: column;` Set the elements to be arranged in column, and in the same direction as the writing mode. (top to bottom in most cases).
- `flex-direction: column-reverse;` Set the elements to be arranged in column, and in the **opposite** direction as the writing mode.

#### flex-wrap

- `flex-wrap: nowrap;` (Default value) All elements are arranged in one line, even if they overflow the width of the container.
- `flex-wrap: wrap;` When the first row is full, the elements will be automatically arranged in the second row.

#### align-items

- `align-items: stretch;` (Default value) Elements in the vertical direction are stretched to fill the container. If the container is arranged in row, the vertical direction means column, and vice versa.
- `align-items: center;` All elements in the vertical direction are center-aligned.
- `align-items: start;` All elements in the vertical direction are arranged according to the arrangement of the container.
- `align-items: end;` All elements in the vertical direction are arranged in the opposite direction of the container arrangement.

For each element inside the flex container, we can resize it by setting the `flex` attribute. For example:

```
.flex-element {
    flex: 2 100px;
}
```

The above css code can set an element to occupy twice the width of a normal element while maintaining a basic width of `100px`.

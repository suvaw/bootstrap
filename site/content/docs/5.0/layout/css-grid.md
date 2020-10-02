---
layout: docs
title: CSS Grid
description: Learn how to enable, use, and customize our alternate layout system built on CSS Grid with examples and code snippets.
group: layout
toc: true
---

## Overview

Bootstrap's default grid system represents the culmination of over a decade of CSS layout techniques, tried and tested by millions of people. But, it was also created without so many of the modern CSS features and techniques that we're seeing in browsers—features like the new CSS Grid.

With Bootstrap 5, we've added the option to enable a separate grid system that's built on CSS Grid, but with a Bootstrap twist. You still get classes you can apply on a whim to build responsive layouts, but with a different approach under the hood.

## How it works

- Disable the default grid system by setting `$enable-grid-classes: false`.
- Enable the CSS Grid by setting `$enable-cssgrid: true` and recompiling your Sass.
- Replace instances of `.row` with `.grid`. `.grid`s set `display: grid` and create a `grid-template` that you build on with your HTML.
- The number of columns and the width of the gutters are set via CSS variables on the `.grid`, which means you can customize those values on the fly: `--columns` and `--gutter`.

## Examples

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-4">.g-col-4</div>
  <div class="g-col-4">.g-col-4</div>
  <div class="g-col-4">.g-col-4</div>
</div>
{{< /example >}}

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
  <div class="g-col-1">.g-col-1</div>
</div>
{{< /example >}}

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
</div>
{{< /example >}}

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-3">.g-col-3</div>
  <div class="g-col-3">.g-col-3</div>
  <div class="g-col-3">.g-col-3</div>
  <div class="g-col-3">.g-col-3</div>
</div>
{{< /example >}}

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-4">.g-col-4</div>
  <div class="g-col-4">.g-col-4</div>
  <div class="g-col-4">.g-col-4</div>
</div>
{{< /example >}}

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-6">.g-col-6</div>
  <div class="g-col-6">.g-col-6</div>
</div>
{{< /example >}}

## Starts

Start classes replace our default grid's offsets, but they're not the same. CSS Grid creates columns through styles that tell browsers to "start at this column" and "end at this column." Those properties are `grid-column-start` and `grid-column-end`. Start classes are shorthand for the former.

By comparison, our default grid's offsets use `margin-left` to nudge a column.

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-3 g-start-2">.g-col-3 .g-start-2</div>
  <div class="g-col-4 g-start-6">.g-col-4 .g-start-6</div>
</div>
{{< /example >}}

## Auto columns

Any immediate child of `.grid` will automatically be sized to one column.

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
</div>
{{< /example >}}

This behavior can be mixed with grid column classes.

{{< example class="bd-example-cssgrid" >}}
<div class="grid">
  <div class="g-col-6">.g-col-6</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
  <div>1</div>
</div>
{{< /example >}}

## Customizing

Customize the number of columns, the number of rows, and the width of the gutters with local CSS variables.

- `--rows` is the number of rows in your grid template (default: `1`)
- `--columns` is the number of columns in your grid template (default: `12`)
- `--gutter` is the width of the gap between columns (default: `1.5rem`)

Because these CSS variables are local to the `.grid` class, you can override them whenever you like, as many times as you like, even across media queries.

{{< example class="bd-example-cssgrid" >}}
<div class="grid" style="--columns: 3;">
  <div>Auto-column</div>
  <div>Auto-column</div>
  <div>Auto-column</div>
</div>

<div class="grid" style="--columns: 4; --gutter: 5rem;">
  <div class="g-col-2">.g-col-2</div>
  <div class="g-col-2">.g-col-2</div>
</div>

<div class="grid" style="--columns: 10; --gutter: 1rem;">
  <div class="g-col-6">.g-col-6</div>
  <div class="g-col-4">.g-col-4</div>
</div>
{{< /example >}}

Adding more rows and changing the placement of columns:

{{< example class="bd-example-cssgrid" >}}
<div class="grid" style="--rows: 3; --columns: 3;">
  <div>Auto-column</div>
  <div class="g-start-2" style="grid-row: 2">Auto-column</div>
  <div class="g-start-3" style="grid-row: 3">Auto-column</div>
</div>
{{< /example >}}

## Sass

One limitation of the CSS Grid is that our default classes are still generated by two Sass variables, `$grid-columns` and `$grid-gutter-width`. You have two two options here:

- Modify those default Sass variables and recompile your CSS.
- Or, use inline or custom styles to augment the provided classes.

For example, you can customize the column count and gutter, and then size your "columns" with inline styles.

{{< example class="bd-example-cssgrid" >}}
<div class="grid" style="--columns: 18; --gutter: .5rem;">
  <div style="grid-column: span 14;">14 columns</div>
  <div class="g-col-4">.g-col-4</div>
</div>
{{< /example >}}

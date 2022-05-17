---
title: Creating loader animation from plain CSS.
date: "2022-02-26T22:40:32.169Z"
description: "Using CSS to create loading animations"
---
<style>
/* LOADERS */

.loader {
	--color: white;
	--size-mid: 10vmin;
	--size-dot: 1.5vmin;
	--size-bar: 0.4vmin;
	--size-square: 10vmin;
	
	display: block;
	width: 50%;
	display: grid;
	place-items: center;
}

.item	{
	display: grid;
	place-items: center;
	border-radius: 4px;
	transition: opacity 0.4s ease;
  	height: 2.5rem;
  	margin-bottom: 1rem;
}

.loader::before,
.loader::after {
	content: '';
	box-sizing: border-box;
	position: absolute;
}

/**
	loader --1
**/


.loader.--1::before {
	width: var(--size-mid);
	height: var(--size-mid);
	border: 8px solid var(--color);
	border-top-color: transparent;
	border-radius: 50%;
	/*animation: loader-1 1s linear infinite;*/
}


.loader.--1::after {
	width: calc(var(--size-mid) - 2px);
	height: calc(var(--size-mid) - 2px);
	border: 4px solid transparent;
	border-top-color: var(--color);
	border-radius: 50%;
	/*animation: loader-1 0.6s linear reverse infinite;*/
}


@keyframes loader-1 {
	100% {
		transform: rotate(1turn);
	}
}

/**
	miscs
**/


.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  place-items: center;
  height: 7em;
  padding: 1rem;
  min-height: 10rem;
}

.notes {
  grid-column: 1 / 3;
  text: blue;
}

.item {
  grid-column: 3;
}

code {
  background-color: white;
  color: black;
  border-radius: 10%;
}


.loader.--A::before {
	width: var(--size-mid);
	height: var(--size-mid);
	border: 4px solid var(--color);
	border-top-color: transparent;
	/*animation: loader-1 1s linear infinite;*/
}


.loader.--A::after {
	width: calc(var(--size-mid) - 2px);
	height: calc(var(--size-mid) - 2px);
	border: 2px solid transparent;
	border-top-color: var(--color);
	/*animation: loader-1 0.6s linear reverse infinite;*/
}

.loader.animation::before {
  animation: loader-1 1s linear infinite
}

.loader.animation::after {
  animation: loader-1 0.6s linear reverse infinite
}

.local-wrapper {
  display: grid;
  place-content: center;
  min-height: 8rem;
}

</style>
<div style="text-align: justify">

##### Quickly develop a loader using only pure and simple CSS.

<div class=local-wrapper>
  <div class="item"><i class="loader --1 animation"></i></div>
</div>


First let's use some HTML to create a container for our CSS stylings.

```html
<div class="item">
  <i class="loader --1"></i>
</div>
```

Moving on to CSS, let's start by defining the color and size of the loader, as well position and alignment settings of the grid:

```css
.loader {
  --color: white;
  --size-mid: 10vmin;

  display: block;
  position: relative;
  width: 50%;
  display: grid;
  place-items: center;
}
```
Using units like `vmin`, `vmax` and `rem` provides immediate responsiveness to viewport aspect ratio changes without the need to use `media queries`.

> Next let's the pseudo-elements `before` and `after`. Pseudo-elements are special words in CSS that allow you to style certain parts of selected components. The `before` and `after` pseudo-elements can be used to inject content right before or after a target.

We will use pseudo-elements associated with position settings to create two layers in our container. We will style these two layers in different ways to create the loader animation effect.

```css
.loader::before,
.loader::after {
  content: "";
  box-sizing: border-box;
  position: absolute;
}
```

We've just created two elements that will come just before and after each and every component on our page that has the "loader" class. The thing here is that so far these elements have no content.

> An important setting is `position: absolute`, which causes these two elements to be positioned relative to their parent element. This property will help postion both ::before and ::after at the same place, as if they were two layers of the same object.

The `border-box` setting makes the `width` of the component its content, padding and border.

Now that we have set up both layers let's start injecting some CSS to give life to our element. We'll start with `::before`.

```css
.loader.--1::before {
	width: var(--size-mid);
	height: var(--size-mid);
	border: 8px solid var(--color);
	border-top-color: transparent;
```
<div class="wrapper"><div class="notes">Agora finalmente podemos visualizar nosso loader ganhando forma:</div><div class="item">
  <i class="loader exemplo" style="width: var(--size-mid);height: var(--size-mid);border: 4px solid var(--color);border-top-color: transparent;"></i>
</div></div>

With just a few CSS commands like `width`, `height` and `border`, we started building our loading animation. We'll use the same method for `::after`, just gently changing some settings. To visualize the result, let's comment out the `::before` code so that the layer is not visible.

```css
.loader.--1::after {
  width: calc(var(--size-mid) - 2px);
  height: calc(var(--size-mid) - 2px);
  border: 4px solid transparent;
  border-top-color: var(--color);
}
```

<div class="wrapper"><div class="notes"><code>.loader.--1::before</code>:</div><div class="item">
  <i class="loader exemplo" style="width: calc(var(--size-mid) - 2px);height: calc(var(--size-mid) - 2px);border: 2px solid transparent;border-top-color: var(--color);"></i>
</div></div>

<div class="wrapper"><div class="notes"><code>::before</code> e <code>::after</code> together:</div><div class="item">
  <i class="loader --A" style="border-radius: 0%;"></i>
</div></div>



<div class="wrapper"><div class="notes">To give it a circular shape, one option is to add the configuration <code>`border-radius: 100%`</code> in both layers we`ve just created:</div><div class="item"><i class="loader --1"></i></div></div>

Now let's introduce a rotation animation and apply it to each of the ::before and ::after, making sure they'll rotate in different directions and speeds. We will use the `transform` CSS property and the `rotate` command.

```css
@keyframes loader-1 {
	100% {
		transform: rotate(1turn);
	}
```
To apply this animation, let's insert the following commands in each of the `::before` and `::after` blocks:

```css
animation: loader-1 0.6s linear reverse infinite

animation: loader-1 1s linear infinite
```
<div class="wrapper"><div class="notes">Now, the loader is ready to be applied:</div><div class="item"><i class="loader --1 animation"></i></div></div>

I learned to develop this loader in [Jenning](https://codepen.io/jenning)'s CodePen, [Simple CSS Loaders](https://codepen.io/jenning/pen/YzNmzaV). There you can learn how to build other CSS loaders like this one.

<div style="text-align: right">

###### []'s


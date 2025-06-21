# Frontend Mentor - Testimonials grid section solution

This is a solution to the [Testimonials grid section challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/testimonials-grid-section-Nnw6J7Un7). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size

### Screenshot

![Desktop](/images/solution-screenshot-desktop.png)
![Mobile](/images/solution-screenshot-mobile.png)

### Links

- Solution URL: [https://github.com/HaiDangN/testimonials-grid-section]
- Live Site URL: [https://haidangn.github.io/testimonials-grid-section/]

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid

### What I learned

Biggest thing I learned is how to use CSS grid at a basic level. I learned how to manually set the grid's columns and rows with the dimensions of each cell. I also learned how to set the dimensions dynamically with the viewport's width. In this code, 4 is the amount of columns and the second value is how much space they take up (each get equal weighting so "1fr" = 1 fraction)

```css
.testimonials {
    grid-template-columns: repeat(4, 1fr); 
    grid-template-rows: repeat(2, auto); 
}
```

I also sort of learned how clamping works. The first value is the minimum value, the second is the default, and the third is the max value. So here, it won't get smaller than 2rem (32px) or larger than 10rem (160px). And it will try to be 10% of the viewport width which in the solution is 1440px / 10 = 144px.

```css
padding-inline: clamp(2rem, 10vw, 10rem);
```

This one is cool. I learned how to include calculations in the css property values. I wanted this background to be 4rem from the right of the container so I did this:

```css
    background-position: calc(100% - 4rem) 0;
```

Also this is the rest of the css for an image that isn't the background but you want to be overlayed with the background color:

```css
    background-image: url('images/bg-pattern-quotation.svg');
    background-repeat: no-repeat;
    background-position: calc(100% - 4rem) 0;
    background-color: hsl(263, 55%, 52%);
```

I learned how to target specific elements in the dom if they several elements have the same class name. Using `:nth-of-type(n)` where n is their order.

``` css
    .testimonials__card--compact:nth-of-type(2) {
    }
```

To make an image a circle, use `border-radius: 50%;`

I'm also proud of my HTML structure as well as the BEM naming. I did use chatgpt to help me though..but my goal is to have the intuition to do it by myself.

BEM stands for Block, Element, and Modifier. The block here is `testimonials`. The element are the cards; `testimonials__card`. And the modifier is the word that differentiates the, for example: `testimonials__card--featured` for the featured testimonial.

```html
    <section class="testimonials">
      <article class="testimonials__card testimonials__card--featured">
        <div class="testimonials__profile">
          <img src="images/image-daniel.jpg" alt="">
          <div class="testimonials__user-info">
            <h3 class="testimonials__name">Daniel Clifford</h3>
            <p class="testimonials__status">Verified Graduate</p>
          </div>
        </div>
        <h2 class="testimonials__headline u-text-light-grey">
          I received a job offer mid-course, and the subjects I learned were current, if not more so,
          in the company I joined. I honestly feel I got every penny’s worth.
        </h2>
        <p class="testimonials__text">
          “ I was an EMT for many years before I joined the bootcamp. I’ve been looking to make a
          transition and have heard some people who had an amazing experience here. I signed up
          for the free intro course and found it incredibly fun! I enrolled shortly thereafter.
          The next 12 weeks was the best - and most grueling - time of my life. Since completing
          the course, I’ve successfully switched careers, working as a Software Engineer at a VR startup. ”
        </p>
      </article>
```
---
title: "Scale is just another component"
---

The news of modular scales first reached me in 2011. I read an A List Apart article titled ["More Meaningful Typography"](http://alistapart.com/article/more-meaningful-typography). Almost seven years on, I still use the modular scale in all my design work.

> A modular scale is a sequence of numbers that relate to one another in a meaningful way. Using the golden ratio, for example, we can produce values for a modular scale by multiplying by 1.618 to arrive at the next highest number, or dividing by 1.618 to arrive at the next number down.

> — More Meaningful Typography by Tim Brown
 

Visual scales are nothing new. Typographers and graphic designers have experimented with them for centuries to bring elegance and structure to their work.

Visual scales are invented to take the guesswork out of composing layouts. By using mathematics ,  to eyeball everything they placed on a page until it looked right.

The modular scale has almost fallen out of use today. Some libraries, like [Bourbon](https://www.bourbon.io/docs/latest/#modular-scale), still come with modular scale functionality, buy its rare to see it put to use in real projects.

## A visual guide to the modular scale
The modular scale is to the eyes what the musical scale is to the ears. Musical and visual scales share three important similarities:

- They can be expressed as simple mathematical formulas. 
- They highlight an invisible structure of "meaningful numbers" that coincide with ratios that the human brain finds appealing.
- Because of this, they can be used to make something look or sound good without the need to understand why it works.

[Curve with no labels]

### Three magic numbers
If you wanted to make a modular scale, you'd need to define just three numbers:

- **Exponent** The number that let's you move forward and backwards along the scale.
- **Base** The number to be multiplied by (on the web this is usually the default font size of 16px.
- **Scale** The most important number. Set's the amount that the scale will increase by on each step.

And you'd apply the numbers like so:

<div class="maths">***Value** = **Scale^Exponent^** ⋅ **Base***</div>

[modular scale curve with numbers]

## A tool for working with the modular scale
<div class="box">
I've made a [GitHub repository](https://github.com/nosajio/modularscale) containing a bunch of implementations of the modular scale in different frontend languages.
</div>

The languages supported so far are: SCSS, pure Javascript, and Styled Components. If you'd like to add more, make a pull request and I'll make sure to merge it in.

There's a tool for experimenting with different scales at [modularscale.com](http://www.modularscale.com).

<div class="image">
  <img src="http://a.nosaj.io/modularscale/ms-ui-labelled.jpg" alt="UI made with modular scale with labels." />
  <div class="caption">A simple layout constructed using the modular scale.</div>
</div>

As you can see in the example above, by adjusting the scale's exponent value it's possible to compose a layout relying just on the modular scale for sizes and spaces, and because it's [DRY](https://www.codementor.io/joshuaaroke/dry-code-vs-wet-code-89xjwv11w), any changes to the base or scale variables will affect the entire layout. This is the magic of the modular scale.

For examples of how to use one of the modular scale helpers in your own project, refer to the Readme or the examples over on GitHub.

If you have any questions or recommendations about the modularscale-helpers project, you can find me on [twitter @__nosaj](https://twitter.com/__nosaj).



---
title: "Scale is just another component"
---

The news of modular scales first reached me back in 2011 in an [A List Apart article titled "More Meaningful Typography"](http://alistapart.com/article/more-meaningful-typography). Seven years later, I still use modular scales in all my design work.

> A modular scale is a sequence of numbers that relate to one another in a meaningful way. Using the golden ratio, for example, we can produce values for a modular scale by multiplying by 1.618 to arrive at the next highest number, or dividing by 1.618 to arrive at the next number down.

> — More Meaningful Typography by Tim Brown
 

Visual scales are nothing new. Over the centuries typographers and graphic designers used them to bring elegance and structure to their works.

Using the modular scale takes the guesswork out of composing layouts because you no longer have to eyeball everything you place on a page until it looks right. Or even worse, have a designer sign off on every UI change.

A good way to think of the modular scale is as a visual analogue to musical scales. They have several things in common: 

- They can be expressed in simple mathematical formulas. 
- They highlight an invisible structure of "meaningful numbers" that coincide with ratios that humans find appealing.
- They're both simple ways to make something look or sound good, without the need to understand why.

## The three numbers that make the modular scale
If you wanted to make a modular scale, you'd need to define three numbers:

- **Exponent** The number that let's you move forward and backwards along the scale.
- **Base** The number to be multiplied by (on the web this is usually the default font size of 16px.
- **Scale** The most important number. Set's the amount that the scale will increase by on each step.

And you'd apply the numbers like so:

<div class="maths">***Value** = **Scale^Exponent^** ⋅ **Base***</div>

[modular scale visualisations]

Note that the curve above is smooth, but when generating a scale we only use values from each whole increment. For example:

[Visualisation]

## A tool for working with the modular scale
<div class="box">
I've [made]() a [GitHub repository](https://github.com/nosajio/modularscale) containing a bunch of implementations of the modular scale in different frontend languages.
</div>

The languages supported so far are: SCSS, pure Javascript, and Styled Components. If you'd like to add more, make a pull request and I'll make sure to merge it in.

There's a tool for experimenting with different scales at [modularscale.com](http://www.modularscale.com).

[Example layout using modular scale with `Scale^exponent*Base = Value` labels on sizes]

As you can see in the example above, by adjusting the scale's exponent value it's possible to compose a layout relying just on the modular scale for sizes and spaces, and because it's [DRY](https://www.codementor.io/joshuaaroke/dry-code-vs-wet-code-89xjwv11w), any changes to the base or scale variables will affect the entire layout. This is the magic of the modular scale.

For examples of how to use one of the modular scale helpers in your own project, refer to the Readme or the examples over on GitHub.

If you have any questions or recommendations about the modularscale-helpers project, you can find me on [twitter @__nosaj](https://twitter.com/__nosaj).



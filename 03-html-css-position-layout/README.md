# intro to HTML & CSS: position and layout

In this workshop, we'll build a basic intuition of HTML and CSS, the two languages that affect how a website looks. We'll emphasize HTML as a tool that defines the **structure** of a webpage; more on that later.

*Note:* this workshop's written portion is an amalgamation of a couple workshops Matt and [Leo](https://krashanoff.com/) ran for the [Learning Labs Crash Course](https://github.com/uclaacm/learning-lab-crash-course-su20): the intermediate CSS lessons on [The Box Model & Positioning](https://github.com/uclaacm/learning-lab-crash-course-su20/tree/main/02-intermediate-css) and [Flexbox & Grid](https://github.com/uclaacm/learning-lab-crash-course-su20/tree/main/04-flexbox-grid).

## Table of Contents

* [Workshop Goals](#workshop-goals)
* [The Box Model](#the-box-model)
  * [The Content Area](#the-content-area)
  * [The Padding Area](#the-padding-area)
  * [The Border Area](#the-border-area)
  * [The Margin Area](#the-margin-area)
  * [Padding vs. Margin](#padding-vs-margin)
  * [Aside: the box-sizing property](#aside-the-box-sizing-property)
* [display:inline and display:block](#displayinline-and-displayblock)
* [The position property](#the-position-property)
  * [A quick aside on z-index](#a-quick-aside-on-z-index)
* [CSS Grid](#css-grid)
  * [But wait, there's more](#but-wait-theres-more)
* [Putting It All Together](#putting-it-all-together)
* [Licensing](#licensing)


## Workshop Goals

This workshop covers three big areas of CSS styling: the box model, positioning, and layout.

On the box model, we'll answer:

* What is the "Box Model"? How does that play into how we view websites?
* What are `padding` and `margin`? How are they different?
* What is a block element? An inline element?

On the `position` property, we'll answer:

* What does the CSS `position` property due? What do the values `absolute`, `relative`, and `fixed` do?
* How does inheritance in CSS work? (note: this will be light)

On layout, we'll discuss:

* What is CSS Grid?
* What is it useful for?
* What are some other alternatives?

We'll then put this all together and work on a pretty neat website!

## The Box Model

The **box model** is a core part of HTML and CSS, and you'll likely hear about it more as you read web documentation, talk to web developers, and do front-end interviews. But what exactly does the box model mean?

The box model says that **every HTML element is really just a box**. Simple, right? But, there's a bit more. In particular, it says that each box is comprised of four (somewhat concentric) rectangles that describe the layout of element. These four rectangles (or areas, zones, parts), are called:

1. The Content Area
2. The Padding Area
3. The Border Area
4. The Margin Area

Before we discuss each of these areas, it would be helpful if we could see a diagram explaining what we mean. Here's one, courtesy of the Mozilla Developer Network:

![MDN example of Box Model](images/mdn-box-model.png)

Was that confusing? Hopefully not, but let's break each portion down.

### The Content Area

The content area contains, well, your content. By default, the size of this area is determined by the size of your content: a `400px` image will have a content area of size `400px`, and text *generally* fills as much space as possible (though we'll go into this more in a bit). In addition, we've played around with the `width` and `height` attributes: by default, the `width` and `height` attributes only affect the content area.

This is the easiest area to think about and examine. We can do this with a very trivial code example:

```css
/* CSS file */
.box {
  width: 300px;
  height: 300px;
  background-color: blue;
}
```

```html
<!-- HTML FILE -->
<div class="box">
  I'm a box!
</div>
```

![screenshot of content area example](images/content-area.png)

A good question that you might be asking is "what are the default `width` and `height` values for the content area?". That's a *very* good question, and we promise we'll get there by the end of this session.

### The Padding Area

Now, let's throw our next box in. The **padding** of a box surrounds the content area with whitespace. I You can control the `padding` of a box with a set of CSS properties, such as:

* `padding-top: 5px;`, which would add 5 pixels of padding to the top of a content area
* `padding-right: 5px;`, which would add 5 pixels of padding to the right of a content area
* `padding-bottom: 5px;`, which would add 5 pixels of padding to the bottom of a content area
* `padding-left: 5px;`, which would add 5 pixels of padding to the left of a content area
* `padding: 5px;`, which adds 5 pixels of padding to the top, right, bottom, and left of a content area

When we say *whitespace*, we mean that there is nothing there, *transparently*; that is to say, we will display whatever is the background of the element.

Let's also take a look at this with a code example. One very common use case of `padding` is to "pad" some text, to make it more visually appealing.

```css
/* CSS file */
.orange-box {
  background-color: orange;
  width: 200px;
  height: 200px;
}
.padded-orange-box {
  background-color: orange;
  width: 200px;
  height: 200px;
  padding: 10px;
}
```

```html
<!-- HTML FILE -->
<div class="orange-box">
  Why are spiders so good at making websites? Because they're great web developers!
</div>
<br />
<div class="padded-orange-box">
  Why are spiders so good at making websites? Because they're great web developers!
</div>
```

![screenshot of padding + content areas example](images/padding-area.png)

The padded box looks better, and it's easier to read! Note that the second box is actually bigger: even though the `width` and the `height` is the same, that only affects our content area: our entire box is actually `220px` by `220px`!

Also, notice that the space between the inside box and the outside box is orange, the `background-color` of the element. We want to emphasize that the "whitespace" that padding creates isn't always white!

By default, if no `padding` property is specified, the browser will assume that `padding: 0px;`.

### The Border Area

Hopefully, the **border area** should be somewhat self-explanatory: it creates a visible border around your padding and content areas. Unlike padding, border related properties all add some sort of color, and can sometimes add patterns as well.

There are a plethora of different options to customize a border (and we recommend you take a look at some documentation when you have the chance), but for now, we'll examine the `border` property (which is in reality shorthand for `border-width`, `border-style`, and then `border-color`).

This is best explained visually. Let's look at this with another common code example, a simple "card" element:

```css
/* CSS file */
.text-card {
  width: 200px;
  height: 200px;
  padding: 10px;
  border: 1px solid black;
}
```

```html
<!-- HTML FILE -->
<div class="text-card">
  I never understood Fifty Shades of Gray - there are at least thousands in RGB color space.
</div>
```

![screenshot of border + padding + content areas example](images/border-area.png)

Here, the `border: 1px solid black;` is telling us:

* the border should be `1px` wide
* the border should be `solid` (it could also be dashed)
* the border should be `black`

Also, note that the border goes around both the content and the padding! And, the border itself is adding to the size of our box: the total size of `.text-card` is actually `221px` now!

### The Margin Area

Last, but not least, let's talk about margin! Margin operates somewhat similarly to padding, in that we'll add some space around the element. Like `padding`, there's:

* `margin-top`
* `margin-right`
* `margin-bottom`
* `margin-left`
* and the shorthand `margin`

Let's take a look at an example with all of our elements in play, building on our card example:

```css
/* CSS file */
.text-card-mb {
  width: 200px;
  height: 200px;
  padding: 10px;
  border: 1px solid black;
  margin-bottom: 50px;
}
```

```html
<!-- HTML FILE -->
<div class="text-card-mb">
  I never understood Fifty Shades of Gray - there are at least thousands in RGB color space.
</div>

<div class="text-card-mb">
  Paradoxically, taking computer organisation has made my computer less organized; there's stacks and heaps of files everywhere now!
</div>
```

![screenshot of margin + border + padding + content areas example, with margin-bottom: 50px;](images/margin-area.png)

Notice that, in addition to the padding within the box, we've now added space between the boxes: `50px` to be exact!

There is one difference between the behaviour of margin and padding, other than their difference in order respective to the box model. Margins "collapse": that is to say, if two elements on top of each other have `margin-bottom: X;` and `margin-top: Y;`, the total space won't be `X + Y` (as it would for padding); instead, it'll *collapse* the margins, and pick the larger item. We can see this with our text cards:

```css
/* CSS file */
.text-card-spaced {
  width: 200px;
  height: 200px;
  padding: 10px;
  border: 1px solid black;
  margin: 50px;
}
```

```html
<!-- HTML FILE -->
<div class="text-card-spaced">
  I never understood Fifty Shades of Gray - there are at least thousands in RGB color space.
</div>

<div class="text-card-spaced">
  Paradoxically, taking computer organisation has made my computer less organized; there's stacks and heaps of files everywhere now!
</div>
```

![screenshot of margin + border + padding + content areas example with margin collapsing, with margin 50px;](images/margin-collapse.png)

Note that the visual distance between the two cards is the same as our previous example, even though we've changed the `margin-bottom: 50px;` to `margin: 50px;`!

### Padding vs. Margin

Often times, you'll want to add some space to your website. You now have two great options in your toolkit: `padding` and `margin`. But, which should you pick?

If you wanted a one-liner, it would look something like this:

> Padding creates space inside an element, while margin creates space between elements.

In general, Matt uses that as a good rule of thumb. However, you'll develop your own internal intuition on which is the right choice to use, and eventually, you'll have more tools in your toolkit to properly space out your webpage.

### Aside: the `box-sizing` property

Technically, what we just described is how margin, border, padding, and content play together when the property `box-sizing: content-box;` is set, which is the default value.

However, you'll often see people set `box-sizing: border-box;` instead (which is something that we often do as well).

What does this do? Well, instead of making `width` and `height` control just the content area, it makes those properties control *the combination of border, padding, and content* instead! This is often very convenient, because you can dynamically size the "bordered content" with `width` and `height` without having to account for the padding or border sizes.

A quick example:

```css
/* CSS file */
.text-card-spaced {
  width: 200px;
  height: 200px;
  padding: 10px;
  border: 1px solid black;
  margin: 50px;
}
.box-sizing-border-box {
  box-sizing: border-box;
}
```

```html
<!-- HTML FILE -->
<div class="text-card-spaced">
  This card is actually 200 + 10 + 1 + = 211px wide and tall (width + padding + border).
</div>

<div class="text-card-spaced box-sizing-border-box">
  This card is 200px wide, just as we set!
</div>
```

![screenshot comparing box-sizing values of content-box and border-box](images/box-sizing.png)

It's so convenient, in fact, that some developers (like us) apply the property to all elements:

```css
/* the '*' selector applies to all elements */
* {
  box-sizing: border-box;
}
```

However, you need to **opt-in** to this feature, which is why we explained the box model in this order. It's up to you on which you prefer - just make sure everybody on your team is clear on what you're using!

## `display:inline` and `display:block`

One concept that's closely related to the box model is the `display` property. It turns out, the `display` property has many possible values (including `flex` and `grid`, which we'll go over in a later session), but for now, we'll focus on two very important ones: `inline` and `block`.

**Block** and **inline** are a mutually exclusive way to describe the behaviour of an element, and in particular, these key properties:

* a block element **takes up the full width of its parent** (unless changed with CSS), while an inline element **only takes up the width of its content** (unless changed with CSS)
* a block element **always starts on a new line**, while an inline element does not

Why is this important? Well first, this describes some of the behaviour of HTML tags that we've used before; note that creating a new `<p>` or `<div>` tag breaks the content on a new line, while tags like `<a>` and `<span>` don't. This is because `<p>` and `<div>` (among many others) are by default block-level elements, while `<a>` and `<span>` are by default inline.

You can change these values with `display:inline` and `display:block`, which happens more often than you might think! To bring forward one example, you'll often see a snippet of code that looks something like this:

```css
.large-img-container {
  width: 600px;
  height: 600px;
  border: 1px solid black;
  background: pink;
}

.small-img-container {
  width: 400px;
  height: 400px;
  border: 1px solid black;
  background: pink;
}

.img-responsive {
  display: block;
  max-width: 100%;
  height: auto;
  margin-left: auto;
  margin-right: auto;
}
```

```html
<!-- images/wash.jpg is 500x500 -->
<div class="large-img-container">
  <img src="images/wash.jpg" />
</div>
<br />
<div class="large-img-container">
  <img src="images/wash.jpg" class="img-responsive" />
</div>
<br />
<div class="small-img-container">
  <img src="images/wash.jpg" />
</div>
<div class="small-img-container">
  <img src="images/wash.jpg" class="img-responsive" />
</div>
```

![screenshot using img-responsive when the image is smaller than the container](images/img-responsive-smaller.png)

First, let's look at what this does when the image is smaller than the container. The first (untouched) element is in the top-left, as we'd expect. But, the second one, with `img-responsive`, is horizontally centered. Nice! This is because of `margin-left: auto;` and `margin-right: auto;` (which we'll explain in a moment).

![screenshot using img-responsive when the image is larger than the container](images/img-responsive-larger.png)

Next, we look at what this does then the image is larger than the container. The first (untouched) element expands past its container, which makes it look ugly. But, the second one, with `img-responsive`, is just within the bounds of its container. Nice! This is because of `max-width: 100%`, which we'll explain in a bit.

In essence, what we've done is horizontally center an image and make it as big as possible in its container. It's necessary for us to set `display:block;`, as the `<img>` is inline by default, and we need to use the property that a block element takes up the full width of its parent for this to work.

While we're on the topic, let's quickly also mention what `max-width` and `auto` do, since they're relevant in the context of block-level elements.

* `max-width` overrides the `width` property, and stops the `width` from ever being larger than the `max-width` property. Basically, this says to never scale the image larger than its original size.
* the `auto` keyword automatically adjusts the value of its property based on the content and context of the element. `height: auto;` keeps the aspect ratio the same as the image gets larger, while `margin-left:auto;` and `margin-right:auto;` "fill" the rest of the space in the block-level element (as our width can't get larger than `100%`, so something else needs to take on the space.

If that didn't make too much sense, that's okay - that was a bit of a hand-wavy explanation. We'll include some resources below that explain that more in-depth.

## The `position` property

We have now discussed layout and spacing, but how do we determine the position of an element? It turns out, there will be many different ways to do so, but one of the earliest ways to do so was with the `position` property. It has five values:

* `static` (the default)
* `relative`
* `fixed`
* `absolute`
* `sticky`

Everything so far we have discussed is what happens when you set `position:static`; elements appear one after another, known as the "normal" flow.

The other `position` values change what the properties `top`, `right`, `bottom`, and `left` do - things we haven't discussed yet. Let's discuss them now!

Each of those properties are an *offset property*, in that they tell the browser how far from the "offset" to place the new content area: for example,

```css
.some-element {
  top: 30px;
  left: 45px;
}
```

Would place that element 30 pixels from the top, and 45 from the left of its reference point.

But what is the reference point? That's what each of `relative`, `fixed`, and `absolute` describe:

* `relative`: the reference point is where the content area would be normally, i.e. before using `top`, `right`, `bottom`, and `left`. In our example, this would shift our element 30 pixels down, and 45 to the right.
* `fixed`: the reference point is the **viewport**, which is a fancy name for the edge of the browser. In our example, our element would be 30 pixels down and 45 to the right of the top-left corner of the screen, and it'll stay there **even when we scroll**.
* `absolute`: the reference point is the first parent that has `position` not equal to `static` (choosing the entire document if needed). In our example, our element would be 30 pixels down and 45 to the right of the top-left corner of the top of the page, and will move away as we scroll.

These are harder to demonstrate with screenshots, so we recommend that you visit [this W3Schools Demo](https://www.w3schools.com/css/css_positioning.asp) for more information!

Okay, and what about `position: sticky`? This one is a bit more complicated, and depends on the scroll position of the website. From a high level,

* by default, we treat it as `postion: relative`
* if the user has "scrolled past" where the element is on the website, it then becomes `position: fixed`

Why would we want this property? It turns out, it's very useful in creating navigation bars and table headers - something you'll probably do as a web developer at some point.

You can see a demo and more information on the [MDN Page](https://developer.mozilla.org/en-US/docs/Web/CSS/position#Sticky_positioning).

### A quick aside on `z-index`

If you're thinking carefully, you might have the question: what happens when two elements overlap? What chooses what goes on top of what?

The answer is the `z-index` property, which we don't have too much time to go in-depth in the presentation. The very short answer is that if you think of the webpage as being governed by the x-axis and the y-axis, the natural "z-axis" would point at you, coming out of the monitor. By setting the `z-index` property, we can dictate the position of elements along this "z-axis". For example, an element with `z-index: 999` is "closer to you" than an element with `z-index: 100`, so it'll be on top. By default, elements have `z-index: 0`.

You should read more about `z-index`; the [MDN page](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) is pretty manageable.

## CSS Grid

Let's switch gears and talk about layout for a moment. One of the easiest (and also newest) tools that CSS provides is called CSS Grid.

Put simply, it is CSS' way of organizing content into a rigid grid on the page.

Let's visualize this with a simple webpage. I have product cards that I want to lay out in a rigid, 3x3 grid containing previews of my top items.

![a black three-by-three grid overlay ed on a white background](images/3x3.png)

We will have *at most* 9 items to preview on this grid, so it works out nicely.

To create a CSS grid, we just need a container and its children.

```html
<div id='container'>
    <div class='element'>
        Content
    </div>
    <div class='element'>
        Content
    </div>
    <div class='element'>
        Content
    </div>
    <!-- ... -->
</div>
```

Then, if we want to let all our child elements occupy the specified space, the styling can be carried out entirely through the parent:

* To create columns, we use the property `grid-template-columns`
* To create rows, we use the property `grid-template-rows`
* We can specify the gaps between parts of the grid with `grid-column-gap` and `grid-row-gap`

Since we want to create a 3x3 grid, our CSS will look like:

```css
#container {
    display: grid;
    grid-template-columns: 33% 33% 33%;
    grid-template-rows: 33% 33% 33%;
}
```

That's not super clean, though. Luckily, CSS accounts for this by giving us the `auto` value. If we want to create 3 columns and rows of equal size, we can just swap out our 33% with it!

```css
#container {
    display: grid;
    grid-template-columns: auto auto auto;
    grid-template-rows: auto auto auto;
}
```

And if we wanted to go ahead and make the middle column a little larger than the others, or a specific size, we can remove that particular `auto` in favor of a specific value:

```css
#container {
    display: grid;
    grid-template-columns: auto 500px auto;
    grid-template-rows: auto auto auto;
}
```

The best part of using the `auto` keyword is that we can allow the rows and columns to automatically adjust to the `gap` we specify, or any other changes.

### But wait, there's more

There's a **lot** more to CSS grid than we've covered, but the purpose of this section was to simply introduce it. If you'd like to read any more about it, you can find some great [resources](#Resources) down below.

## Some other layout options

CSS Grid is not our only layout option! We don't really have time to go in-depth for others, but let's quickly mention some other alternatives that you may have heard of:

* [Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) (short for flexible box model) is an alternative `display` mode that's much more *flexible* than CSS Grid. It's great for vertically aligning objects, dealing with items that might have variable or unknown sizes, and really complicated layouts.
* [Float (and clearfix)](https://developer.mozilla.org/en-US/docs/Web/CSS/float) is a tried and true method to align elements to the left and right of a container. For many cases, CSS Grid can do the trick!

## Putting It All Together

This section is done live, and we do it together as a group; unfortunately, it's pretty hard to put this into writing.

We'll run through:

* making common elements with the box model modifiers: "cards", buttons, and navbars
* creating a two-column layout with grid and box model modifiers
* using `position: fixed;` to make a navbar!

## Licensing

Like the rest of this repository, the contents of this workshop are dual-licensed under the [MIT License](https://github.com/uclaacm/transfer-accel-portfolio-website-workshop/blob/main/LICENSE) and the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/); feel free to use whichever license suits your purpose better.

I'd love to hear if you found this helpful, or if you have any suggestions! Please send me an email at [matt@matthewwang.me](mailto:matt@matthewwang.me).

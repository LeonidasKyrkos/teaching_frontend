##### Frontend Development Lunch and Learns Series

# Cascading Style Sheets

So you've got a basic understanding of HTML, and you've added some titles and text to a page. At this point it becomes important to understand how to *style* your content. CSS is the tool that frontend developers use to shape and decorate their HTML. As I'll be showing you, CSS can be used to do some fairly complex things. But for now we'll be focusing on the simple stuff and move on from there.

## What can it do?

Here's a short list of some things that can be achieved in CSS:

* Set a background colour
* Set a background image
* Change your text colour
* Change your font size
* Change your font family
* Change your line height
* Make the text centre aligned
* Add some padding to your element
* Add a margin
* Add a border

## What does it look like?

The great thing about CSS is that it was designed to be human readable, so it's the least alien looking part of the frontend development landscape. HTML has tags that look ugly and are difficult to read. JavaScript has all sorts of computer sciency looking stuff. CSS mostly avoids this complexity and even someone who has never written any can do a reasonable job of understanding it. Here's an example.

```css
p {
    color: red;
    padding: 10px;
    margin-bottom: 20px;
    font-size: 18px;
    font-family: "Helvetica";
    text-align: left;
    line-height: 1.5;
}
```

So, reading that for the first time you can immediately understand about 75% of it. You might note that the language was created by Americans because they've misspelled colour, but you'll get over that fairly quickly. Assuming you know what a pixel is, you can likely assume the behaviour of the padding, margin and font-size lines. Font family should make sense, as should text-alignment. Line height probably reads fine as well, but the value might be a little strange; you might have expected a px value for it as well. Overall, you can look at this block of CSS and know roughly what it's up to. And you can probably tell *what* it's being applied to as well, i.e. the ```<p></p>``` tag.

![Anatomy of a CSS block](assets/anatomy-of-a-css-rule.gif)

As you can see in the above diagram, a CSS block is made up of a *selector* (what we want to style) and some *rules* (how we want to style it).

## Selectors

A CSS selector dictates for which HTML element our CSS declarations apply. In the above diagram we can see a tagname selector, h1. This will apply our styles to every ```<h1></h1>``` element in our HTML document. A powerful tool but a pretty unwieldy one. What if you don't want all of your h1 tags to look the same? Let's introduce a more nuanced selector to the mix:

```html
<h1> This is a title</h1>
<h1 class="title">This is a different looking title</h1>
```

```css
.title {
    color: #919191;
    font-size: 24px;
    line-height: 1.5;
    font-weight: 700;
}
```

Meet the "class" selector (denoted by a "." preceding the class name). They are the most important tool in your arsenal because they allow you to be specific with your styling.

Here are just a few of the many many many selectors that are available to you. There are at least a dozen more and they all allow you to do some specific task that isn't usually important as a beginner. And the more fancy the selector, the more likely it is to be abused in a foolish way.


| Name         | Selector style        | HTML example                                                    |
|--------------|-----------------------|-----------------------------------------------------------------|
| All elements | *                     | ```<any-tagname></any-tagname>                                    ``` |
| Tagname      | h1                    | ```<h1></h1>                                                      ``` |
| Classname    | .classname            | ```<div class="classname"></div>                                  ``` |
| ID           | #header               | ```<div id="header"></div>                                        ``` |
| First child  | SELECTOR:first-child  | ```<div>selects this one</div> <div></div>                        ``` |
| Last child   | SELECTOR:last-child   | ```<div></div> <div>selects this one</div>                        ``` |
| Nth-child    | SELECTOR:nth-child(3) | ```<div></div> <div></div> <div>selects this one</div> <div></div>``` |

## RULES

CSS comes with some rules that we need to learn before we go any further and start playing with our new selectors. I'll try to explain these almost entirely with examples because describing them is less impactful than *seeing* them.

### The Cascade

```css
.title {
    color: red;
    background-color: black;
}

.title {
    color: blue;
}
```

**Lower down in the document = more important**

And that rule works great and is super reliable **until it isn't reliable at all**. Just remember that two completely identical selectors are allowed, but the second one's rules will take precedence. In the example above, the background colour would still be black, but the color of the title's text would be blue.

### Specificity

This is a confusing topic so we'll be spending a bit more time on it. In the same way that **lower items** override higher items, more **specific** selectors override less specific selectors. For example:

```html
<h1 class="title">I'm a title</h1>
```

```css
.title {
    color: red;
}

h1 {
    color: blue;
}
```

A tag selector is a very general selector. The more things it can apply to the more general it is. A class selector by comparison is fairly specific. It only applies to those elements that have the class. As such, even though it's higher up in our stylesheet, it overrides our tag selector and the h1 with the title class becomes red. Check out the example in examples/specificity.

Here's another example:

```html
<div class="title__wrapper">
    <h1 class="title">This is a title</h1>
</div>
```

```css
.title__wrapper .title {
    color: blue;
}

.title {
    color: red;
}
```

You can use the HTML family tree in your CSS selectors; writing one selector, then a space, and then another selector. This is called a *child selector*. It doesn't matter how nested the element's child is. If it exists in that element's descendant tree, it will be targeted by the child selector. And as you can imagine, this is more specific than a lone class selector. Hence the above example will output text which is blue. See examples/specificity_2/index.html if you'd like to play around with it.

This is probably the most abused selector style on the web and I would recommend that you avoid it for as long as possible. Here are the good reasons to use it:

#### Theming

Let's say you have a website that uses orange and black as its primary colours. Someone comes along and wants a version of the site which is blue and white. You could create a new version and write all of your styles again, substituting your colours for the new ones. Or you could use the exact same work again and pop a class on your Body element called "blue-theme". Then in your css you can add this:

```css
.title {
    color: orange;
}

.blue-theme .title {
    color: blue;
}
```

This saves you a lot of effort and has relatiely few *side effects*. The name of the theme class implies its impact and it allows you to do some specific overwrites. Good plan.

#### Lack of control

Sometimes you'll use a plugin which controls its own HTML. You're allowed to change its appearance with CSS, but you have no control over the markup it outputs. In those situations you're reduced to child selectors by necessity.

**That's it**. For now assume that there are no other good reasons to use it and avoid it wherever possible.


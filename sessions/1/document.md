# Lunch and Learns Series

## What is Frontend development?

### Static sites

* Interfaces
    * HTML
    * HTML5
    * CSS
    * JavaScript

### HTML
Hypertext Markup Language

**Hypertext**

Fun buzzword that sounds cool

**Markup**

*"In computer text processing, a markup language is a system for annotating a document in a way that is syntactically distinguishable from the text."*. Which is a complicated way of saying that all of the content in a "markup" language includes some information about what that content is. So for example:

```html
<p>Hello there I am a paragraph. I have multiple sentences. I'm supposed to be read by a human.</p>
```

In the above example we have a paragraph tag enclosing some content that can be described as a "paragraph" and because we're using a markup language, the **tags** surrounding the content inform the reader about the **type** of content.

An imperfect but reguarly called upon analogy for HTML is that it behaves like the bricks/cement/steel of a house. It works when you're trying to compare HTML to CSS and JS but in my opinion it doesn't do a good job of explaining how HTML interacts with your *content*. In reality, it's more like a family tree, with a single initial progenitor.

### HTML vs HTML5

#### HTML

Here's an example of a naïve implementation of a header with a set of links which serve as a website navigation.

*assets/Header_naive.html*

```html
<div>
    <div>
        <a href="/">Home page</a>
        <a href="/about-us">About us</a>
        <a href="/contact-us">Contact us</a>
    </div>
</div>
```

*What's a **div**?*

A *Division* is just a container element. It has almost no semantic qualities. It just holds other tags. It's probably the most common tag used on the web today.

*What's an **a**?*

An *Anchor* is a functional tag that when clicked will redirect the browser to either another document, or another location on the current document. We commonly refer to these as links.

#### HTML5

Here's the same header/navigation implemented in HTML5

*assets/Header_html5.html*

```html
<header>
    <nav>
        <a href="/">Home page</a>
        <a href="/about-us">About us</a>
        <a href="/contact-us">Contact us</a>
    </nav>
</header>
```

*Nav?*

Short for navigation. Tells the device reading the content that it's dealing with some links to content rather than actual content.

HTML5 added a bunch of fun tags for us to work with, and they actually do nothing for the majority of users. We could build an entire functioning website out of just one tag if we so desired.

There **are** good reasons for writing *semantic markup* or "markup that appropriately describes the content it holds", and they are:

* Accessibility
    * Some people will access your site in unusual ways, for example via a screen-reader tool which enables blind users to *hear* your website. If you write it semantically, that screen-reader can follow your document as easily as you might read an email or a word doc. If you don't it will have a really difficult time or not work at all. Semantic markup isn't really for *people*, it's for computers.
* SEO ranking
    * In another universe, the search engine gods care about the quality of your markup and will penalise you for doing a poor job. In our universe they actually don't particularly care, but we pretend that they do because search engine optimisation is a murky area, and doing things as well as possible is just a safe play. It also future proofs us for a potential timeline where Google suddenly decides to kill your ranking if you're inaccessible and lazy.
* Readability
    * Other developers might look at your HTML and if you use tags that help them understand what you're doing then they waste less time figuring it out.

If we go back to our family tree analogy for a moment, HTML5 improved our ability to label each leaf in the tree. Now as you follow the tree down you can clearly see where families appeared, and also what their job titles were and how they behaved towards one another.

### HTML in the wild

```html
<!-- DON'T CARE -->
<!DOCTYPE html>
<html>
    <head>
        <!-- DON'T CARE -->
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width,initial-scale=1.0">

        <!-- DO CARE -->
        <link rel="icon" href="/favicon.ico">
        <title>Trucks Dealer Review</title>
        <meta name="description" content="Read about our customers' experiences with our Trucks dealerships, or share your own!">
        <meta name="keywords" content="mercedes, mercedes trucks, review, reviews, form">
        <meta property="og:title" content="Trucks Dealer Review">
        <meta property="og:description" content="Read about our customers' experiences with our Trucks dealerships, or share your own!">
        <meta property="og:type" content="website">
        <meta property="og:image" content="<%= BASE_URL %>assets/images/header-customer.jpg">
    </head>

    <!-- CARE VERY DEEPLY ABOUT THIS BIT -->
    <body>
        <article>
            <h1>Hello world</h1>
        </article>
    </body>
</html>
```

If you open the assets folder in this file's directory you will find a file called Hello_world.html. Double click it to see the above HTML rendered in your default browser.
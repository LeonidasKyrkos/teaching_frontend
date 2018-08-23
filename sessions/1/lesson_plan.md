# HTML lunch and learn

## What is HTML

### Hypertext Markup Language

#### Hypertext

A software system allowing cross-referencing between sections of text and associated imagery.

#### Markup

*In computer text processing, a markup language is a system for annotating a document in a way that is syntactically distinguishable from the text.*

Annotated text

```
"The quick brown fox jumps over the lazy dog" is an English-language pangram—a sentence that contains all of the letters of the alphabet. It is commonly used for touch-typing practice, testing typewriters and computer keyboards, displaying examples of fonts, and other applications involving text where the use of all letters in the alphabet is desired.

^ this is a paragraph
```

Markup

```html
<p>Hello my name is Greg</p>
```

## What does HTML do?

### Structure

![house](assets/house_frame.jpg)

### Order

```html
<header>Header</header>
<article>Content</header>
<footer>Footer</footer>
```

### Semantics

HTML is tasked not just with holding the content, but also *describing* the content. It wants to be as meaningful as possible when read by people and software alike.

## Semantics and HTML5

Lexical semantics = study of the meaning of words
Semantic markup = application of meaningingful markers to content

#### Non-semantic HTML

```html
<body>
    <div>
        <a href="/">Home page</a>
        <a href="/about-us">About us</a>
        <a href="/contact-us">Contact us</a>
    </div>
    <div><!-- main content --></div>
    <div><!-- footer content --></div>
</body>
```

![unsemantic html](assets/HTML.png)


#### Semantic HTML5

```html
<body>
    <header>
        <img src="logo.png" />
        <nav>
            <a href="/">Home page</a>
            <a href="/about-us">About us</a>
            <a href="/contact-us">Contact us</a>
        </nav>
    </header>
    <article><!-- main content --></article>
    <footer><!-- footer content --></footer>
</body>
```

![semantic html](assets/SEMANTIC_HTML.png)

* HTML5 added new elements which makes it easier for us to describe our content.
* Rainbows without words for colours would be confusing, the same goes for html. It's hard for a robot to know that something is a list of navigation items if you don't have the word for navigation.

#### Benefits

* Accessibility
* SEO ranking
* Readability

## HTML in the wild

```html
<!-- DON'T CARE -->
<!DOCTYPE html>
<html>
    <head>
        <!-- DON'T CARE -->
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width,initial-scale=1.0">

        <!-- DO CARE A LITTLE BIT -->
        <link rel="icon" href="/favicon.ico">
        <title>Page title</title>
        <meta name="description" content="a description">
        <meta name="keywords" content="keywords, more keywords, more">
    </head>

    <!-- CARE VERY DEEPLY ABOUT THIS BIT -->
    <body>
        <article>
            <h1>Hello world</h1>
        </article>
    </body>
</html>
```
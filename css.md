
## CSS Styling

Try each of the following:
1. [Intro to CSS](#css)
2. [Selectors](#selectors)
  * [Basic Selectors](#basic-selectors)
3. [Styling](#styling)
  * [Color](#color)
  * [Background Color](#background-color)
  * [Text](#text)
  * [Whitespace](#whitespace)
    * [Padding](#padding)
    * [Margins](#margins)
  * [Shadows](#shadows)


## CSS

CSS stands for cascading stylesheets. It creates the rules that elements follow on a page. Since it's written in a separate language, we usually put it in an entirely separate file and connect it using `link` elements with an `href` attribute and the name of the file - in this case `master.css`.

In the HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" type="text/css" href="master.css">
  </head>
  <body>

  </body>
</html>
```

## Troubleshooting CSS

If your CSS isn't working, there's a lot you can test to surface some common errors:
* Does something simple, like `body {background-color:blue;}` work?
  * If not, try a hard refresh (`cmd` + `shift` + `r` on a mac, and `ctrl` + `shift` + `r` on a pc) - your computer may be caching old copies of the CSS to save bandwith and speed up performance, but that means you won't have the most recent version of your own code. A hard refresh will reload those linked resources even if you have very recent cached copies.
  * Also make sure your CSS is linked correctly - if the file name of the CSS doesn't match the `href` of the link element, the CSS will not be applied to this page.
* Did you forget a semicolon at the end of one of the properties? Even one missing semicolon can invalidate the rest of the ruleset and it will not be applied.
* Did you forget a closing bracket at the end of a selector? Do you accidentally have extra closing brackets somewhere? Even a single unmatched bracket can prevent the ENTIRE set of CSS rulesets from being applied to the HTML document.
* Are you using the period to select by class? Are you using the pound sign to select IDs? over half the CSS errors we debug fall into this category.
* Check your spelling of the selectors (and the matching IDs and classes).

## Selectors

In general, you can select elements by element, by class, or by ID.

All these selectors need both HTML ***and*** CSS, so there are two code snippets for each.

### Select Elements

Select all the paragraphs like this:

In the HTML:
```html
<p>This will be red.</p>
```

In the CSS:
```css
p {
  color: red;
}
```

### Select by IDs

Select one single element by giving it an ID and using a pound sign (a hashtag).

In the HTML:
```html
<p id="main-paragraph">This paragraph is the ONLY main paragraph on the page. It should be blue.</p>
```

In the CSS:
```css
#main-parargraph {
  color: blue;
}
```

### Select by Class

Select multiple elements that all need to behave the same way by assigning them classes. Then select them

In the HTML:
```html
<p class="special">Two of these paragraphs are special, and will have larger fonts.</p>
<p class="special light">This is another large one. We'll make the text 1.5x larger than normal using the rem measurement. This belongs to TWO classes: special and light</p>
<p>THIS paragraph needs to stay the same size.</p>
```

In the CSS:
```css
.special {
  font-size: 1.5rem;
}

.light {
  color: grey;
}
```

## Styling

All style properties declared in CSS go in between the curly braces of the elements (or classes, or ID) that they are meant to style.

All style properties take the form of `property-name: value;`. In other words, they all have four parts:
1. Property name (connected with hyphens)
2. Colon
3. Value OF that property (if it's a margin, how big is it? if it's a color, which one is it?)
4. Semicolon

**IF YOU LEAVE OFF ANY ONE THESE FOUR PARTS, YOUR STYLES WILL NOT RENDER.**

### Color
Sets the color of the text. There are several ways to do this.

CSS pre-defined color words:
```css
h1 {
  color: teal;
}
```

Hexadecimal (Hex) numbers:
```css
h2 {
  color: #B2DFDB;
}
```

RGB colors:
```css
h3 {
  color: rgb(128,203,196);
}
```

#### COLOR BEST PRACTICES:
* The pre-defined names are almost all abrasive and difficult to look at. Pick your own (gentler) colors instead.
* Colored text rarely works as intended in web design. The three best colors you can use are white (on dark backgrounds), black (on light backgrounds), and some gentler shades of grey.
* If you *are* going to use colored text, restrict that to very purposeful and specific uses, like buttons or headers.

### Background Color
Sets the color of the background of the element selected. Responds to all the same values as the `color` property.

Using pre-defined names:
```css
h1 {
  background-color: teal;
}
```

Using RGBA values (where a, alpha, represents how opaque or transparent a color is):
```css
div {
  background-color: rgba(0,0,0,0.2);
  /* The actual color is black (0 red, 0 green, 0 blue), but since it's only 20% opaque (and therefore 80% transparent), the color will render as a grey, and any color behind it will shine through.  */
}
```

#### BACKGROUND COLOR BEST PRACTICES:
* As before, the pre-defined names are pretty terrible as background colors. Pick your own gentler colors instead.
  * When picking colors, you usually need less saturation / vibrancy than you think. It's easier to make mistakes that make websites uglier when you're using bright, neon, or bold colors.  
* Limit the color accents to 1-3 colors. Less is absolutely more.
* Use background on parent elements (like a div used to group text) to make it clear that the child elements are all part of the same whole.

## Text

### Fonts & Font Size

The property for setting fonts is `font-family`.


#### Font - Built in to CSS

Many fonts will be built into a browser, and you can simply use them straightaway.
```css
h1 {
  font-family: "helvetica";
}
```

Use fallback values if you're not sure whether your users will have a certain font available.
```css
h1 {
  font-family: "Gill Sans", sans-serif;
  /* This means try to use Gill Sans, but if you can't find that, then just use the default sans-serif font.  */
}
```

#### Font - Imported from Google Fonts.
https://fonts.google.com/

```CSS
/* load in the font from google fonts at the top of the stylesheet */
@import url('https://fonts.googleapis.com/css?family=Economica');

li {
  font-family: 'Economica', sans-serif;
  /* Use the font (with a fallback) in the elements you want to style. */
}
```

#### Font Size - Fixed Value
```css
li {
  font-size: 40px;
}
```

#### Font Size - Relative Value
```css
h1 {
  font-size: 3rem;
  /* This means 3x as big as normal */
}
```

#### Font Weight
Determines how bold (or not) text is. Can take any multiple of 100 (thinnest) up to 900 (boldest).
```css
li {
  font-weight: 900;
}
```

NOTE: Not all fonts have all 9 versions available, so most browsers will just choose the nearest equivalent.

#### Line Height
Determines how tall each line of text is (to simulate double, single, or multi-line spacing).

#### FONT BEST PRACTICES:
* You will be most drawn to decorative and cursive fonts, but they often impede readability. Notice that Apple, Spotify, Google, and Amazon all avoid using any of the cursive or pseudo-cursive fonts on their pages - they opt for crisp, clean, sans-serif fonts instead.
* Make fonts larger than you might think they need to be. This helps with readability (and keeps your pages from looking too busy).
* Use font size to signal how important content is - huge text will always be read first.
* Adding line height makes text easier to read, so apply additional line height to anything over a sentence long.
* Use font weight to contrast thick titles with think subtitles or body text to have a striking effect while still only using one font.


## Whitespace
Whitespace (which is not necessarily white) refers to the spacing between elements. Almost all well-designed websites have tons of it, which is how they direct your attention to the desired items.

### Padding
CSS `padding` is space between the edge of the element and the content inside, whereas `margin` is the space between separate elements. Here's what that looks like:

![padding](https://raw.githubusercontent.com/upperlinecode/upperline-images/master/images/padding.png)

Here's the syntax to declare padding:

```css
h1 {
  padding-top: 20px;
  /* Only pads the top of the element. */
}

li {
  padding: 5px;
  /* Pads all four sides of the element. */
}
```

### Margins
CSS `margin` is the space between separate elements. Here's an example of how `padding` and `margin` interact.

![margin](https://raw.githubusercontent.com/upperlinecode/upperline-images/master/images/margin.png)

Here's the syntax to declare margin:

```css
h1 {
  margin: 15px;
  /* Adds margin to all four sides of the element. */
}

li {
  margin-left: 30px;
  /* Only adds margin on the left side of the element. */
}
```

#### WHITESPACE BEST PRACTICES:
* If an element has a background color (or border), it will almost always need padding too - otherwise the content will appear cramped and the element itself will seem small.
* If there is no background color, almost every element will need margins of some size added to keep it from appearing too close to its neighbors.
* When in doubt, err on the side of adding too much whitespace - it's almost never too much.

### Shadows

#### Text Shadow
Use the `text-shadow` property to add a shadow to the text on a page.

Use four values: `text-shadow: offsetX offsetY blur color;`
To get a crisp shadow, use 0 for the blur value.

```css
h1 {
  text-shadow: 2px 2px 0px black;
}
```

#### Box Shadow
Use the `box-shadow` property to add a shadow to the entire rectangular area of an element.

Use four values: `box-shadow: offsetX offsetY blur color;`
To get a crisp shadow, use 0 for the blur value.

```css
h2 {
  box-shadow: 10px 10px 0px rgba(0,0,0,0.3);
}
```

#### SHADOW BEST PRACTICES:
* Text shadow is really only useful when there isn't enough contrast between text and its background, and shadow makes it more readable.
  * In these cases the smarter fix is often to change the color of the text or the background instead.
* Box shadow is used when trying to make digital items resemble real items (like cards or paper) from the material world, because it simulates depth. Only use box shadow if it's important that an item appear to be hovering above its neighbors.
  * Google, which generally adheres to Material Design principles, makes use of box shadow all the time.
  * Apple and Spotify edge-to-edge flat design, so their content is less likely to use box shadow.

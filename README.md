# Front-end Reference

## Sequence

1. [HTML](#html)
    * [Core HTML](#core-html)
    * [Auxiliary HTML](#auxiliary-html)
2. [CSS](#css)
    * [Style](#style)
    * [Grid](#grid)
    * [Fonts](#fonts)
    * [Troubleshooting CSS](#troubleshooting-css)
3. [JavaScript](#javascript)
    * [Console](#console)
    * [Selecting Elements](#selecting-elements)
    * [Event Listeners](#event-listeners)
    * [Class List](#class-list)
    * [Style](#style)
    * [Inner HTML](#inner-html)

## HTML

HTML stands for hypertext markup language. It tells WHAT will be on the page (though without CSS, it will just look pretty basic).

### Core HTML

#### Skeleton code

We call the core elements of an html document the skeleton code. Most text editors add it in as a snippet the moment you type "html".

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
  </head>
  <body>

  </body>
</html>
```

Key thoughts:
* EVERYTHING is in between the two **html** tags.
* The **body** begins right after the **head** ends.
* Elements that appear on the page will be between the **body** tags.
* Elements that do not appear on the page will (usually) be in between the two **head** tags.

#### Header

There are six built-in header sizes.

```html
<h1>Biggest</h1>
<h2>Second biggest</h2>
<h3>Third biggest</h3>
<h4>Fourth biggest</h4>
<h5>Okay, not so big by now</h5>
<h6>This one's actually pretty small</h6>
```

#### Paragraph

The `p` elements define and separate paragraphs

```html
<p>This is a paragraph. It's defined by opening and closing p-tags. You can make a single paragraph as large or as small as you care to. Once you close it, the paragraph will be over.</p>
<p>A second paragraph needs to be defined by a new opening p-tag, and closed with a corresponding p-tag.</p>
```

#### Links (anchors)

The `a` elements (anchors) define clickable "links". The `href` attribute determines where the link will direct you. The text between the opening and closing a-tags is what will be underlined and clickable.

```html
<a href="https://www.google.com/">Click here to visit Google!</a>
```

#### Images

###### An image hosted online

The `img` elements allow you to add images to the html page. You need to give an image a source using the `src` attribute. The `alt` text will only show up if the image doesn't load for some reason.

```html
<img src="http://doughnutkitten.com/PNGs/2017/1-Doughnut-Kitten-by-Tania-Hennessy.png" alt="The Donut Kitten didn't load!"/>
```

There's no closing tag, but there is a slash in the end of the `img` tag. It's what's called a self-closing tag.

###### An image housed in your project

That first example linked to an image hosted on someone else's site. If you put an image *in your project folder*, then you can use a shorter (local) source. instead of a URL that starts with "http" or "https", it'll just be a relative filepath (where the image is in relation to the html).

Alt text is generally optional; the image will load just as well without it.

```html
<img src="profilepic.jpeg" alt=""/>
```

#### Line breaks

Line breaks are simple. They split an element into two lines. Don't overuse them.

```html
<h3>This Header<br>is broken into two lines</h3>
```

#### Divs

Divs are just containers. Unless you give them a background color, they're invisible, but when you move or style a div, you also move or style everything inside of it.

Because divs are usually styled, you'll usually add ids or classes to them so that you can select them in CSS.

```html
<div id="firstdiv">
  <p>This div has a paragraph in it, and that's all.</p>
</div>

<div id="seconddiv">
  <h1>This div has two elements inside it. The first is this header.</h1>
  <p>It also has this paragraph.</p>
</div>
```

### Auxiliary HTML

These additional pieces of HTML are helpful, but not necessary when you're just getting started.

#### Unordered Lists

An unordered list is a bulleted list. Each `li` (list item) is a bullet, and the whole list is bundled together with the parent `ul` tags.

```html
<ul>
  <li>Sorcerer's Stone</li>
  <li>Chamber of Secrets</li>
  <li>Prisoner of Azkaban</li>
  <li>Goblet of Fire</li>
  <li>Order of the Phoenix</li>
  <li>Half-Blood Prince</li>
  <li>Deathly Hallows</li>
</ul>
```

*You can also use an `<ol>` tag to number the items, but that's increasingly less common in modern html*

#### Input

Input elements allow the user to enter their own information on a page. All search bars, dropdown menus, and calendars you see online are different types of input elements.
* The `type` attribute defines what kind of information you'll let the user enter. Some of the most important values for the type attribute are **text, number,** and **date**.
* The `name` attribute is a way for you, the developer, to remember what specific info you asked for in this field.
* The `value` attribute is what will already be in the input when the page loads. It's also called the "default text" and a lot of developers will write prompts in the value field, like "Type your name here".
    * It's worth knowing that the value you assign has to be the same TYPE of info as input type, so if an input has an attribute of `type="number"`, then you can't prompt the user with value text - you could only use a number. You'll need a label element (and we'll get to that in a second) to show the user what you want them to do in a number or date field.

```html
<input type="text" name="name" value="Type your name here">
<input type="text" name="school" value="What school do you go to?">
<input type="number" name="gpa" value="">
<input type="date" name="graddate" value="">
```

#### Forms

Forms are intimidating at first. The essentially bundle together a series of inputs and labels for those inputs with the all-important `submit` button.

```html
<form>
  <label for="motto">
    Enter your personal motto:<input type="text" name="motto" value="">
  </label>
  <label for="age">
    Enter your age:<input type="number" name="" value="">
  </label>
  <input type="submit" value="Click here to submit!">
</form>
```

*It's worth knowing that forms are generally used in the context of web applications (not just web pages), so this will likely throw some errors. If you're primarily working in front-end, it might make sense to remove the submit button and listen for input changes instead.*

## CSS

CSS stands for cascading stylesheets. It creates the rules that elements follow on a page. Since it's written in a separate language, we usually put it in an entirely separate file and connect it using `link` elements with an `href` attribute.

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

### Selectors

In general, you can select elements by element, by class, or by ID.

All these selectors need both HTML ***and*** CSS, so there are two code snippets for each.

#### Select Elements

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

#### Select by IDs

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

#### Select by Class

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

### Style

All style properties declared in CSS go in between the curly braces of the elements (or classes, or ID) that they are meant to style.

All style properties take the form of `property-name: value;`. In other words, they all have four parts:
1. Property name (connected with hyphens)
2. Colon
3. Value OF that property (if it's a margin, how big is it? if it's a color, which one is it?)
4. Semicolon

**IF YOU LEAVE OFF ANY ONE THESE FOUR PARTS, YOUR STYLES WILL NOT RENDER.**

#### Color
Color changes the text color.

```css
p {
  color: blue;
}
```

#### Background-color

```css
p {
  color: tomato;
}
```

#### Font-size

Use the `rem` measurement to define relative sizing. This keeps things like headers large, paragraphs small, but lets you make the whole impression bigger.

```css
p {
  font-size: 2rem;
}
```

#### Font-family

Change the font, but give a fallback generic font type (serif, sans-serif) in case the user doesn't HAVE that font.

```css
p {
  font-family: "Helvetica", sans-serif;
}
```

#### Font-weight

Use multiples of 100. 400 is usually normal. 100 is super light. 700 or 900 is usually super dark.

```css
p {
  font-weight: 100;
}
```

Be aware that not all fonts have these weights built-in.

#### Border

Border properties take three arguments: size, weight, and color. You can be more detailed, but honestly, borders don't get used a lot in finished projects.

```css
p {
  border: 3px solid black;
}
```

#### Padding

Padding pushes content in from the edge of its container. Padding can be set for all for four sides, or just for individual sides.

```css
p {
  padding: 10px;
}

h1 {
  padding-left: 20px;
}
```

#### Box Shadow

Box Shadow takes four arguments: horizontal offset, vertical offset, blur, color.

```css
div {
  box-shadow: 2px 2px 0px grey
}
```

*For example, that box shadow is 2 pixels down, 2 pixels to the right, not blurred at all, and grey in color.*

### Grid

Creating a grid requires a parent/container element and child elements. Think this through in steps:
1. Sketch out your layout.
2. Figure out how many divs there are in your layout.
3. Code out the parent div and as many child divs as you'll need to achieve the layout.
4. Code out the grid-template-coulmns (and the grid-template-rows if necessary).
5. Tell any divs that need to span multiple elements to do so.

In the HTML
```html
<div class="parent">

    <div id="one" class="child">
      <h1>My first div</h1>
    </div>

    <div id="two" class="child">
      <h1>My second div</h1>
    </div>

    <div id="three" class="child">
      <h1>My third div</h1>
    </div>

    <div id="four" class="child">
      <h1>My fourth div</h1>
    </div>

</div>
```

IN THE CSS:
```css
#parent {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: 1fr 3fr 1fr;
}

#one {
  grid-column: span 3;
}
```

##### Grid Troubleshooting guide
* Give the child elements background-color or border properties so you can SEE the grid.
* Child elements use the words column and row (singular); parent elements use the plural template-columns.

### Fonts

*coming soon*

### Troubleshooting CSS

If your CSS isn't working, here's a lot you can test:
* Does something simple, like `body {background-color:blue;}` work?
* Did you forget a semicolon at the end of one of the properties?
* Did you forget a closing bracket at the end of a selector? Do you accidentally have extra closing brackets somewhere?
* Are you using the period to select classes or the pound sign to select IDs?
* Check your spelling of the selectors (and the matching IDs and classes).

## JavaScript

Link your JavaScript at the END of your document, right above the closing `</body>` tag.

```html
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <script type="text/javascript" src="coolscript.js"></script>
  </body>
</html>
```

### Console

Debugging code - making sure it's running when you expect it to - requires printing information to the console, and checking for it in the console.

```javascript
console.log("script running!")
```

It's a good idea to put this at the top of JavaScript files to see if they're connected correctly.

### Selecting Elements

Get an element using the same syntax you use in CSS, and store it in a variable you can use later using the `let` command.

Select by element:
```javascript
let profilepic = document.querySelector("img")
```

Or select by id:
```javascript
let profilepic = document.querySelector("#bestpic")
```

When you're still learning, it's helpful to make sure you got the element you were trying to select by logging it to the console.

```javascript
console.log(profilepic)
```

### Event Listeners

Add an event listener to an element and use a codeblock to respond to that event.

```javascript
profilepic.addEventListener("click", e => {
  // Write whatever code you want in the codeblock.
  // I use comments like this to keep track of my code.
  // I also use debug statements like this to make sure the event is firing when I think it should.
  console.log("Profile picture clicked!")
})
```

Here are some events to listen for:
* click
* dblclick
* mousemove
* mouseover
* mouseout

#### Window-level events

You can also add an event to the entire window instead of a selected element.

```javascript
window.addEventListener("mousemove", e => {
  console.log("mouse moved!")
})
```

The best window-level events to listen for:
* mousemove
* scroll
* keydown

### Class List

You can access a classList to .add(), .remove(), or .toggle() a class.

```javascript
profilepic.classList.add("active")
```

**ONLY use this code inside an event listener's codeblock (or other function), that way the action can be triggered by the user.**

### Style

Accessing the style of an element is awesome, because it basically lets you use CSS in your JavaScript.

Move the item 200 pixels from the top.
```javascript
profilepic.style.top = "200px"
```

Make the item have a specific width.
```javascript
profilepic.style.width = "400px"
```

Recolor the item's text.
```javascript
profilepic.style.color = "blue"
```

Recolor the background color
```javascript
profilepic.style.backgroundColor = "tomato"
```

### Inner HTML

You can also change the contents of an element using the innerHTML property.

```html
<div id="div5">Click on me to reveal the secret number!</div>
```

```javascript
// Get the element
let myfifthdiv = document.querySelector("#div5")

// Console log it, just to make sure.
console.log(myfifthdiv)

// Add an event listener, and reset the inner HTML by adding an entire HTML element.
myfifthdiv.addEventListener("click", e => {
  myfifthdiv.innerHTML = `<h1>The secret number is 17!</h1>`
})
```

A few thoughts:
* This code REPLACES the inner HTML by using an `=` (assigment operator). You can ADD to the inner HTML (instead of replacing it) if you used the `+=` (increment operator) instead.
* *more to come*

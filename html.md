# HTML

HTML stands for hypertext markup language. It tells WHAT will be on the page, not how it will look. without CSS, it will primarily render as basic text.

1. [Core HTML](#core-html)
    * [The HTML Shell](#the-html-shell)
    * [Header](#header)
    * [Paragraph](#paragraph)
    * [Links (anchors)](#a)
    * [Images](#images)
    * [Line breaks](#line-breaks)
    * [Divs](#divs)
2. [Auxiliary HTML](#auxiliary-html)
    * [Unordered Lists](#unordered-listes)
    * [Input](#input)
    * [Forms](#forms)

### Core HTML

#### The HTML Shell

We call the core elements of an html document the HTML shell. Most text editors add it in as a snippet the moment you type "html" and then hit tab.

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

NOTE: There's no closing tag, but there is a slash in the end of the `img` tag. It's what's called a self-closing tag. Self-closing tags make it easier to enforce the convention that "every element must be closed" - there aren't many absolutes in programming, but with the inclusion of self-closing tags, you can ensure that every element you open is closed at some point.

Other self-closing tags include:
* `<meta />` - used in a document's `<head>` to identify and describe contents of the page for search engines and other services.
* `<link />` - used in a document's `<head>` to connect stylesheets.
* `<br />` - used to add a blank line of space. This element is less and less common in modern web development. Generally, if you need a line break inside a paragraph, it's better practice to split the content into multiple elements and control their separation more precisely using [CSS whitespace properties](css.md#whitespace)
* `<hr />` - used to insert a visible horizontal line on a page.

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

*It's worth knowing that forms are generally used in the context of web applications (not just web pages), so this will likely throw some errors. If you're primarily working in front-end, it might make sense to use only the label and input elements, and remove the submit button and the `<form>` parent element, and just listen for input changes instead.*

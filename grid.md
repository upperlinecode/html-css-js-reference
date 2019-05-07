TODO - expand this with screenshots, examples, and the corresponding CSS (which isn't here yet)

## Grid

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

/* Size an element by telling it how wide to be.
In this case, it will span across three columns. */
#one {
  grid-column: span 3;
}

/* Size an element by telling it where to start and end.
In this case, it will start at gridline 1 and end at gridline 4 */
#two {
  grid-column: 1/4;
}
```


#### Grid Troubleshooting guide
* Give the child elements background-color or border properties so you can SEE the grid.
* Child elements use the words column and row (singular); parent elements use the plural template-columns.

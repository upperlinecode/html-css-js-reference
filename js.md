# JavaScript

JavaScript is the language that brings the web to life. It's responsible for almost all the animations and instantaneous interactions you experience when visiting a website, as well as a considerable amount of the back-end work of building out large-scale applications like Facebook.

1. [DOM Manipulation](#dom-manipulation)
    * [Connecting Scripts](#connecting-scripts)
    * [Console](#console)
    * [Selecting Elements](#selecting-elements)
    * [Event Listeners](#event-listeners)
    * [Class List](#class-list)
    * [Style](#style)
    * [Inner HTML](#inner-html)
2. [Pure JavaScript](#pure-javascript)
    * [Variables and Types](#variables-and-types)
    * [Functions](#functions)
    * [Conditionals](#conditionals)
    * [Arrays](#arrays)
    * [Objects](#objects)
    * [Loops](#loops)

## DOM Manipulation

JavaScript can be used in many ways, but one of the most powerful applications is to manipulate the DOM (the Document-Object-Model).

### Connecting Scripts

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

Only use this code inside an event listener's codeblock (or other function), that way the action can be triggered by the user.

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

This code as written REPLACES the inner HTML by using an `=` (assigment operator). You can ADD to the inner HTML (instead of replacing it) if you used the `+=` (increment operator) instead.

## Pure JavaScript

### Variables and Types

#### Variables

JavaScript, like most languages, allows for the storage of information in variables using the `=` assignment operator. Use `let` for hard-coded strings and numbers that you intend to change. Use `const` for DOM elements information you intend to leave unchanged.

```javascript
// Assign the string "Raphael" to the variable called name.
let name = "Raphael"
// Assign the number 16 to the variable called age.
let age = 16

// Assign a value to pi, which will not be changed.
const pi = 3.14
```

Variables declared with `let` can be changed using the `=` reassignment operator, which is the same as the assignment operator.

```javascript
// Assign the number 16 to the variable called age.
let age = 16
// Reassign the age because this user had a birthday!
age = 17
```

Reassignment can also be done with variable expressions.
```javascript
// Assign the number 16 to the variable called age.
let age = 16
// Reassign age. The age is NOW equal to the PREVIOUS value of age (16) plus 1.
age = age + 1
```

Reassignment can be done with a shorthand operator to *increment* a value.
```javascript
// Assign the number 16 to the variable called age.
let age = 30
// Reassign age by incrementing it by 1. This is shorthand for `age = age + 1`
age += 1
```

Bear in mind that variables created with **const** are constants, and cannot be changed.
```javascript
// Assign a value to pi, which will not be changed.
const pi = 3.14
// This next line WILL THROW AN ERROR. Constants cannot be reassigned.
 pi = 3.14159265
```

Older JavaScript conventions will also declare variables with the keyword `var`, but this is falling out of style, and not recommended. **When you see examples with `var` online, consider replacing `var` with `let`.**

#### Types

There are numerous types of data you might see in JavaScript, but the most important fall into a few major categories.

##### Numbers
Numbers are exactly what they sound like. Some programming languages subdivide numbers into categories (like integers and non-integers called "floats"), but JavaScript keeps them all in one category.
```javascript
// You can store numbers in variables or constants.
let x = 42
let y = 7
const z = 990

// You can also use number literals, but without storing them in variables, they cannot be referenced later in the code.
13
4
1337
```

##### Strings
Strings are collections of characters - we use strings when we need words or sentences to appear in our programs.
```javascript
// You can store numbers in variables or constants.
let name1 = "Julian"
let name2 = "Shea"
const name3 = "Alejandra"

// You can also use string literals, but without storing them in variables, they cannot be referenced later in the code. String literals by themselves are not generally useful.
"Aaron"
"Erin"
```

##### Boolean Values
Boolean values are binary or true-false values. They can have no other value.
```javascript
let hungry = true
let thirsty = false
```

### Functions

#### Named Function Syntax

Functions are named, repeatable blocks of code, and they aren't usually modified after they are defined, so it's generally best to store then using `const`.

##### Basic JavaScript Functions
Here's an example of a function that greets a known user. It's called `greetKnown()`
```javascript
// Function definition - this only needs to be done once per function.
// It should be noted that just defining a function will not actually run it.
const greetKnown = (user) => {
  console.log(`Hello, ${user}! Welcome to the console.`)
}

// Function call - this can be done any number of times.
greetKnown("Diana")
greetKnown("Marquis")
```

Let's break this down:

Most programming languages associate functions to **parentheses** `()`, so yes, `console.log()`, `document.QuerySelector()`, and `element.classList.add()` are all functions - they're just pre-built. In all of these examples, and in the one above, the parentheses hold a string as an **argument**, but you can define functions that take multiple arguments, that take a numerical or other non-string argument, or that take no arguments at all.

The **ES6 Arrow** `=>` is a new way of defining functions that cut out the word "function" entirely, but these arrow functions still operate just like normal functions.

The braces or curly brackets `{}` designate the start and end of the function - this is the code that will be run whenever the function is called.

##### Functions Without Arguments
Functions can also be designed to take zero arguments. The syntax is similar, except that the `()` are empty in both the definition and the call:

```javascript
// Function definition
const greetUnknown = () => {
  console.log(`Hello! Welcome to the console.`)
}

// Function call - this can be done any number of times.
greetUnknown()
```

Note that even if a function does not require any arguments, parentheses are required to call the function.

#### Calling and Referencing Named Functions

Function definitions are useless on their own - they have to also be run. Running, executing, or otherwise "doing" the contents of a function is handled with a **function call**. Calling a function is done by writing the function name with parentheses after it. The moment a browser reads a function call, that function will be run.

If you write the name of a function *without* parentheses, that will not run the function - the name of a function without parentheses is just a **reference** to the function.

```javascript
// Function call - this will be executed as soon as it is run.
greetUnknown()

// Function reference - this will not be executed.
greetUnknown
```

#### Functions with Inputs and Outputs

Functions can also be designed to return data to the rest of the program so that it can be stored in variables or otherwise further processed.

```javascript
// Function definition
const nameLength = (name) => {
  if (name.length <= 5) {
    return "short"
  } else if (name.length <= 10) {
    return "medium"
  } else {
    return "long"
  }
}

// Function calls
let adjective1 = nameLength("Kim")
let adjective2 = nameLength("John Jacob Jingleheimerschimdt")
```

##### Using Function Return Values
Functions can also be designed to return numerical data, which is usually stored in variables.

Consider the following two function definitions:
```javascript
// Function definition
const square = (x) => {
  return x * x
}
// Function definition
const half = (x) => {
  return x / 2
}
```

Return values can be used in a variety of ways. Here are some of the most common:
##### Return Use 1: Store the Result for later use
```javascript
// Function call example 1: storing the return value in variables
let firstSquare = square(3) // This should store the number 9.
let secondSquare = square(5) // this should store the number 25.
...
console.log(firstSquare) // this should log out the number 9.
```

##### Return Use 2: Use the Result Inline, Immediately
```javascript
// Function call example 2: using the return value in other code
let x = 12

if (square(x) > 99) {
  console.log("Wow! The square of that number is large!")
}
```

##### Return Use 3: Use the Result For *Another* Function
```javascript
// Function call example 3: using the return value of one function as the argument to another function
let coolNumber = half(square(10)) // This should store 50.
// First it takes 10 and squares it (100), and then it takes THAT result and halves it.
```

### Conditionals

Conditional statements in JavaScript are written with the following syntax:
```javascript
if (condition1) {
  // Code for if condition1 is true
} else if (condition2) {
  // Code for if condition2 is true (after condition 1 fails)
} else {
  // Code for if none of the above conditions are true
}
```

Conditional statements are confusing at first, but very syntax heavy, so 90% of errors with JS conditionals are punctuation issues. Make sure your code is indented properly, that every condition is enclosed in parentheses, and that every opening `{` has a corresponding closing `}`.

#### Conditional Operators
**Basic operators** compare two values.
* `a === b` checks to see if two values are *strictly* the same.
* `a == b` checks to see if two values are the same (even if the types mismatch).
* `a > b` checks to see if a is greater than b.
* `a < b` checks to see if a is less than b.
* `a >= b` checks to see if a is greater than or equal to b.
* `a <= b` checks to see if a is less than or equal to b.
* `a != b` checks to see if a is *not* equal to b.

NOTE that `=`, the assignment/reassignment operator is **NOT** a conditional operator. It MAKES statements true instead of checking to see if they are. Most often, if the `=` assignment operator is included in conditions, that's going to cause bugs.

**Compound / logical operators** compare two boolean values, so they can be used to write complex conditions.
* `a || b` checks to see if either a **OR** b is true.
* `a && b` checks to see if both a **and** b are true.

#### Conditionals Example
Here's what a compound conditional looks like in action.
```javascript
if (age < 65 && age > 17) {
  console.log("We're sorry, but you don't seem to be eligible for either our senior or our child discounts.")
} else if (age < 0 || age > 109) {
  console.log("We're sorry, but you appear to by lying about your age - please try again.")
} else if (age >= 65) {
  console.log("Please enjoy a 10% senior discount.")
} else {
  console.log("Kids eat free!")
}
```

### Arrays

Multiple items can be stored in a single variable by assigning an array of items to that variable.

```javascript
let favoriteFoods = ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi"]
```

#### Accessing Elements in an Array
Once the array has been assigned, individual items in the array can be accessed using the array's name, square brackets, and the specific item's index - be aware that the first item has an index of 0, so the second has an index of 1, and so on.

```javascript
favoriteFoods[1] // Will return the string "Okonomiyaki"
```

#### Reassigning Elements in an Array
Values in an array can be reassigned in a way very similar to variable reassignment.

```javascript
// Change the second value from "Okonomiyaki" to "Ramen"
favoriteFoods[1] = "Ramen"
// Console.log the array to confirm the change went through.
console.log(favoriteFoods)
// Should print: ["Pizza", "Ramen", "Elote", "Mangos", "Bulgogi"]
```

#### Adding Elements to an Array
Instead of replacing an element from an array, you can just add it to the end.
```javascript
let favoriteFoods = ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi"]

// Add "Spaghetti" to the Array
favoriteFoods.push("Spaghetti")

console.log(favoriteFoods)
// Should print: ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi", "Spaghetti"]
```

#### Additional Array Methods
Arrays have more numerous capabilities than can be mentioned here. To learn more, you'll want to consult [documentation]() on array methods.

Bear in mind that some methods like `.push()` modify the original array, while other array methods like `.reverse()` make a NEW array - in this case, with the items in exact reverse order.

Methods that mutate/modify the original array don't need to be resaved. But methods that return new arrays based on the original should be saved if you plan to do additional work on them afterwards.

```javascript
let favoriteFoods = ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi"]

// Add "Spaghetti" to the Array
favoriteFoods.push("Spaghetti")
console.log(favoriteFoods)
// Should print: ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi", "Spaghetti"]

// Reverse the Array
let backwardsFoods = favoriteFoods.push("Spaghetti")

console.log(favoriteFoods)
// Should print: ["Pizza", "Okonomiyaki", "Elote", "Mangos", "Bulgogi", "Spaghetti"]
// The original is unchanged! Even though it was reversed!
console.log(backwardsFoods)
// Should print: ["Spaghetti", "Bulgogi", "Mangos", "Elote", "Okonomiyaki", "Pizza"]
// If you hadn't stored these results, you'd be unable to use your reversed array.
```

### Objects

Information that needs to be organized by name rather than be order is often best stored in a JavaScript Object (sometimes called JSON format, which is short for "JavaScript Object Notation").

Objects are stored not as single entries, but as **key-value pairs**. The **key** is the NAME of the information, and the **value** is the information itself.

#### 

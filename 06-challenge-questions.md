# Challenge Questions
## Question #1
* You've learned that a typical for loop statement begins with three parts, which can be called the initialization, the condition, and the final expression, such as:

```js
for (let i = 0; i < 10; i++) {
    // do stuff
}
```

* Are any of these three parts optional, or are they all required? Explain.

* [all 3 parts are optional](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)

## Question #2
* Name another array method that has not been covered and briefly explain what it does
    - The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array
* Provide sample code:

```js
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

## Question #3
* Name another string method that has not been covered and briefly explain what it does
    - `replace()`
        + replaces a specified value with another value in a string
* Provide sample code

```js
str = "Please visit Microsoft!";
var n = str.replace("Microsoft", "W3Schools");
```

## Question #4
* You've learned about an escape sequence` \n` that creates a newline in a string
    - [JavaScript escape sequences](https://mathiasbynens.be/notes/javascript-escapes)
* Provide another example of an escape sequence, or escape characters, and explain what it does

```
\b: backspace (U+0008 BACKSPACE)
\f: form feed (U+000C FORM FEED)
\n: line feed (U+000A LINE FEED)
\r: carriage return (U+000D CARRIAGE RETURN)
\t: horizontal tab (U+0009 CHARACTER TABULATION)
\v: vertical tab (U+000B LINE TABULATION)
\0: null character (U+0000 NULL) (only if the next character is not a decimal digit; else it’s an octal escape sequence)
\': single quote (U+0027 APOSTROPHE)
\": double quote (U+0022 QUOTATION MARK)
\\: backslash (U+005C REVERSE SOLIDUS)
```

## Question #5
* You've learned that you can access the attributes of HTML elements using syntax such as: `node.style.background` and `node.hidden`
* List at least two other HTML element attributes that you can access as JavaScript element node properties, and include sample code to demonstrate how you would use them in JavaScript

1. `var x = document.getElementById("myBtn").textContent;`
2. `document.getElementById("myDIV").classList.add("mystyle");`

* See [this reference on W3Schools](https://www.w3schools.com/jsref/dom_obj_all.asp) and [this reference on MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement#properties)
* **Note:** methods end with `()` and properties do not

## Question #6
* What is the return value from a call to `node.removeChild()`?
* What can you do with it?
* Show sample code to demonstrate how you might store the return value in a variable then use it

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>Hello</h1>
    <div id="top">
      <div>
        <p>I will not be removed</p>
      </div>
      <div id="nested">I am nested</div>
    </div>
    <script charset="utf-8">
      let divEl = document.getElementById("top");
      let divElNested = document.getElementById("nested");
      let throwawayNode = divEl.removeChild(divElNested);
    </script>
  </body>
</html>
```

## Question #7
* What happens if you try to use the `node.insertBefore()` method to insert a node that already exists in the document, i.e. is already attached to the DOM?
    - The `Node.insertBefore()` method inserts a node before a reference node as a child of a specified parent node
    - If the given node already exists in the document, insertBefore() moves it from its current position to the new position. (That is, it will automatically be removed from its existing parent before appending it to the specified new parent.)
    - This means that a node cannot be in two locations of the document simultaneously.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Challenge Question 7 answer</title>
  </head>
  <body>
    <h1>insertBefore</h1>
    <div id="parentElement">
      <span id="childElement">foo bar</span>
    </div>

    <footer>
      <p>footer</p>
    </footer>
    <script>
      // Create the new node to insert
      let newNode = document.createElement("span");

      // grab the footer test
      let footer = document.querySelector("footer");
      // Get a reference to the parent node
      let parentDiv = document.getElementById("childElement").parentNode;

      // Begin test case [ 1 ] : Existing childElement (all works correctly)
      let sp2 = document.getElementById("childElement");
      // parentDiv.insertBefore(newNode, sp2);
      parentDiv.insertBefore(footer, sp2);
    </script>
  </body>
</html>
```

## Question #8
* Research JavaScript events such as `onclick/click`, `onmouseover/mouseover` and find one that has not been discussed during this course
* Give a brief explanation of what it does
    - The focus event fires when an element has received focus
    - The main difference between this event and focusin is that focusin bubbles while focus does not
    - The opposite of focus is blur
    - [mdn focus docs](https://developer.mozilla.org/en-US/docs/Web/API/Element/focus_event)

```html
<form id="form">
  <input type="text" placeholder="text input">
  <input type="password" placeholder="password">
</form>
```

```js
const password = document.querySelector('input[type="password"]');

password.addEventListener('focus', (event) => {
  event.target.style.background = 'pink';
});

password.addEventListener('blur', (event) => {
  event.target.style.background = '';
});
```

## Question #9
* You've seen how the array method `sort()` can be used to sort an array of strings alphabetically
* What is its behavior when used to sort an array of numbers? For example, what would this array look like once sorted?: `[1, 13, 1000, 29, 255]`
    - [stackoverflow answer](https://stackoverflow.com/questions/1063007/how-to-sort-an-array-of-integers-correctly)
    - By default, the sort method sorts elements alphabetically. To sort numerically just add a new method which handles numeric sorts




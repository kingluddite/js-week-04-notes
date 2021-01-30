# DOM basics
## What is the DOM?
* Document Object Model (DOM)
* Provides an interface betwen JavaScript and HTML
* When a browser loads an HTML document, it will internally represent it with the DOM

### View Source vs Inspect Element
* Inspect Element is showing you the DOM

## Representing HTML in the DOM

`index.html`

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM Representation</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>Welcome to my web site</p>
  </body>
</html>
```

## In browser's internal memory it represents web page like this:
![web page visual dom](https://i.imgur.com/9Y92XBU.png)

* In data science above is called a tree structure or tree graph
    - Think of it as an upside down tree with branches
    - [Chrome Extension: HTML Tree Generator](https://chrome.google.com/webstore/detail/html-tree-generator/dlbbmhhaadfnbbdnjalilhdakfmiffeg/related?hl=en-US)
    - Each point on the graph is called a `node`
    - The root starts with a single `node`
        + In HTML this is `<html>` and is known as the `root node`

![root node and head and body branches](https://i.imgur.com/VGwF09Q.png)

* Think of tree like a family tree
    - You have a parent node
    - A child node
    - A sibling node

### Viewed in browser
![web page rendered in browser](https://i.imgur.com/qZEPynj.png)

## Text nodes
* Text is also nodes and known as "text nodes"
* [example of text nodes](https://javascript.info/dom-nodes#an-example-of-the-dom)
* [view DOM tree chrome extension](https://chrome.google.com/webstore/detail/dom-node-tree-viewer/jbplakkefflidgnjhckoahendgekokfc/related?hl=en)

`table-dom-nodes.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <table>
      <tbody>
        <tr>
          <td>1</td>
          <td>2</td>
          <td>3</td>
        </tr>
        <tr>
          <td>A</td>
          <td>B</td>
          <td>C</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

* View with Dom text nodes Chrome extension
* **note** How attributes are part of the node (they are not given their own node)
* text nodes can be siblings to tag nodes
    - **note** But text nodes never have their own children
    - **note** void elements like `<br />` have no children nodes either
        + void nodes can not have any content
        + void notes can be siblings or children but can't be a parent node

## Whitespace nodes
* White space is a node

```
<html lang="en">
  <body>
    <p>Hello World</p>
  </body>
</html>
```

* You could remove white space

```
<html lang="en"><body><p>Hello World</p></body></html>
```

## Node Relationships
* Accessing DOM nodes in JavaScript through node relationships

### Node relationship properties
* .parentNode
* .firstChild
* .lastChild
* .nextSibling
* .previousSibling
* .childNodes[]
    - Will give an iterable called `NodeList`, containing all child nodes of a node
    - Use bracket notation with `index` to access each child in the list
    - `childNodes[1]` for second child

## Traversing the DOM
* Because of parent/child node relationships in the DOM the DOM gives us a interface we can use to reference nodes in relation to each other in JavaScript
    - Other languages like PHP, Java and Python can also use these concepts to interact with the DOM

### Accessing the body node
`let node = document.body;`

* We can do this with `body` because there is only one `body` element
    - Can't do this with `div` or other elements with multiple instances
* When we have an entrance point we can "traverse the DOM"

![traverse DOM](https://i.imgur.com/F6DB2cu.png)

![another DOM traverse](https://i.imgur.com/RQa3Dh0.png)

`node-relationships.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>DOM Relationships Demo</title>
    <style>
        table, table * {
            border: 2px solid;
            padding: 10px;
        }
        td {
            background: palegreen;
        }
        body {
            font: 1.2em "Source Sans Pro", Arial, sans-serif;
        }
    </style>
</head>
<body>
    <h1>DOM Relationships Demo</h1>
    <p>
        Click on any element to see the DOM path to its node
    </p>
    <h2>LISTS & ANCHORS</h2>
    <ul>
        <li><a href="">Unordered Listitem Anchor</a></li>
        <li>Unordered Listitem 4
            <ol>
                <li><a href="">Nested Ordered Listitem Anchor</a></li>
                <li>Nested Ordered Listitem 2</li>
            </ol>
        </li>
    </ul>
    <h2>TABLE</h2>
    <table>
        <tbody>
            <tr>
                <td>Cell 1</td>
                <td>Cell 2</td>
                <td>Cell 3</td>
            </tr>
        </tbody>
    </table>

    <script>
        function handleClick(event) {
            event.stopPropagation();
            let node = event.target;
            let thisPath = node.nodeName;
            while (node.parentNode) {
                node = node.parentNode;
                thisPath = node.nodeName + " > " + thisPath;
            }
            alert(thisPath);
        }

        function attachHandler(node) {
            if (node === null) {
                return;
            }
            node.onclick = handleClick;
            for (child of node.childNodes) {
                attachHandler(child);
            }
        }
        attachHandler(document.body);
    </script>
</body>
</html>
```

## Mouse Events
* onclick()
* onmousedown()
* onmouseup()
* onmouseover()
* onmouseout()

## inline event handlers
* When you add the inside HTML elements
* Can be added as an attribute inside any HTML element that can be clicked
* After clicking it will run the JavaScript inside the attribute value
* typically used to call a function

`<h1 onclick="changeBackground();">Click Me</h1>`

### Demos
`onclick.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Onclick Demo</title>
</head>
<body>
    <h1 onclick="changeBackground();">Click Me</h1>

    <script>
        function changeBackground() {
            const h1 = document.getElementsByTagName('h1')[0];
            h1.style.background = 'orange';
        }
    </script>
</body>
</html>
```

* `getElementsByTagname('h1')[0]`
    - returns a list of elements even if there is only 1

### onmousedown & onmouseup
`onmousedown.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Onmousedown & Onmouseup Demo</title>
</head>
<body>
    <h1 onmousedown="changeBackground();" onmouseup="revertBackground()">Click Me</h1>

    <script>
        const h1 = document.getElementsByTagName('h1')[0];

        function changeBackground() {
            h1.style.background = 'orange';
        }
        function revertBackground() {
            h1.style.background = 'white';
        }
    </script>
</body>
</html>
```

## onmouseover & onmouseout
`onmouseoverout.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Onmouseover & Onmouseout Demo</title>
    <style>
        div {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div onmouseover="changeBackground('red');" onmouseout="changeBackground('yellow');">
        Move your mouse over this text, then move it out
    </div>

    <script>
        function changeBackground(newColor) {
            document.getElementsByTagName('div')[0].style.background = newColor;
        }
    </script>
</body>
</html>
```

### Challenges
1. Update the code in `onmouseoverout.html` by adding `onmousedown` and `onmouseup` inline event handlers to the `div` element thus that the `onmouseover` and `onmouseout` events are preserved as-is, but when you click down on the `div` in the browser, the `div` text turns **green**, and when you release the mouse button, the `div` text turns **orange**

```
// MORE CODE

    <div onmousedown="changeBackground('green')"
      onmouseup="changeBackground('orange')"
      onmouseover="changeBackground('red')"
      onmouseout="changeBackground('yellow');"
    >
      Move your mouse over this text, then move it out
    </div>

// MORE CODE
```

2. Update the code in `onmousedownup.html` to use a single function that handles both the `onmousedown` and `onmouseup` events, as you saw it's possible to do in the `onmouseoverout.html` demo, by passing the color to change to as an argument

```
// MORE CODE

  <body>
    <h1
      onmousedown="changeBackground('red');"
      onmouseup="changeBackground('blue')"
    >
      Click Me
    </h1>

    <script>
      const h1 = document.getElementsByTagName("h1")[0];

      function changeBackground(color) {
        h1.style.background = color;
      }
    </script>
  </body>

// MORE CODE
```

3. Update all three files to use `document.getElementById` instead of `document.getElementsByTagName`. Then try updating them all to use `document.querySelector`

`onmousedownup.html`

```
// MORE CODE

    <script>
      // const myHeading = document.getElementById("my-heading");
      const myHeading = document.querySelector("#my-heading");
      // const h1 = document.getElementsByTagName("h1")[0];

      function changeBackground(color) {
        myHeading.style.background = color;
      }
    </script>

// MORE CODE
```

`onmouseoverout.html`

```
// MORE CODE

  <body>
    <div
      id="my-div"
      onmousedown="changeBackground('green')"
      onmouseup="changeBackground('orange')"
      onmouseover="changeBackground('red')"
      onmouseout="changeBackground('yellow');"
    >
      Move your mouse over this text, then move it out
    </div>

    <script>
      function changeBackground(newColor) {
        // document.getElementsByTagName("div")[0].style.background = newColor;
        // document.getElementById("my-div").style.background = newColor;
        document.querySelector("#my-div").style.background = newColor;
      }
    </script>
  </body>

// MORE CODE
```

```
// MORE CODE

  <body>
    <h1 id="my-unique-h1" class="my-h1" onclick="changeBackground();">
      Click Me
    </h1>

    <script>
      function changeBackground() {
        // const h1 = document.getElementsByTagName('h1')[0];
        const myUniqueHeadingEl = document.getElementById("my-unique-h1");
        // const myHeadingEl = document.querySelector(".my-h1");
        // h1.style.background = 'orange';
        // myHeadingEl.style.background = "orange";
        myUniqueHeadingEl.style.background = "orange";
      }
    </script>
  </body>

// MORE CODE
```


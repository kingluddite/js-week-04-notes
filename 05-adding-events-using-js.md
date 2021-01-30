# Adding Events using JavaScript
* `addEventListener()`
* `removeEventListener()`

## We used inlinie event handler (like `onclick` in our HTML)
* Great to use for basic demos

## We will add event handlers with JavaScript
* Using the built-in `addEventListener()` method
* **Best Practice** recommended to use this modern way to add events using vanilla JavaScript
* syntax
    - `node.addEventListener('eventName', funcToRun)`
    - We typically use this event method on a DOM element node
    - The event names are the same as before but we drop the `on`
    - The event name must be a string (be inside quotes)
    - The funcToRun must be the function name only (no argument list (so leave off the quotations))

## The right way
```js
function sayHello() {
    alert('hello');
}
const headerEl = document.querySelector('.header');
header.addEventListener('click', sayHello);
```

## The wrong way
```js
function sayHello() {
    alert('hello');
}
const headerEl = document.querySelector('.header');
header.addEventListener('click', sayHello());
```

## `event-listener-demo1.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Event Listener Demo 1</title>
    <style>
        div {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div>Move your mouse over this text then off!</div>

    <script>
        const div = document.querySelector('div');
        
        div.addEventListener('mouseover', changeTextColor);
        div.addEventListener('mouseout', revert);

        function changeTextColor() {
            div.style.color = 'orange';
        }

        function revert() {
            div.style.color = 'black';
        }
    </script>
</body>
</html>
```

## Pro of using `addEventListener()`
* You can use it to add more than one handler function to the same event, on the same element
    - You can not do this with inline event handler

## Show how inline event handlers doesn't work as we expect
* Only one inline event handler works

`event-listener-demo2.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Event Listener Demo 2</title>
    <style>
        div {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div onmouseover="changeTextColor();" onmouseover="changeBackground();" onmouseout="revert();">Move your mouse over this text then off!</div>

    <script>
        // This demo does not show any actual event listeners
        // It demonstrates how with more than one inline onmouseover event handler, only the first will work
        const div = document.querySelector('div');

        function changeTextColor() {
            div.style.color = 'orange';
        }

        function changeBackground() {
            div.style.background = 'purple';
        }

        function revert() {
            div.style.color = 'black';
            div.style.background = 'white';
        }
    </script>
</body>
</html>
```

### But this will work
`event-listener-demo3.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Event Listener Demo 3</title>
    <style>
        div {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div>Move your mouse over this text then off!</div>

    <script>
        const div = document.querySelector('div');
        div.addEventListener('mouseover', changeTextColor);
        div.addEventListener('mouseover', changeBackground);
        div.addEventListener('mouseout', revert);

        function changeTextColor() {
            div.style.color = 'orange';
        }

        function changeBackground() {
            div.style.background = 'purple';
        }

        function revert() {
            div.style.color = 'black';
            div.style.background = 'white';
        }
    </script>
</body>
</html>
```

## removeEventListener()
```js
node.addEventListener('eventName', funcToRun);

node.removeEventListener('eventName', funcToRun);
```

### Let's show how we can add an event and then remove it
* We'll add an event that changes the bg but then we'll remove it

`event-listener-demo4.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Event Listener Demo 4</title>
    <style>
        div {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div>Move your mouse over this text then off!</div>

    <script>
        const div = document.querySelector('div');
        div.addEventListener('mouseover', changeTextColor);
        div.addEventListener('mouseover', changeBackground);
        div.addEventListener('mouseout', revert);

        function changeTextColor() {
            div.style.color = 'orange';
        }

        function changeBackground() {
            div.style.background = 'purple';
            div.removeEventListener('mouseover', changeBackground);
        }

        function revert() {
            div.style.color = 'black';
            div.style.background = 'white';
        }
    </script>
</body>
</html>
```

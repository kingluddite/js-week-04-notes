# Timer Events
* setTimeout()
    - Timers allow us to delay the execution of some code for a specific amount of time
    - syntax
        + `setTimeout(functionName, waitDuration)`
        + **note** Do not call the function with `()` after the function name
            * We want to `reference` the function not call it
        + `waitDuration` is in milliseconds
* clearTimeout()
* setInterval()
* clearInverval()

`timer-demo1.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Timer Demo 1</title>
  </head>
  <body>
    <button type="button" onclick="setAlarm()">Set Alarm</button>

    <script>
      function setAlarm() {
        // get user input with what time to wake up
        const waitDuration = prompt("How long do you want to sleep?");
        setTimeout(wakeMeUp, waitDuration);
      }

      function wakeMeUp() {
        alert("Wake up!");
      }
    </script>
  </body>
</html>
```

## setTimeout() - Move the banana to the right
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Timer Demo 2</title>
    <style type="text/css" media="screen">
      img {
        position: absolute;
        left: 0;
      }
    </style>
  </head>
  <body onload="moveBanana()">
    <img src="./images/banana.png" alt="a yellow banana" />
    <script charset="utf-8">
      let xPosition = 0;
      let theBanana = document.querySelector("img");
      function moveBanana() {
        xPosition += 1;
        theBanana.style.left = xPosition + "px";
        setTimeout(moveBanana, 50);
      }
    </script>
  </body>
</html>
```
## clearTimeout() - We stop the banana with `clearTimeout()`
* We can have multiple timers running at 1 time
    - We need to tell which one to stop so we need the Timer's name
    - **note** `setTimeout()` will always return a numberic timer ID as it's return value (assign this numeric ID to a variable)
    - `let timerId = setTimeout(functionName, waitDuration)`

```html
// MORE CODE
    <title>Timer Demo 2</title>
    <style type="text/css" media="screen">
      img {
        position: absolute;
        left: 0;
        top: 50px;
      }
    </style>
  </head>
  <body onload="moveBanana()">
    <img src="./images/banana.png" alt="a yellow banana" />
    <button type="button" onclick="clearTimeout(bananaTimer)">
      Stop Banana Moving
    </button>
    <script charset="utf-8">
      let xPosition = 0;
      let theBanana = document.querySelector("img");
      let bananaTimer = 0;
      function moveBanana() {
        xPosition += 1;
        theBanana.style.left = xPosition + "px";
        bananaTimer = setTimeout(moveBanana, 50);
      }
    </script>
  </body>
</html>
```
## setInterval()
* Will repeat the given function instead of running it once, using the given wait duration
  - `setInternal(func, wait)`
* Returns a numeric ID that you can assign to a variable

### clearInterval() - stop setInterval()
* `let timerID = setInterval(func, wait)`
* Stop the timer with `clearInterval by giving it that specific timer ID`
* `clearInterval(timerId)`

`move-banana-a-lot.html`

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <title>Timer Demo 4</title>
    <style>
        img {
            position: absolute;
            left: 0;
            top: 50px;
        }
    </style>
</head>
<body onload="startMovingBanana()">
    <img src="images/banana.png" alt="A yellow banana image" />
    <button type="button" onclick="clearInterval(bananaTimer);">STOP BANANA</button>
    <script>
        let xPosition = 0;
        let theBanana = document.querySelector('img');
        let bananaTimer = 0;

        function startMovingBanana() {
            bananaTimer = setInterval(moveBanana, 50);
        }

        function moveBanana() {
            xPosition += 1;
            theBanana.style.left = xPosition + 'px';
        }
    </script>
</body>
</html>
```

* Add a button to start the movement again

```
    <button type="button" onclick="startMovingBanana()">
      Start Banana again
    </button>

```

## Review - So what's the difference between setInterval and setTimeout?
```
var intervalID = setInterval(alert, 1000); // Will alert every second.
// clearInterval(intervalID); // Will clear the timer.

setTimeout(alert, 1000); // Will alert once, after a second.
setInterval(function(){ 
  console.log("Oooo Yeaaa!");
}, 2000);//run this thang every 2 seconds
```

# For loops
- similar to while loops, but with built-in support for an incrementing iterator

## While loop

```javascript
let i = 0;
while (i < 5) {
  console.log("Loop iteration #", i);
  i += 1;
}
```

## Convert while loop to for loop

```javascript
for (let i = 0; i < 5; i++) {
  console.log("Loop iteration #", i);
}
```

## Loop through an array

```javascript
const starWarsTrilogy = [
  "Star Wars",
  "The Empire Strikes Back",
  "Return Of the Jedi",
];

for (let i = 0; i < starWarsTrilogy.length; i++) {
  console.log("My favorite Star Wars movies are " + starWarsTrilogy[i]);
}
```

## Great visualization tool
[visualize code tool](http://www.pythontutor.com/visualize.html#mode=display)

## for...of loop
* Less typing than for loop
* Works with arrays and other iterables

## What are "other iterables"
* Data structures that contain lists of items that can be iterated over
* ES6 made iterables possible in JavaScript

### For...Of Loops
```
// MORE CODE

for (const/let variableName of arrayName) {
  // code to exectute once per each item in the array
}

// MORE CODE
```

## And we'll use it in our previous array
```
// MORE CODE

for (const movie of starWarsTrilogy) {
  console.log("My favorite Star Wars movies are " + movie);
}

// MORE CODE
```

* Better than a for loop when you want to iterate through an array
    - Why? It is shorter syntax, more readable
    - We use `const` but `let` would work if you want to reassign the value while inside the loop

# Let's use `let`

```
// MORE CODE

for (let movie of starWarsTrilogy) {
  movie = movie.toUpperCase();
  console.log("My favorite Star Wars movies are " + movie);
}

// MORE CODE
```

## break and continue statements
* `break` immediately exits a loop
* `continue` statement will immediately skip to the next iteration of the loop

```
// MORE CODE

// break statement to break out of a for loop
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i);
}

// MORE CODE
```

* Output

```
0
1
2
3
4
undefined
```

### continue
```
// MORE CODE

// continue statement to break out of a for loop
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue;
  }
  console.log(i);
}

// MORE CODE
```

* That will log 0 to 9 but skip 5

## Dice exercise 3
`dice.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Dice Game</title>
  </head>
  <body>
    <h1>Dice Game</h1>
    <h2>Rules:</h2>
    <ul>
      <li>
        When you click the Roll Dice! button, you will roll up to 10 dice, one
        at a time.
      </li>
      <li>If you roll a 1, game stops and all further rolls are forfeited.</li>
      <li>
        If you roll 2, 3, or 4, you win nothing but you get to roll again.
      </li>
      <li>If you roll a 5, you win 5 gold coins and you get to roll again.</li>
      <li>If you roll a 6, you win 6 gold coins and you get to roll again.</li>
    </ul>
    <button type="button" onclick="rollDice()">Roll Dice!</button>
    <script src="js/dice-game.js"></script>
  </body>
</html>
```

`dice.js`

```javascript
function rollDice() {
  let goldCoins = 0;
  for (let i = 0; i < 10; i++) {
    const roll = Math.floor(Math.random() * 6) + 1;
    alert("You roll a " + roll + ".");
    if (roll === 1) {
      alert("Game over, no more rolls :( ");
      break;
    }
    if (roll < 5) {
      continue;
    }
    alert("Congrats, you win " + roll + " gold coins!");
    goldCoins += roll;
  }
  alert("You have won a total of " + goldCoins + " gold coins");
}
```
## Additional challenges for dice game
* Update the code to give the player a running count of how many gold coins they have won each time they roll a winning toss, instead of only at the end.
* Add another rule: If the player rolls a 4, then 1 coin is subtracted from the total before the next roll, only if they have more than 0 coins

```javascript
function rollDice() {
  let goldCoins = 0;
  for (let i = 0; i < 10; i++) {
    const roll = Math.floor(Math.random() * 6) + 1;
    alert("You roll a " + roll);
    if (roll === 1) {
      alert("Game over, no mjre rolls :( ");
      break;
    }
    if (roll === 4 && goldCoins > 0) {
      goldCoins -= 1;
      alert(
        "Sorry, you roll a " +
          roll +
          " and you lose 1 gold coin.\n\nYou currently have " +
          goldCoins +
          " gold coins"
      );
    }
    if (roll < 5) {
      continue;
    }
    goldCoins += roll;
    alert(
      "Congrats, you win " +
        roll +
        " gold coins!\n\nYou currently have " +
        goldCoins +
        " gold coins"
    );
  }
  alert("You have won a total of " + goldCoins + " gold coins");
}
```

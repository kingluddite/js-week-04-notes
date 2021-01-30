# Built-in array methods
### concat()
* combines two arrays into one and returns a new array containing all items from both arrays
* Does NOT mutate original arrays

### concat() syntax
`firstArray.concat(secondArray)`

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

### sort()
* alphabetically sort array of strings
* Will mutate the original array (so you don't need to assign it's return value to a new variable)

```javascript
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]
```

### reverse()
* reverse sort array of strings
* mutates the original array

```javascript
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]
```

## slice()
* Will copy part of an array and place it into a new array
* Non-mutating method so it does not mutate the original array
* The return value is a new array with copies of the "sliced" out items

### slice syntax
`array.slice(beginIndex, endIndex)` (note: endIndex is not included)

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]
```

* **note** If you don't include the second index, then it will take the beginIndex to the end of the array
* If you provide not argument it will return the entire array

## splice()
* insert, add to, or remove  items from an array at any point, (not only the beginning or end)
* It does mutate the original array

### splice() to insert
#### syntax
`array.splice(atIndex, 0, item)`

* The second argument for splice insert must always be `0` (because `0` means you are not trying to replace or delete any items)

```javascript
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]
```

### use splice to insert multiple items into an array
`array.splice(atIndex, 0, item1, item2, item3, ...)`

### splice to remove syntax
`array.splice(atIndex, numItemsToRemove)`

* splice() returns the removed items

```javascript
let myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon']
let removed = myFish.splice(3, 1)

// myFish is ["angel", "clown", "drum", "sturgeon"]
// removed is ["mandarin"]
```

### splice() to replace syntax
`array.splice(atIndex, numItemsToReplace, item(s)`

* returns the replaced item(s)

```javascript
const testArr = ['a', 'b', 'c', 'd', 'e', 'f'];
const replaced = testArr.splice(1, 3, 'uno');
// testArr // ['a', 'uno', 'e', 'f']
// replaced // ['b', 'c', 'd']
```

## Code Challenge: Arrays Practice
```javascript
/******************* CHALLENGE 1: CONCAT ******************/
const states1 = ['Iowa', 'Texas', 'Oregon']; 
const states2 = ['Kansas', 'California', 'Nevada'];
// concat() the above two arrays into a single array and assign the result to the states array below (delete the empty array currently there)
const states = states1.concat(states2);

// you do not need to change the line below
document.querySelector('#challenge1').textContent = states.join(', ');
/****************** End of Challenge 1 ********************/

/******************* CHALLENGE 2: SORT ********************/
const animals = ['bonobo', 'hyena', 'zebra', 'koala', 'tiger'];
// write code below this line to sort the animals array
animals.sort();

// you do not need to change the line below
document.querySelector('#challenge2').textContent = animals.join(', ');
/****************** End of Challenge 2 ********************/

/****************** CHALLENGE 3: REVERSE ******************/
const numbers = [7, 13, 68, 49, 10000, 0.23]
// write code below this line to reverse the numbers array
numbers.reverse();

// you do not need to change the line below
document.querySelector('#challenge3').textContent = numbers.join(', ');
/****************** End of Challenge 3 ********************/

/******************** CHALLENGE 4: SLICE ******************/
const directions = ['n', 's', 'nw', 'e', 'se'];
// write code below this line to slice the items with index 2 and 3 from the directions array, and assign the resulting array to the variable newDirections (delete the empty array currently there)
const newDirections = directions.splice(2, 2);

// you do not need to change the line below
document.querySelector('#challenge4').textContent = newDirections.join(', ');
/****************** End of Challenge 4 ********************/

/************* CHALLENGE 5: SPLICE TO INSERT **************/
const birds = ['seagull', 'hawk', 'sparrow', 'raven'];
// write code below this line to add 'owl' to the birds array, between 'sparrow' and 'raven', using splice
birds.splice(3, 0, 'owl')

// you do not need to change the line below
document.querySelector('#challenge5').textContent = birds.join(', ');
/****************** End of Challenge 5 ********************/

/************* CHALLENGE 6: SPLICE TO REMOVE **************/
const menu = ['gyro', 'sandwich', 'burger', 'taco', 'pasta'];
// write code below this line to remove 'burger' and 'taco' from the menu array, using splice once
menu.splice(2, 2)

// you do not need to change the line below
document.querySelector('#challenge6').textContent = menu.join(', ');
/****************** End of Challenge 6 ********************/

/************* CHALLENGE 7: SPLICE TO REPLACE *************/
const drinks = ['milkshake', 'coffee', 'tea', 'mimosa']
// write code below this line to replace 'milkshake' from the drinks array and replace it with 'lemonade', using splice once.
drinks.splice(0, 1, 'lemonade')

// you do not need to change the line below
document.querySelector('#challenge7').textContent = drinks.join(', ');
/****************** End of Challenge 7 ********************/
```



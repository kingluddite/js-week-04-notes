# Iterables in JavaScript
## spread operator (...)
```
console.log(...[1,2,3]) // 1 2 3
```

* Spread it out into another array
```
console.log([...[1,2,3]) // [1, 2, 3]
```

* We spread all the arguments inside a function

```
// spread function arguments
function fun(...args) {
  console.log(args);
}

fun(1, 2, 3, 4, 5, 6); // [1,2,3,4,5,6];
```

## We can also use the spread operator in a string
* We can treat strings like arrays

```
// MORE CODE

const luke = "Luke Skywalker";

// spread a string
console.log(...luke);

// MORE CODE
```

## generators
* Got them officially in ES6
* But technically had them in Chrome and in some browser for awile before ES6

### What lets you know something is a generator?
* If it has a `*` after the function keyword
* Inside a generator you will see a special `yield` statement
    - `yield` inside a generator means "pause"
* To use a generator you must call it
    - And you'll get back a `Generator` object
    - That Generator object has on it a method called `next()`

```
// MORE CODE

// generators
function* count() {
  yield 1;
  yield;
  yield 3;
}

count = generator = count();
console.log(generator); // Generator {};
```

## The `next()` method on Generator objects
```
// MORE CODE

// generators
function* count() {
  yield 1;
  yield;
  yield 3;
}

count = generator = count();
console.log(generator.next()); // { value: 1, done: false}

// MORE CODE
```

* When we call next we get back an object with 2 keys on it: `value` and `done`
    - `value` is to the right of yield of whatever you want to send back
    - `done` tells you the status of the generator (is it done or not)
    - In our case it's not because there's more statements to run

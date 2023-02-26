# Two Dimensional Arrays and Nested Loops

## Introduction

Take a moment to think about a digital image. It is made up of data. It is made up of rows and columns. A very simplified image could be made up of data organized as arrays inside of arrays or a two dimensional array.

```js
const myHouse = [
  ["blue", "blue", "yellow"],
  ["blue", "white", "blue"],
  ["green", "green", "green"],
];
```

How could you access one property at a time?

## Learning Objectives

- What are two dimensional arrays and what is an example of where you might encounter one?
- Be able to access individual items inside a 2D array
- Be able to loop over each item in a 2D array

<hr>

## Accessing items in a two-dimensional array

Let's look at a 2D array

```js
const pairs = [
  ["Harold", "Maude"],
  ["Harold", "Kumar"],
  ["Laurel", "Hardy"],
];
```

Firstly, the pairs array has a length of 3. Let's confirm:

```js
console.log(pairs.length);
// 3
```

- The element at index 0 is `["Harold", "Maude"]` and has a length of 2.
- The element at index 1 is `["Harold", "Kumar"]` and has a length of 2.
- The element at index 2 is `["Laurel", "Hardy"]` and has a length of 2.

How can you access just Kumar? Let's take it one step at a time and first access the array he is in:

```js
console.log(pairs[1]);
```

Then, let's access him:

```js
console.log(pairs[1][1]);
```

You can change an element inside a 2D array the same way you have done with a 1D array.

```js
pairs[1][0] = "Neil Patrick Harris";
console.log(pairs);
```

## Create a nested loop

Oftentimes, when beginning to code, there is a tendency to try to code linearly (like from left to right). Since most people are used to writing text in this style. However, code is better suited writing from the outside in.

Start with the outside loop and confirm it works as expected:

```js
for (let i = 0; i < 5; i++) {
  console.log("The value of i is:", i);
}
```

Now create the inner loop

```js
for (let i = 0; i < 5; i++) {
  console.log("The value of i is:", i);
  for (let j = 0; i < 3; j++) {
    console.log("The value of j is:", j);
  }
}
```

## Loop over a 2D array

Let's create a simple grid.

```js
const grid = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8, 9],
];
```

The goal will be to print each item in numeric order.

It is also important to figure out how to code small testable steps. If you make a mistake in three lines of code, it is easier to find the mistake. If you wait until you have coded 30 lines of code, hunting for your mistake(s) becomes much harder.

Start with a function:

```js
function printGrid() {
  console.log("I will print a grid!");
}

printGrid();
```

Next, set up a parameter:

```js
function printGrid(arr) {
  console.log("I will print a grid!", arr);
}

printGrid(grid);
```

The outer function works as expected. Now you can create the first loop. You can use `for of` loops since you want to log every value.

```js
function printGrid(arr) {
  for (let row of arr) {
    console.log(row);
  }
}

printGrid(grid);
```

Now the inner loop:

```js
function printGrid(arr) {
  for (let row of arr) {
    for (let cell of row) {
      console.log(cell);
    }
  }
}

printGrid(grid);
```

You could also have used a for loop:

```js
function printGrid(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr[i].length; j++) {
      console.log(arr[i][j]);
    }
  }
}

printGrid(grid);
```

For loops are a better choice if you want to print every other row or cell or if you want to start from the middle or go backwards.

```js
function printGridInReverse(arr) {
  for (let i = arr.length; i > 0; i--) {
    for (let j = arr[i].length; j > 0; j--) {
      console.log(arr[i][j]);
    }
  }
}

printGrid(grid);
```

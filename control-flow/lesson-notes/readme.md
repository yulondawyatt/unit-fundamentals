# Control Flow

## Learning objectives

By the end of this lesson, you should be able to:

- Learn how to use and evaluate boolean expressions
- Understand how truthy and falsy values are used with `if` statements.
- Conditionally run code with `if/else` statements.
- Describe how curly braces often signify a code block in JavaScript and why it is important.
- Control the flow of programs to solve real-world problems.

---

## Guiding questions

- Each value in JavaScript is either truthy or falsy. What does this mean?

- You can check the truthiness or falseness of a value by adding `!!` in front of it. For example, `!!0` evaluates to `false`.

Why does this work? What does a single `!` operator do?

- You can represent the logical concepts of "and" and "or" with `&&` and `||` respectively. With that in mind, take a look at the following code. What do you think will be printed on the console? Why so?

```js
console.log(false || true);
```

- What will be printed to the console for the following code? Why so?

```js
console.log(true && false && true);
```

- What will be printed to the console for the following code? Why so?

```js
console.log(((!false && true) || false) === true);
```

- The following code includes a conditional statement. If you were to run the code below, would anything be logged to the console? Why or why not?

```js
const isProgrammer = true;
const isMotivated = true;
if (isProgrammer && isMotivated) {
  console.log("It's time to start coding!");
}
```

- Is there a limit to the amount of code you can include between the curly braces of the conditional statement?

- What is a keyword in JavaScript?

- Take a look at the following code and identify all keywords.

```js
const city = "Portland";
const state = "Maine";
let greeting = "Welcome to ";
greeting += city + ", " + state;
```

- What does it mean for something to be "conditional?"

- The code below includes an `if/else` statement and keywords that allow you to write conditional code.

Before running the code below, take a look and guess what will be logged. Then, run the code and confirm your guess.

```js
const costInCents = 6_500;
if (costInCents > 5_000) {
  console.log("Too expensive!");
} else {
  console.log("I'll buy it!");
}
```

- What is the purpose of the code between the parenthesis after the `if` keyword? (i.e. `(costInCents > 5_000)`.)

- There are two code blocks in the code above. What are they? How do you know?

- Take a look at the code below. What will be logged? Why?

```js
const costInCents = 3_500;
if (costInCents > 5_000) {
  console.log("Too expensive!");
}
```

- Take a look at the code below. What will be logged? Why?

```js
const costInCents = 3_500;
if (costInCents > 5_000) {
  console.log("Too expensive!");
} else if (costInCents > 1_000) {
  console.log("Not bad, I'll take one.");
} else {
  console.log("I'll buy it!");
}
```

- Take a look at the code below. What will be logged? Why?

```js
const isNew = true;
const costInCents = 6_500;
if (isNew) {
  console.log("I'll take it.");
}

if (costInCents > 5_000) {
  console.log("Too expensive!");
}
```

- Take a look at the code below. What will be logged? Why?

```js
const isNew = true;
const costInCents = 6_500;
if (costInCents > 5_000) {
  if (isNew) {
    console.log("It's expensive but, I think I'll take it.");
  } else {
    console.log("Too expensive for something that isn't brand new!");
  }
}
```

- A `switch` statement is another way to run code conditionally. How does a `switch` statement differ from an `if/else` statement?

- Take a look at the `switch` statement below. What will be logged? Why?

```js
const productName = "sneakers";

switch (productName) {
  case "sneakers":
    console.log("A nice pair of sneakers.");
    break;
  case "shirt":
  case "t-shirt":
    console.log("A good looking t-shirt.");
    break;
  case "jacket":
    console.log("A well made jacket.");
    break;
  default:
    console.log("Sorry, that product is not registered.");
}
```

- What would happen if `productName` had a value of `"shirt"`? Why?

- What would happen if `productName` had a value of `"JACKET"`? Why?

- Take a look at the situation described below. What are the possible outcomes of this situation? What are the variables or inputs that help determine the outcome?

```
If I have at least $10, then I'll buy a single slice of pizza. If I have more than $10, I'll buy a small pizza.
```

- Write code that represents the situation described above. Consider the following:

- What variables do you need to keep track of?
- What are the conditions that change the outcome?

You may log out what happens within your `if/else` statement code blocks. (E.g., `"I buy a single slice."`.)

- Take a look at the code you've written. Try changing the value of the variables you've defined. Does the outcome change as you expect?

- Is it possible to replace what you've written using a `switch` statement instead of `if/else`? Why or why not?

- Take a look at the more complicated situation described below. What are the possible outcomes of this situation? What are the variables or inputs that help determine the outcome?

```
The price of a single slice of pizza is $3. A small pizza is $11, a medium pizza is $15, and a large pizza is $19.

If my group size is more than 6 people, I'll buy a large pizza. If, instead, the group size is between 4 and 6 people. I'll buy a medium. If the group size is either 2 or 3 people, I'll buy a small pizza. Otherwise, I'll buy a slice of pizza.

Finally, if there are any vegetarians in my group, I'll buy a veggie pizza. Otherwise, I'll buy a pepperoni pizza.

How much money do I need, and what kind of pizza will I get?
```

- Write code for the situation above. Keep in mind the inputs, outputs, and different conditions.

- When you write an `if/else` block do you always need an `else` statement?

```js
if (response === "yes") {
  console.log("I agree! Coding is cool");
} else if (response === "kinda") {
  console.log("I am glad you kinda like it!");
} else {
  // Do nothing, say nothing
}
```

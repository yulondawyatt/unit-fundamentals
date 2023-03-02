# Higher Order Native Array Methods

Higher-order functions have some functionality that can be combined with your custom functionality.

A common use-case is with arrays. You often want to loop over an array, and _do something_. You may wish to filter your array for values that are always above 0. You may want to check if every array item contains a specific value, or you may want to create a new array that has transformed an old array in some way.

You can, of course, create your versions of these higher-order functions. But it is typically faster and easier to use what JavaScript has provided for you.

## Learning Objectives

By the end of this lesson, you should be able to:

- Review programming principles
- Learn to use some common array methods that use callbacks

---

## Programming principles

As you learn more intermediate coding concepts and build your skills, there will be opportunities to solve a code challenge and improve your coding ability.

Read this article on[ programming principles](https://www.artima.com/weblogs/viewpost.jsp?thread=331531), pick three to learn more about:

- DRY: (Don't Repeat Yourself)
- KISS: (Keep it simple)
- Avoid creating a YAGNI: (You ain't gonna need it)
- Do the simplest thing that could possibly work
- Don't make me think
- Write code for the maintainer
- Single responsibility principle
- Avoid premature optimization
- Separation of concerns

## Higher-order array methods

### Abstraction

When you go to a restaurant and order a slice of pizza, the action you take is simple. However, in the restaurant, many things are happening: the ingredients for the pizza had to be ordered, and the oven turned on, the cook had to prepare and cook the pizza, the manager had to make sure that the restaurant opened on time and that everything is up to code and much more. The process of preparing the pizza has been abstracted away from the customers.

Code also can be abstracted. Certain functionality can be tucked away inside of a function so that you can focus on writing clear and maintainable code.

Imagine you are creating new labels for some ice cream. The incoming data is

```js
const flavors = ["Chocolate", "Vanilla", "Wasabi", "Strawberry"];
```

And the label must read `Pursuit's Amazing ${flavor} Ice Cream`.

You could write a for loop to accomplish the task:

```js
const arrayLabels = [];
for (let i = 0; i < flavors.length; i++) {
  const label = `Pursuit's Amazing ${flavors[i]} ice cream`;
  arrayLabels.push(label);
}

console.log(arrayLabels);
```

By now, reading for loops is likely getting easier for you. But overall, this code is somewhat long and will take you a bit to walk through it.

Instead, you could reach for a higher-order native array method. These methods iterate (loop over) each array item and do _something_.

Let's look at the `.map()` method. `.map()` is a method that can transform an array into a new array.

Let's rewrite the code above using `.map()`. `.map()` is an array method that takes one argument, a callback function.

```js
const newArrayLabels = flavors.map();
```

```js
const newArrayLabels = flavors.map(() => {});
```

The callback takes a minimum of 1 parameter. The parameter will represent each array item, one at a time. Typically, arrays have a plural name like `flavors` or `llamas` or `songs`: therefore, a sensible parameter name would be the singular form like `flavor`, `llama`, or `song`.

```js
const newArrayLabels = flavors.map((flavor) => {});
```

`.map()` requires a return statement to work. However, before the return statement, you can code whatever you like. To help see how .`.map()` works, add a console.log:

```js
const newArrayLabels = flavors.map((flavor) => {
  console.log(flavor);
  return flavor;
});
```

You can see that flavor represents each array item in order.

Now, you can update the function to return a new label:

```js
const newArrayLabels = flavors.map((flavor) => {
  return `Pursuit's Amazing ${flavor} ice cream`;
});

console.log(newArrayLabels);
```

At first, this syntax can seem strange because it is new. However, it is shorter and more straightforward than using a regular for loop for this problem.

Additionally, the arrow function syntax can be made even shorter. As you research more methods, you may encounter more concise syntax if the code is only one line long. Remember, the `return` statement is implicit when there are no curly braces.

```js
const newArrayLabelsShort = flavors.map(
  (flavor) => `Pursuit's Amazing ${flavor} ice cream`
);

console.log(newArrayLabelsShort);
```

## On your own

One of the most valuable skills to have in any career is teaching yourself what you need to know. In the rest of this reading, you can teach yourself how to use some native array methods with higher-order functions.

See how many problems you can solve using your ability to research and code. These problems don't need to be turned in. They are simply an opportunity to practice and better understand the challenging yet powerful concept of higher-order functions.

Two arrays to work with:

```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 0];

const pangram = [
  "The",
  "quick",
  "brown",
  "fox",
  "jumps",
  "over",
  "the",
  "lazy",
  "dog",
];
```

The first question is for the numbers array. The second question is for the words array.

#### `.every()`

1. Determine if every number is greater than or equal to 1
1. determine if every word shorter than 6 characters

#### `.filter()`

1. filter the array for numbers less than 3
1. filter words that have an even length

#### `.find()`

1. Find the first value divisible by 4
1. find the first word that is longer than 5 characters

#### `.findIndex()`

1. find the index of the first number that is divisible by 3
1. find the index of the first word that is less than or equal to 2 characters long

#### `.forEach()`

1. `console.log` each value of the `nums` array multiplied by 10
1. `console.log` each word with a question mark at the end of it.

**Thought Questions**

- What happened to the original array?
- Can you store the values from a `forEach` method in a new array?

#### `.map()`

1. make a new array of each number multiplied by 1000
1. make a new array of all the words in all lowercase

**Thought Questions**

- What happened to the original array?
- Can you store the values from a `map` method in a new array?

#### `.some()`

- Find out if some numbers are divisible by 6
- Find out if some words have the letter `i` in them

### More Challenging

The following array methods require a bit more setup than the previous ones.

#### Reduce

- Add all the numbers in the array together using the `reduce` method
- concatenate all the words using reduce

**Thought Questions**

- What happened to the original arrays for this method?

#### Sort

- Try to sort without any arguments. Do you get what you'd expect with the numbers array?
- Try to sort without any arguments. Do you get what you'd expect with the words array?
- Sort the numbers in ascending order
- Sort the numbers in descending order
- Sort the words in ascending order
- Sort the words in descending order

**Thought Questions**

- What happened to the original array?

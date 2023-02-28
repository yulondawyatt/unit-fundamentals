# Higher Order Native Array Methods

Higher-order functions have some functionality that can be combined with your custom functionality.

A common use case is with arrays. You often want to loop over an array, and _do something_. You may wish to filter your array for values that are always above 0. You may want to check if every array item contains a specific value, or you may want to create a new array that has transformed an old array in some way.

You can, of course, create your versions of these higher-order functions. But it is typically faster and easier to use what JavaScript has provided for you.

## Learning Objectives

By the end of this lesson, you should be able to:

- Review programming principles
- Learn to use some common array methods that use callbacks

---

## Programming principles

As you learn more intermediate coding concepts and build your skills, there will be opportunities to solve a code challenge and improve your coding ability overall.

Read this article on[ programming principles](https://www.artima.com/weblogs/viewpost.jsp?thread=331531), pick three to learn more about:

- DRY: (Don't Repeat Yourself)
- KISS: (Keep it simple)
- Avoid creating a YAGNI: (You ain't gonna to need it)
- Do the simplest thing that could possibly work
- Don't make me think
- Write code for the maintainer
- Single responsibility principle
- Avoid premature optimization
- Separation of concerns

## Higher-order array methods

A few array methods use callbacks. For example, `.map` - `.map` takes each element of an array, does something to it, and returns a new array.

But what should it do? Multiply everything by 5? Capitalize everything? It wouldn't be very flexible if `.map` had a hard-coded thing it always did with an array.

By allowing a callback to determine what happens to each array element, we get a lot of flexibility and can do some really powerful things.

Two arrays to work with

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

You don't have to write an answer to the thought questions.

#### Every

1. Determine if every number is greater than or equal to 1
1. determine if every word shorter than 6 characters

#### Filter

1. filter the array for numbers less than 3
1. filter words that have an even length

#### Find

1. Find the first value divisible by 4
1. find the first word that is longer than 5 characters

#### Find Index

1. find the index of the first number that is divisible by 3
1. find the index of the first word that is less than or equal to 2 characters long

#### For Each

1. `console.log` each value of the `nums` array multiplied by 10
1. `console.log` each word with an question mark at the end of it?

**Thought Questions**

- What happened to the original array?
- Can you store the values from a `forEach` method in a new array?

#### Map

1. make a new array of each number multiplied by 1000
1. make a new array of all the words in all lowercase

**Thought Questions**

- What happened to the original array?
- Can you store the values from a `map` method in a new array?

#### Some

- Find out if some numbers are divisible by 6
- Find out if some words have the letter `i` in them

### Hungry for More

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

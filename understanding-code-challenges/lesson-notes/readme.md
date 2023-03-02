# Understanding Code Challenges

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe the importance of creating standards
- Describe the role of comments in software development.
- Be able to read code comments that are in the style of JS Docs
- Describe the role of tests and how they can help when writing functions in JavaScript.
- Write simple tests using basic JavaScript.
- Interpret Jest test output to take actionable steps in code.

---

## Guiding Questions

- Based on what you know so far, why might you comment code?

- What is JSDoc?

- Describe the following code block. Focus on the comments and what each part of the comment means. What questions would you have if you needed to write the function based on this syntax?

```js
/**
 * Returns the more common plant name from the species name, if possible.
 * @param {string} speciesName - Scientific name of a plant.
 * @returns {string} Common name of the plant.
 */
function getCommonPlantName(speciesName) {}
```

- Is any part of the JSDoc syntax required?

- Based on the function below, write your JSDoc descriptor to go above the function. Make sure to include a function description, any parameter descriptions, and what the function should return.

```js
function describeNumberOfPlants(plantName, count) {
  let result = null;

  if (count < 1) {
    result = `There are no ${plantName}s.`;
  } else if (count === 1) {
    result = `There is one ${plantName}.`;
  } else {
    result = `There are ${count} ${plantName}s.`;
  }

  return result;
}
```

- How would you test that the function above works as intended?

- Why might a software developer want to test their code?

- In this course, the Jest testing library will be used. What is a library?

- Take a look at the following code, which makes use of the Jest testing library. Then, answer the questions below the code block.

```js
describe("describeNumberOfPlants()", () => {
  test("should say there are no plants (plural) if the count is less than 1", () => {
    const plantName = "Jade Plant";
    const count = 0;
    const actual = describeNumberOfPlants(plantName, count);
    const expected = "There are no Jade Plants.";
    expect(actual).toEqual(expected);
  });
});
```

For the code block above:

- What case is being tested?

- What does the `actual` variable represent?

- What does the `expected` variable represent?

- Based on what you know about the function and the test, do you think this test case will pass?

- What other test cases can you imagine should be included in the tests?

## Code Challenges in Replit, using Jest

Your instructor will have a repl.it project that is ready to have tests added.

### Understanding Code Challenges Demo

Here, you will learn the components of a test so that you can read and understand the tests better.

There are some syntax and concepts you have not yet learned. That's ok! Just focus on the parts you understand and how you can read tests to understand better what is being asked of you. Being able to read code out loud is a critical skill for being able to communicate your ideas.

You will not need to learn how to write tests in this module.

### Create a test

Test whether a function returns the sum of two numbers.

### Start by writing the first test

The first test will only test if `true` is equal to `true`. It will not rely on a function. This is so you can see a simple example and then build your understanding.

Go to the `__tests__` folder to the file `index.test.js`

Start by writing a `describe()` function. The `describe` testing suite defines function. Jest must be "downloaded" and configured correctly for this to work.

```js
describe();
```

Describe is a function that takes two arguments. The first one is a string. The second one is a `callback` function. For now, just put an empty arrow function inside.

```js
describe("a simple example", () => {});
```

Next, you will add an `it()` function inside the `describe()` callback function.

Inside of this code block, you will use the `expect()` function and chain the `toBe()` function to it. The arguments given should be the values to compare.

```js
describe("a simple example", () => {
  it("should expect true to be equal to true.", () => {
    expect(true).toBe(true);
  });
});
```

You should now be able to run this code with the green run button.

### Write another test that will test the `sumTwo()` function

#### Write the test first

Start with the outer 'shell'. In coding, it is best to work from the outside in, rather than linearly (like from left to right):

```js
describe("sumTwo()", () => {});
```

Then add the inside code:

```js
describe("sumTwo()", () => {
  it("should sum two numbers.", () => {
    expect(true).toBe(true);
  });
});
```

Now, set up the test to test the function.

You will need to call the function with the appropriate arguments. Start by testing `2 + 2`, which should equal `4`.

The actual value will be what the `sumTwo` function returns when `2` and `2` is inputted.

The `expected` value will be what you determined to be the correct result from inputting `2` and `2` as arguments.

Then use the `expect` and `toBe` functions to compare the `actual` value with the `expected value.`

```js
describe("sumTwo()", () => {
  it("should sum two numbers.", () => {
    const actual = sumTwo(2, 2);
    const expected = 4;
    expect(actual).toBe(expected);
  });
});
```

### Connecting the function and the test

The `sumTwo` function should be declared in the `index.js` function and imported into this test file.

Let's import it first. The `sumTwo` function must be wrapped in curly braces. It will be equal to the value of the file in the `index.js` that will be exported shortly.

```js
const { sumTwo } = require("../index.js");
```

Next, go to the `index.js` file and add the following at the bottom:

```js
module.exports = {
  sumTwo,
};
```

### Write the function

In the `index.js` file, create the function.

```js
function sumTwo() {}
```

You should now be able to run the tests.

The test for `sumTwo` should fail. Typically, tests are written first, and then the functions are written. It is expected that all the tests fail at first.

You can see that the detailed output says that the `Expected` value is 4, but the `Recieved` value (`actual`) is undefined.

### Get the function to pass the test

```js
function sumTwo(num1, num2) {
  return num1 + num2;
}
```

Now, the test should pass.

### Adding another test

You can add more tests inside the describe block. Check if the value returned has a `typeof` number.

```js
it("should return a number.", () => {
  const actual = typeof sumTwo(2, 2);
  const expected = typeof 4;
  expect(actual).toBe(expected);
});
```

### Add the JSDoc Comment

```js
/**
 * This function should return the sum of two numbers
 * @param {number} num1 - a number
 * @param {number} num2 - a number
 * @return {number} the sum of the two numbers
 */
function sumTwo(num1, num2) {
  return num1 + num2;
}
```

### The entire `__tests__/index.test.js` file

```js
const { sumTwo } = require("../index.js");

describe("someFunction()", () => {
  it("should expect true to be equal to true", () => {
    expect(true).toBe(true);
  });
});

describe("sumTwo()", () => {
  it("should sum two numbers.", () => {
    const actual = sumTwo(2, 2);
    const expected = 4;
    expect(actual).toBe(expected);
  });
  it("should return a number.", () => {
    const actual = typeof sumTwo(2, 2);
    const expected = typeof 4;
    expect(actual).toBe(expected);
  });
});
```

### The entire `index.js` file

```js
/**
 * This function should return the sum of two numbers
 * @param {number} num1 - a number
 * @param {number} num2 - a number
 * @return {number} the sum of the two numbers
 */
function sumTwo(num1, num2) {
  return num1 + num2;
}

module.exports = {
  sumTwo,
};
```

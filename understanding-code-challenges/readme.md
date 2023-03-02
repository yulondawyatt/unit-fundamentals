# Understanding Code Challenges

Code challenges are an excellent way to build and hone your coding skills. The better you understand and can utilize your knowledge of fundamentals, the better developer you'll become.

Before you get hired as a developer, it is very likely you will need to pass a technical interview. These interviews often involve solving a coding problem. These problems can be done in front of your interviewers, through an automated website, on a whiteboard, or even on paper.

Therefore it's critical for you to practice solving coding challenges, not only to become a stronger coder in your career but also to prepare you for technical interviews.

## Introduction

## Learning Objectives

- Describe the importance of creating standards
- Describe the role of comments in software development.
- Be able to read code comments that are in the style of JS Docs
- Describe the role of tests and how they can help when writing functions in JavaScript.
- Write simple tests using basic JavaScript.
- Interpret Jest test output in order to take actionable steps in code.

<hr>

## Standards

Standards are agreed upon styles and norms for something. An example of this is the web: early on in the web, every browser created its own standards. This meant that code that worked in Safari may have worked differently or not at all in Chrome. This made work for developers quote difficult and tedious because they had to create multiple versions of their code for each browser.

Eventually the [W3 consortium](https://www.w3.org) was formed and they take time to create standards and agree what is the 'right' way to do things on the web. This has improved the stability of the web and eased some of the difficulties web developers experience.

In this unit/module, we will use JSDoc comment standards for testing functions for your labs and projects. By using the same standard consistently, it should become easier to read and understand what you are being asked to code.

## JSDocs Standard Comments

So far, you've been able to read and write your own comments for the code you have written. Adding comments can be helpful to learn the material and if you have not looked at the code in a while, it is a great way to re-familiarize yourself with the code there.

If you've looked at your friend's comments they likely look and sound quite different. When working on a project with tens or hundreds of people over a long span of time, it is prudent to agree to some standards, so that the code is easier to understand and maintain.

While there is no right way to write comments, a common choice for a comment standard is called [JSDoc](https://jsdoc.app).

Here is a simple one-line comment for a simple function:

```js
/** This is a description of the foo function. */
function foo() {}
```

Typically, the comments are made up of:

- A simple description of the function
- A list of parameters and what datatype they are (number, string, boolean etc.)
  - These will always start with the keyword `@param`, so you can clearly determine what this line is describing
  - After `@param` is a set of curly braces. Within those curly braces is the datatype (string, number, boolean etc.)
  - After the curly braces is the name of the parameter
  - After the name of the parameter is a dash and then a brief description of the parameter
- The value that is returned

  - This line will always start with `@return` and will give the datatype an a brief description

  [JSDoc Guide for parameters](https://jsdoc.app/tags-param.html)

```js
/**
 * Uses console log to output the bank account balance.
 * @param {number} amount - a dollar amount
 * @returns {undefined} - this function only console logs something
 */

function checkBalance(amount) {
  console.log(`This is your bank account balance ${amount}`);
}

checkBalance(100);
```

This above function is fairly easy to understand, even without comments, but more complicated functions can be much harder to figure out.

In this next function, what is the difference between `user` and `username`? Is `withdrawal` a number? A boolean? Something else? What should this function return? A string? A number? Something else?

How can you tell what the input names mean and what datatypes they should be? It would take some trial and error without comments.

```js
function checkBalance(amount, user, userName, withdrawal) {
  console.log(`Hello, ${userName}, you are logged in as ${user}`);
  if (withdrawal) {
    console.log(`Your last transaction was a withdrawal`);
  } else {
    console.log(`Your last transaction was not a withdrawal`);
  }
  console.log(`Your current balance is ${amount}`);
  if (amount < 0) {
    console.log(`Your bank account balance is negative`);
    return true;
  } else {
    console.log(`Your bank account balance is positive`);
    return false;
  }
}
```

Now, comments have been added. It does look a bit verbose and possibly intimidating, but if you go line by line, this comment clarifies all the questions you had about this function and now you should be able to invoke this function with the proper arguments and also be able to predict what value should be returned.

```js
/**
 *  Returns a boolean whether the bank account balance is positive or negative
 * @param {number} amount - a dollar amount
 * @param {string} user - the user's login name
 * @param {string} userName - the user's preferred name
 * @param {boolean} withdrawal - whether the last action was a withdrawal
 * @returns {boolean} A boolean whether the bank account balance is positive or negative
 */

function checkBalance(amount, user, userName, withdrawal) {
  console.log(`Hello, ${userName}, you are logged in as ${user}`);
  if (withdrawal) {
    console.log(`Your last transaction was a withdrawal`);
  } else {
    console.log(`Your last transaction was not a withdrawal`);
  }
  console.log(`Your current balance is ${amount}`);
  if (amount < 0) {
    console.log(`Your bank account balance is negative`);
    return true;
  } else {
    console.log(`Your bank account balance is positive`);
    return false;
  }
}

checkBalance(-1, "chowe@m.net", "Cameron", true);
checkBalance(1000, "chowe@m.net", "Cameron", false);
```

### Other JSDoc notation

Some other JSDoc notation you may encounter:

```js
/**
 *  Returns a boolean whether the bank account balance is positive or negative
 * @param {*} yourChoice - any type of value you want
 * @param {string} userName - the user's preferred name
 * @param {number} startingAmount = 0  - provide a default value
 * @param {(number|boolean)} points - can be a number or boolean
 * @param {!boolean} present - must have a value, cannot be null/undefined
 */
```

[JSDocs types](https://jsdoc.app/tags-type.html)

## Understanding Tests

When working on larger applications, it quickly becomes impossible to manually check that all of your code is always working. To solve this problem, software developers write tests for their code. To write tests means to write code that verifies whether or not other code you've written is working.

Although it can be a bit confusing to understand at first, testing is an incredibly powerful tool for ensuring your code works the way you want it to and as you add features, testing will confirm if you have retained the previous functionality of your old code. Studies have been done that show that professional projects that use testing are able to add new features and grow faster than projects that don't use testing. And, for your duration at Pursuit, tests will play a big part of getting immediate feedback on the code you've written, especially early-on.

The goal of this lesson is just to get you familiar with tests.

## What are tests?

Look at the following code comment and create test case. We would expect that 2 \* 10 would be 20.

```js
/**
 *  Returns a number multiplied by 2
 * @param {number} num - a number
 * @returns {number} A number that has been multiplied by 2
 */
```

Let's say this is our first attempt to write this function:

```js
function multiplyBy2() {
  num - 3;
}

console.log(multiplyBy2(10));
// NOT 20
```

Is this code correct? No. There are many things wrong with it. Because it is short and simple, it is easy for you to evaluate this code and check it.

Let's fix it. First, let's add the JSDoc comments to help clarify what code we should write. It is better to think a lot and write a little: the more clarity you have about the code you plan to write, the smoother the process of writing code will be. Then, use our test case again.

```js
/**
 *  Returns a number multiplied by 2
 * @param {number} num - a number
 * @returns {number} A number that has been multiplied by 2
 */

function multiplyBy2(num) {
  return num * 2;
}

console.log(multiplyBy2(10));
// 20
```

What other test cases can you think of to be sure this function works as expected?

We can write a function to check this code.

We will need to:

- Call the function and get the actual value it returns.
- Think about our test case and store the expected value.
- Compare the actual value and expected value.
- Give feedback whether the actual and expected values match.

This is a lot of work up-front and with the small code challenges you have had so far, it can feel quite over-engineered. Over time, as your projects grow, this functionality will make more sense and more worthwhile.

```js
function checkMultiplyBy2() {
  const actual = multiplyBy2(10);
  const expected = 20;
  if (actual === expected) {
    console.log("✅ The function works as expected");
  } else {
    console.log(
      `❌ The function does not work as expected. The expected value is ${expected}, but received ${actual}`
    );
  }
}

checkMultiplyBy2();
// ✅The function works as expected
```

Try another value. Change the value of actual from 10 to 'ten'.

```js
const actual = multiplyBy2("ten");
// ❌ The function does not work as expected. The expected value is 20, but received NaN
```

If you imagine that a user is on a webpage with an input field and they can type whatever they want, this situation could occur. You would want to deal with it in a way that the user is informed that something has gone wrong.

```js
function multiplyBy2(num) {
  if (typeof num === "number") {
    return num * 2;
  } else {
    return "There was an error. Please make sure you enter a number";
  }
}
```

To test for the error message, you would have to write a new function. This ends up being quite tedious work.

## Introduction to Jest

Whenever coders run into similar problems over and over again, they will likely create a way to deal with them. A lot of this work is open-source-software - which is free to use and anyone can contribute to it. In coding, these projects are often referred to as libraries or frameworks.

In this course we will use the testing library Jest, which will allow us to set up tests in a much simpler and more readable way.

When you run Jest tests, you will receive output in your console that will tell you what functions are working and which are not. If something about your function is failing, you'll get additional details about what is wrong.

![Image of Jest test failures](./assets/jest-failures.png)

The image above is an example of Jest output. It is only a partial view of what you get back from Jest.

In the image above, you can see the following:

- You can see that one file was tested, `__tests__/index.test.js`. This is where the Jest tests live.
- You can see that four functions were tested: `greetings()`, `confirmTotalPrice()`, `upgradeRequested()`, and `deliverRoomNumber()`. These functions each have a number of different test cases. For example, `greetings()` has four test cases, all of which failed.
- In the bottom half of the image, you can see more details about one of the tests for the `greetings()` function. You can see that what Jest expected was the result `"Good morning, Emily."`, but instead it got the result `undefined`.
- Underneath where it says "Difference", the test code is shown where this error occurs. This will be covered in the next section.

The function that is being tested currently looks like this:

```js
/**
 * Displays an appropriate greeting to the guest.
 * @param {string} timeOfDay - Should be either "morning", "afternoon", or "evening".
 * @param {string} name - The guest's name.
 * @returns {string} An appropriate greeting based on the time of day.
 */
function greetings(timeOfDay, name) {}
```

With that in mind, it should make sense that the actual result that was returned from the function was `undefined`, as there's no explicit return value. Reading the comments above the function, it should also become clear that this function should be returning a string that makes use of the `timeOfDay` and `name` parameters.

To find out more about how this function should work, you can look at the actual Jest tests.

### Test code

The tests for the `greetings()` function will look very complicated at first. Don't panic! Your only goal right now is to interpret enough of what is going on so that you can understand the function's intention.

```js
describe("greetings()", () => {
  test("should greet the person by name when the time of day is 'morning'", () => {
    const timeOfDay = "morning";
    const guest = "Emily";
    const actual = greetings(timeOfDay, guest);
    const expected = "Good morning, Emily.";
    expect(actual).toEqual(expected);
  });

  // More tests...
});
```

Some of the code above will look very different, but some may actually look familiar. You can read the code above in the following way:

- This test is "describing" the `greetings()` function.
- The "test" declares that it "should greet the person by name when the time of day is 'morning'".
- When the `greetings()` function is called with the values `"morning"` and `"Emily"`, the `expected` output is `"Good morning, Emily."`.

Although the syntax may look at bit strange compared to what you've learned so far, the Jest tests can read nicely when you know what to look for. Try reading the code out loud. Jest tries to make their code human readable:

> This block of code `describes` the function `greetings`. The following test `should` greet the person by name when the time of day is `morning`. The `actual` output by the function `greetings` when `morning` and `Emily` are entered as arguments is set to the value `actual`. The `expected` value is set to `Good morning, Emily.` Finally, I `expect` the `actual` value `to equal` the `expected` value.

Whenever you are not sure what to do or what the code does, take the time to write it out on paper or in a note-taking app, saying it out loud or writing lots of comments in your file. You can use different colored pens or other tools to help you draw out more details. You can draw arrows or circle different components. If you don't have clarity about what you are supposed to do, it will be much harder to figure out what you need to do. Over time, you will learn to do this kind of work faster. When you look to your instructor or other coders, take a moment to realize they tend to move faster with coding because they have been practicing longer and can analyze and act on code more efficiently due to practice and experience. You will get there too!

Now, with all the information you've gathered, you should have a better idea of how the `greetings()` function should work and what steps you need to take in order to get the tests to pass.

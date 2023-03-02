# Common Errors

Part of the experience of being a developer is seeing and solving errors. While this doesn't feel great initially, errors are a normal part of developing software and aren't something to fear. In fact, great developers are excited when they get an error message because it means they have some information to help them solve their problem.

In this lesson, you'll learn about some of the most common error types. Once you know these error types, it should hopefully become easier to solve them.

## Learning Objectives

By the end of this lesson, you should be able to:

- Use the stack trace to identify where an error might be occurring.
- Describe and fix syntax errors.
- Describe and fix reference errors.
- Describe and fix type errors.

---

## The stack trace

When an error occurs, you are often shown a stacktrace. The stacktrace is like a detective's notes. It starts at the where the error occurred and then traces back to other lines of code that were executed that eventually caused the error. This output can feel very overwhelming and hard to understand at first. Take the time to go through it slowly, you'll get the hang of it soon enough. This text gives you some context as to where the error occurred.

```
TypeError: console.lg is not a function
    at listCharacters (/home/runner/Warmup-Common-Error-Handling/index.js:15:13)
    at /home/runner/Warmup-Common-Error-Handling/index.js:20:1
    at Script.runInContext (vm.js:130:18)
```

In the example above, you receive the following information:

1. The error that has occurred is a **`TypeError`**.
1. The problem is that **`console.lg`** is not a function.
1. Below, you can see that the error occurred at **`listCharacters`**. This will typically reference a function or process that caused the error.
1. Finally, you receive a more precise location of where the error occurred: you get the file name **`index.js`**, the line number **`15`**, and the character position **`13`** - which is denoted as **`15:13`**.
1. There is one more line of information, but when you see `Script.runInContext` - you can recognize this is not a file or function you have worked with, so you can disregard this information for now. Always start by looking for the files you know you did work in.

You will learn more about the concepts of "stacks" later. At this point, the most important takeaway is to read the error and be able to pick out the relevant information.

When first starting to code, it can be easy to see a lot of weird text, feel overwhelmed, and choose to ignore the output. However, these errors often have a lot of helpful information and will help you solve your issue. They will become easier to read and use to fix the code with practice.

## Syntax errors

Syntax errors occur when the code you've written is not syntactically correct. For example, the code below would cause a syntax error. Can you see why?

```js
const game = `name: "Super Mario Galaxy",
  developers: ["Nintendo", "MORE"],
  rating: 4.8,`;
console.log(game
//> SyntaxError: missing ) after argument list
```

In this case, the `SyntaxError` is quite helpful because it points out that a closing parenthetical is missing from the `console.log()` statement.

Syntax errors aren't always this simple, unfortunately. The following code also produces a `SyntaxError`. Can you see the problem?

```js
if (game === 'Super Mario Galaxy')
  console.log(game);
} else {
console.log('please choose another game);
};

//> SyntaxError: Unexpected token '}'
```

You may be surprised that the unexpected token is the closing curly brace instead of a missing opening one. That's because you can write an `if` statement without curly braces. Therefore, JavaScript is more surprised to see the closing brace.

Syntax errors mean that JavaScript cannot parse something you've written. When you encounter a `SyntaxError`, look at your code closely to see what's been mistyped.

## Reference errors

A `ReferenceError` occurs when you are attempting to refer to some variable that does not exist. Can you spot the problem in the code below?

```js
function getRatingDescription(gameName, gameRating, maxRating) {
  return `${gameName}: ${gameRating} out of ${maxRating}.`;
}

getRatingDescrption("Super Mario Galaxy", ["Nintendo", "MORE"], 4.8);
//> Uncaught ReferenceError: getRatingDescrption is not defined
```

When the function above is invoked, it's misspelled. The JavaScript interpreter attempts to invoke the misspelled function but finds nothing. Therefore, the error `getRatingDescrption is not defined` is printed.

Notice that the second argument doesn't look like a game rating value. Will this cause an error? Sometimes the mistakes in our code don't throw an error and they can be even more frustrating to find.

## Type errors

Type errors typically occur when calling a method on the wrong data type.The method `.toFixed()`, takes a floating point number and fixes the number of decimals.

```js
console.log((5.555555).toFixed(2));
```

Can you spot the issue with the code below?

```js
const javaScript = "JavaScript";

console.log(javaScript.toFixed(2));
// TypeError: "JavaScript".toFixed is not a function
```

This error by calling a method on a data type that does not have it. You cannot set the number of decimal places on a string. Therefore strings do not have this method and thus, an error is produced.

These situations most often happen when you think your variable is one datatype, but it actually another. Now you know what to look for in your code to fix it.

# Introduction to JavaScript

## Learning Objectives

- Define and use the basic syntax of code
- Define and implement the five most common primitive data types in JavaScript( numbers, strings, booleans, undefined, null).
- Implement and define standard JavaScript operators.
- Describe how curly braces often signify a code block in JavaScript and why it is important.
- Differentiate between different variable declaration keywords.
- Determine data types to variables with `typeof`
- Find more information

<hr>

## Guiding Questions

- There are seven primitive data types in JavaScript. Which ones have you seen before?

- Take a look at the data types below and identify each one.

```
null
"Hello world!"
10009
undefined
true
42.9
false
.301
``
0
NaN
-Infinity
'It\'s a sunny day!'
```

- In your own words, describe a variable in the coding context.

- Variables can be declared with three special keywords: `var`, `let`, and `const`. We will always use `let` or `const` in this course.

What are some differences between `let` and `const`?

- In your own words, describe how the code to the left of the `=` sign in the example below relates to the code on the right side of the `=` sign.

```js
const programmer = "Yehuda Katz";
```

- Will the following code run, or will it throw an error? Why or why not?

```js
let programmer;
```

- Will the following code run, or will it throw an error? Why or why not?

```js
let coding = "fun";
let coding = "exciting";
```

- Will the following code run, or will it throw an error? Why or why not?

```js
let language = "python";
language = "javascript";
const favoriteLanguage = language;
```

- The value assigned to the `welcomePhrase` variable below is a template literal or template string. In your own words, describe how it works. Does it still have a data type of `string`?

```js
const programmerName = "Abbi";
const welcomePhrase = `Welcome, ${programmerName}!`;
```

- You may have noticed that more than one-word variables are put together. For example, `welcomePhrase`. Can you have a variable with a space?

- The standard casing convention in JavaScript is camel case. What is a casing convention? What is camel case?

- Standard arithmetic operators such as `+` and `-` can be used in JavaScript. For division, you can use `/`. For multiplication, you can use `*`. You can also use parenthesis to impose an order of operations. Keeping that in mind, mentally evaluate the following code.

```js
let result = (4 + 10) / 2 - 4 * 2;
```

- If working with a complex equation, it can sometimes be simpler to break down the equation into multiple steps. Keeping that in mind, mentally evaluate the following code.

```js
let result = 4 + 10;
result = result / 2;
result = result - 4 * 2;
```

- Arithmetic code can be shortened by combining the `=` assignment operator with the appropriate arithmetic operator. For example, using `+=` means that the value will increase the value stored in the variable to the right.

Change the code above so that it makes use of combination operators. As reference, they are: `+=`, `-=`, `*=`, and `/=`.

- Take a look at the code below. Then, follow the instructions and answer the questions below that.

```js
const programmingLanguage = "Python";
if (programmingLanguage === "JavaScript") {
  console.log("JavaScript was created by Brendan Eich in just 10 days.");
}
```

1.  In the code above, how would you add another case so that when `programmingLanguage` is equal to "Python", the different text is printed? Go ahead and update the code in your repl so that the following text prints in that case: `"Guido van Rossum began working on Python in the late 1980s"`.

1.  In the code above, if the conditional statement doesn't do anything particular for the value stored in `programmingLanguage`, write code that will print the following text: `"I don't know a fun fact about that language."`. How can you test that this code works?

- Take a look at the code below. Then, follow the instructions and answer the questions below that.

```js
let num = 3;
num = "2" + 3;
```

1. What will the value of `num` be?
2. Why do you think this was evaluated the way it was?

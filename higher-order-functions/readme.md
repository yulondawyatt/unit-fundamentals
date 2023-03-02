# Higher Order Functions

Higher-order functions are an essential concept when learning JavaScript. Much code in JavaScript relies on the fact that functions can be passed to other functions, like any other value type.

This lesson will introduce you to higher-order functions and give you a bit of context about why they are used.

This lesson can be challenging because the syntax and concepts are new. However, higher-order functions are ubiquitous, and with some practice, you can use them to build some great code.

## Learning Objectives

By the end of this lesson, you should be able to:

- Define what makes a higher-order function.
- Define what makes a callback function.
- Write functions that accept a function as an argument and use that inputted function.

---

## What is a higher-order function?

A higher-order function is _any function that returns a function or expects a function as one of its parameters._

Higher-order functions are used in a variety of ways, including but not limited to the following:

- Building highly customizable functions.
- Managing code that takes time. (i.e., asynchronous code)

Have you ever visited a website and, after a minute or so, received a pop-up notification? This delay is usually caused by the function `setTimeOut`.

`setTimeOut` is a higher-order global function that accepts two arguments. The first one is the callback function, and the second is a number that represents the number of milliseconds to wait. (2000 milliseconds equals 2 seconds).

`setTimeout` is unopinionated about the code you write inside the callback. It can be whatever you want. This makes it a very customizable function and allows you to stack its functionality with other functionality.

```js
setTimeout(() => {
  console.log("Triggering pop-up message");
}, 3000);
```

## What is a callback function?

The callback function is the function that is passed as a parameter to another function. In the above example, the callback function is the arrow function. As you can see, this function is not named. Therefore it is an anonymous function.

```js
() => {
  console.log("Triggering pop-up message");
};
```

An unnamed function is useful when you only need the function one time. If you are reusing a function, it is best to name it and pass it in.

```js
const popUpMessage = () => {
  console.log("Triggering another pop-up message");
};

setTimeout(popUpMessage, 2000);
```

You will notice that only the function reference is passed in (no parenthesis) when passing in a named function. If you add parenthesis, one of two things may happen - the function is triggered immediately (not after 2000 milliseconds), or you will get an error.

```js
setTimeout(popUpMessage(), 2000);
```

```
TypeError [ERR_INVALID_CALLBACK]: Callback must be a function. Received undefined
```

## Managing code that takes time

All the code you have written so far happens quickly, so the output happens in order. However, JavaScript is `asynchronous`, meaning that it starts a task (code block), and then it does not wait for it to finish before moving on to the next code bock.

What order will the following console logs happen in?

```js
setTimeout(() => {
  console.log("I should happen first");
}, 1000);

setTimeout(() => {
  console.log("I should happen second");
}, 5000);

setTimeout(() => {
  console.log("I should happen third");
}, 3000);

console.log("I should happen last");
```

You can rewrite the code above:

```js
setTimeout(() => {
  console.log("I should happen first");
  setTimeout(() => {
    console.log("I should happen second");
    setTimeout(() => {
      console.log("I should happen third");
      console.log("I should happen last");
    }, 3000);
  }, 5000);
}, 1000);
```

As you can see, the callback function executes only after its higher-order function has been invoked.

Later, you will start to use code that is asynchronous and you will learn more about how to manage this type of code with real-world scenarios.

### Write your own higher-order function

In the previous example, you used a built-in higher-order function. However, you can also write your own.

Take a look at the `calculate()` function below.

```js
function add(num1, num2) {
  return num1 + num2;
}
function subtract(num1, num2) {
  return num1 - num2;
}
function multiply(num1, num2) {
  return num1 * num2;
}
function divide(num1, num2) {
  return num1 / num2;
}
function calculator(num1, num2, operator) {
  if (operator === "add") {
    return add(num1, num2);
  } else if (operator === "subtract") {
    return subtract(num1, num2);
  } else if (operator === "multiply") {
    return add(num1, num2);
  } else if (operator === "divide") {
    return divide(num1, num2);
  } else {
    return `Something went wrong`;
  }
}
console.log(calculator(1, 1, "add"));
console.log(calculator(2, 1, "subtract"));
console.log(calculator(3, 4, "multiply"));
console.log(calculator(5, 2, "divide"));
```

What happens if you want to add more calculations, like power, percentage, and more? This code becomes harder and harder to maintain.

Refactor this code to use higher-order functions and callbacks.

Start with the callback functions. These are fine. You could keep adding to them by including percentages, power, and more. Let's start with these.

```js
function add(num1, num2) {
  return num1 + num2;
}
function subtract(num1, num2) {
  return num1 - num2;
}
function multiply(num1, num2) {
  return num1 * num2;
}
function divide(num1, num2) {
  return num1 / num2;
}
```

Now update the higher-order function to accept the callbacks:

```js
function calculator(num1, num2, operatorCallbackFunction) {
  console.log("Getting ready to calculate the values of", num1, "and", num2);
  console.log("With function:", operatorCallbackFunction.name);
  const result = operatorCallbackFunction(num1, num2);
  console.log("Done! Your answer will be returned shortly!");
  return result;
}

console.log(calculator(1, 1, add));
console.log(calculator(5, 4, subtract));
console.log(calculator(2, 2, multiply));
console.log(calculator(100, 10, divide));
```

On top of being able to organize your code better, you can continue to customize the `calculator` function to have whatever additional functionality it needs, along with the mathematical operations. You don't have to copy and paste the `calculator` functionality in multiple places, which helps keep your code DRY.

To test yourself on how well you understand callbacks you can try to add a percentage or power function to the above code.

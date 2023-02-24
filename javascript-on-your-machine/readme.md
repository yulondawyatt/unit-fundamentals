# JavaScript on Your Machine

Up until this point, you've been running JavaScript code through online IDEs. While convenient, most developers write code on their local machines in text editors like VSCode. To get into a good workflow that leverages all the tools you need to build full web applications, you'll need to be able to run code on your computer.

Running JavaScript on your machine is quite doable, thanks to NodeJS. JavaScript was initially created to only run in web browsers. However, some developers created NodeJS and released it for anyone to use in 2009. NodeJS allows you to run JavaScript outside of the browser and you can now use it to build all kinds of applications.

In this lesson, you'll learn how to use NodeJS to run JavaScript files on your machine as well as how to run a NodeJS REPL.

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe what NodeJS is and why it's important.
- Install NodeJS on your local machine through Homebrew.
- Run JavaScript files with the `node` command.
- Access command line arguments with the `node` command.
- Run JavaScript in the NodeJS REPL.

---

## What is NodeJS?

Recall that JavaScript is just text. To have that text take some action, we have to have a program to interpret the text. For example, take a look at the following JavaScript code.

```js
console.log("🚀 3... 2... 1... Blast off!");
```

While that code might mean something to you, it doesn't naturally mean something to a computer. By running the code above through a JavaScript interpreter, the code will do something, such as print a statement to the console.

Since its creation, JavaScript has grown from a niche browser tool to a powerful coding language and has become much more popular and has far more utility. You can now use JavaScript to build programs, not just animations on the web.

There's much more to the story of [NodeJS](https://en.wikipedia.org/wiki/Node.js) and you can read the wikipedia entry if you are interested in learning more.

## Installing NodeJS

You can check that Node has been installed correctly by running the following command.

```bash
node -v
```

You should receive a version equal to or above `v16.0.0`. If you do not have NodeJS on your computer, please refer to the Computer Setup Guide.

## Running JavaScript files

Once you have `node` installed, running JavaScript files is pretty straightforward.

First, you'll need to create a JavaScript file. To do so, you'll create a file with the `.js` extension.

```bash
touch example.js
```

Inside that file, write some JavaScript code.

```js
console.log("🌌 Space. The final frontier.");
```

Then, use the `node` command from the command line, passing the path to the file as the argument.

```bash
node example.js
```

Your code will be run, and any output will be displayed in your terminal window.

### Expected output

It's essential to remember that when running a file with the `node` command, the only thing that will be outputted to the terminal is the logged code. For example, take a look at the following code.

```js
function waveHello() {
  return "👋 Hello!";
}

waveHello();
```

If you place the code above inside a `.js` file and then run it with the `node` command, you will not see any output. That doesn't mean the code is not being run. The code _is being run_, but there is no output (i.e., nothing that is logged) to display. If you want to see the result of the code, you'll need to log it.

```js
const result = waveHello();
console.log(result);
```

## Accessing command line arguments

One benefit to running JavaScript from the command line is that you can access information about the machine running the code. For example, NodeJS gives you access to a lot of information about `node` and the machine running NodeJS through the `process` object.

```js
console.log(process);
```

If you were to run the above in a `.js` file with the `node` command, you would see a very dense object printed to your terminal, with many keys and values about NodeJS and your machine.

```js
{
 version: 'v16.4.0',
 arch: 'x64',
 platform: 'darwin',
 release: {
 name: 'node',
 sourceUrl: 'https://nodejs.org/download/release/v16.4.0/node-v16.4.0.tar.gz',
 headersUrl: 'https://nodejs.org/download/release/v16.4.0/node-v16.4.0-headers.tar.gz'
 },
 // ...
}
```

The `process` object in its entirety is not incredibly useful for the kinds of projects you'll be building, but there are a few keys on the object that are pretty interesting. For example, the `argv` key represents all of the arguments passed to the `node` command.

```js
console.log(process.argv);
// [
// '/path/to/node',
// '/path/to/your/example.js'
// ]
```

`process.argv` returns an array of strings. The first element of the array is the file path to the `node` program. The second argument is the file path to `.js` file that was run. And every element afterward will be arguments added after the file.

For example, imagine your `example.js` file contains the following code, which accesses the third element of the `process.argv` array and passes it as an argument to the `waveHello()` function.

```js
function waveHello(name) {
  let result = "👋 Hello!";
  if (name) {
    return `👋 Hello, ${name}!`;
  }
  return result;
}

const name = process.argv[2];
const result = waveHello(name);
console.log(result);
```

Next, look at the following command you could run on the command line.

```bash
node ./example.js Jamie
```

If you were to run the command above, the output would be:

```
👋 Hello, Jamie!
```

### Multiple words

On the command line, each argument is separated by a space. If you wanted to write a program that allowed you to add a phrase as an argument, you would need to wrap the phrase in double quotes.

```bash
node ./example.js "Jamie B."
```

### Different data types

Every value passed as an argument will be interpreted as a string. If you choose to pass in other data types, you will need extra work to evaluate them. For example, take a look at the command below.

```bash
node ./example.js 3 5 10
```

This would result in the following values for `process.argv`.

```
[
 "/path/to/node",
 "/path/to/your/example.js".
 "3",
 "5",
 "10"
]
```

## The NodeJS REPL

Using a REPL can be helpful for just testing out your code. Thankfully, with the `node` command, you can access a JavaScript REPL from the command line.

To open up the `REPL`, just type `node`. Your terminal prompt will change to look something like the following.

```
Welcome to Node.js v16.4.0.
Type ".help" for more information.
>
```

You can now type JavaScript and run it by pressing return.

```
Welcome to Node.js v16.4.0.
Type ".help" for more information.
> console.log("👀 JavaScript in the terminal!?");
👀 JavaScript in the terminal!?
undefined
>
```

In the code above, a `console.log()` statement is written, and the return key is pressed. That statement is then logged immediately afterward. Finally, the return value of the statement (i.e., `undefined`) is shown.

Instead of logging, you can also evaluate expressions.

```
> "⭐️" + " " + "Let's go!";
"⭐️ Let's go!"
```

### Running multiple lines

The JavaScript REPL is best used for running short lines of code. However, you can write longer statements.

If you start a statement on one incomplete line and hit return, three dots will appear, showing the REPL waiting for you to finish.

```
> if (emoji === "⭐️") {
... console.log("You're a star!");
... }
undefined
```

If you ever see the three dots unexpectedly, that likely means the syntax you previously wrote is somehow incorrect. You can exit the statement by pressing `Control` + `C`.

Remember that if you start a lengthy statement, you can't go back to previous lines. If you're testing out several lines of code, creating a new `.js` file is likely better.

### Exiting the REPL

To exit the REPL, you can either press `Control` + `D` or `Control` + `C` twice. Lastly, you can type `.exit`.

```
>
(To exit, press Ctrl+C again or Ctrl+D or type .exit)
```

# Reference Types

Recall that earlier on, you learned about primitive types. In particular, you learned about five different primitive types in JavaScript you would often use: `number`, `string`, `boolean`, `undefined`, and `null`. Notice that list excludes arrays and objects.

In this lesson, you'll learn about reference types. Reference types are different than primitive types in a few crucial ways. By the end of this lesson, you'll be able to distinguish between the two types and learn about destructive and non-destructive methods.

## Learning Objectives

By the end of this lesson, you should be able to:

- Differentiate between primitive and reference types.
- Mentally evaluate code blocks that use primitive and reference types.
- Differentiate between destructive and non-destructive methods.

---

## Primitive vs. reference types

Primitive types include the following data types:

- number
- string
- boolean
- undefined
- null
- bigInt (not covered in class)
- symbol (not covered in class)

All other data types are reference types. This includes objects and arrays, functions, and other datatypes you have not seen yet, like maps and sets.

Primitive and reference types differ because primitive types are _immutable_ while reference types are _mutable._ This means that primitive types, once created, cannot be changed, although they can be copied. Reference types, on the other hand, _can be changed._ You will see many examples of what this means below.

### Everything is an object?

In reading about JavaScript, you may have heard the phrase, "everything in JavaScript is an object." This is not quite true. But more things are objects than you might initially guess.

For example, look at the code below after each expression is what that expression would evaluate. Does anything surprise you?

```js
typeof "string"; //> 'string'
typeof undefined; //> 'undefined'
typeof null; //> 'object'
typeof {}; //> 'object'
typeof []; //> 'object'
typeof function myFunction() {}; //> 'function'
```

It doesn't make much sense that `null` returns `'object'` when it is a primitive type. Just as confusing is that an array returns an `'object'`. And while it makes sense that the function returns `'function'`, a function is, in fact, a special kind of object!

When you start coding it's important to figure out when to peak under the hood and understand why something is the way it is and when it is better to not worry about it and rather focus on how to use something and then go down the rabbit hole later.

When you take a course, much thought is put into the order of information and how much depth in every lesson, since learning is a process of many weeks, months or years. This is meant to help your learning be as productive as possible: by learning the right things, in the right depth, at the right time.

A lot of schools teach you that you need to fully understand something before attempting to do something. But coding is different. Coding is a back and forth process between getting some information, trying to use it, reviewing the information, and trying some more. A great deal of understanding will happen for you when you are coding.

A lot of hows and whys of coding won't make sense until you start building something and experience the challenges first-hand.

This lesson will introduce you to some concepts that you'll need to be aware of but won't fully understand until you need to utilize them in a project or have a bug in your code that will require this kind of knowledge to solve.

For now, keep in mind:

- Anything that _is not_ an explicit primitive type in JavaScript is a reference type. That includes objects, arrays, and functions.
- `typeof` _is not_ a good way to determine whether or not something is a primitive or reference type.

### Passing values

Read through the code below. What do you expect will be logged to the console?

```js
let isSunny = true;
let isHappy = isSunny;

console.log(isHappy);

isSunny = false;

console.log(isHappy);
// true
console.log(isSunny);
// false
```

In this case, `isSunny` evaluates to `true`, which is then assigned to `isHappy`. This means that when `isHappy` is logged, its value is `true`.

But what about the second case? Does changing `isSunny` change the value of `isHappy`? No, it does not. This is because `true` and `false` are booleans, which are primitive types. When passing a primitive type from one variable to another, a copy is made. That means _there is no connection between variables that store the same primitive type._

### Passing references

When declaring things with variables, one of two things can happen. A new value is stored in a new place in the computer's memory (which is what you saw with the boolean example above) or a new reference to the same place in the computer's memory will be created.

Read through the code below. What do you expect will be logged to the console?

```js
let luciano = { isHappy: true };
let hollie = luciano;

console.log(hollie);
//  { isHappy: true }

luciano.isHappy = false;

console.log(hollie);
//  { isHappy: false }
```

Similar to before, guessing what the value of `hollie` was straightforward. When logged, `luciano` and `hollie` will look like the same object with a key of `isHappy` and a value of `true`.

However, the second case may be a surprise. When passing a reference type, like an object, from one variable to another, a copy _is not made._ Instead, the reference to the place in memory of the first object is passed to the variable. That means that the variables `luciano` and `hollie` point to the same object stored in the computer's memory.

Therefore when `luciano.isHappy` is set to `false`, the object referenced by both `luciano` and `hollie` is changed.

This same effect happens with arrays since arrays are also reference types.

```js
let lucianoHobbies = ["drawing", "coding"];
let hollieHobbies = lucianoHobbies;

lucianoHobbies.push("playing piano");
hollieHobbies.push("cooking");

console.log(lucianoHobbies);

// [ 'drawing',  'coding', 'playing piano', 'cooking']
```

In the code above, `lucianoHobbies` and `hollieHobbies` point to the same array. This means when values are added to them with `.push()`, it updates the shared array. Therefore, all of Hollie's hobbies are pushed into Luciano's hobby list.

To get a separate array, you must copy the original array. You can do this with the spread operator.

```js
let lucianoHobbies = ["drawing", "coding"];
let hollieHobbies = [...lucianoHobbies];

lucianoHobbies.push("playing piano");
hollieHobbies.push("cooking");

console.log(lucianoHobbies);

// [ 'drawing','coding', 'playing piano',]

console.log(hollieHobbies);
// [ 'drawing', 'coding', 'cooking' ]
```

You can also copy objects using `Object.assign()`

```js
let luciano = { isHappy: true };
let hollie = Object.assign({}, luciano);

console.log(hollie);

luciano.isHappy = false;

console.log("Luciano", luciano);
// { isHappy: false }
console.log("Hollie", hollie);
// { isHappy: true }
```

### Variable declarations

Recall that declaring variables with `const` protects that variable named from being _assigned_ again. However, it is still possible to update the values within.

This means you can use `const` to assign reference types and update the inner values however you want.

```js
const hobbies = ["drawing", "coding", "playing piano"];
hobbies.push("running");
console.log(hobbies);
//> ['drawing', 'coding', 'playing piano', 'running']
```

However, if you try to overwrite the entire array, it will throw an error:

```js
hobbies = ["knitting", "playing violin"];
```

Take a moment to think why the authors of JavaScript chose to design the language this way.

### Equality

The difference between primitive and reference types also explains why the following code acts the way it does.

Primitive types are compared based on their values.

```js
console.log("cheerful" === "cheerful"); // true
const mood1 = "jovial";
const mood2 = "jovial";
console.log(mood1 === mood2); // true
```

However, reference types compare whether they point to the same place in memory. The values are not compared.

```js
console.log(["carefree"] === ["carefree"]); // false
console.log({ mood: "joyful" } === { mood: "joyful" }); // false

const constance = luciano;
console.log(luciano === constance); // true
console.log(luciano === hollie); // false
```

You can, however, compare values inside of reference types:

```js
const moods1 = ["jocular", "content"];
const moods2 = ["gleeful", "jocular"];
console.log(moods1[0] === moods2[1]); //> true
```

## Destructive vs. Non-destructive operations

The language of coding introduces many new words and sometimes uses words in ways we don't expect. Learning the right words and meanings for coding will help you communicate your thoughts and ideas with other coders.

Destructive operations are those operations that mutate (change) the underlying reference type on which they are called. A destructive method doesn't have to "delete" a value for it to be destructive. Rather, it destroys the original version and replaces it with the new version.

### Non-destructive operations

In contrast, non-destructive operations _do not_ mutate the underlying reference.

All methods called on primitive types are non-destructive: they return a new value based on the method called. However, the underlying primitive type stays the same.

```js
const pangram = "Grumpy wizards make a toxic brew for the jovial queen.";

// toUpperCase() returns an uppercase version of the pangram
console.log(pangram.toUpperCase());

// afterward, the original pangram is the same (not mutated)
console.log(pangram);

// To save the version you can declare a new variable

const yellingPangram = pangram.toUpperCase();
console.log(yellingPangram);
```

### Destructive operations

However, arrays do have a mix of methods that can update the underlying array and other methods that do not.

### Basic array mutations

Methods like `.push()`, `.pop()`, `.shift()`, and `.unshift()` are all destructive methods in that they modify the array.

```js
const breakfast = ["coffee", "cereal", "orange", "coffee", "coffee"];

breakfast.pop();

console.log(breakfast);
```

### .concat()

The `.concat()` method is a helpful way of joining one or more arrays together. It is a non-destructive method.

```js
const lucianoOrder = ["coffee", "panini", "cake"];
const hollieOrder = ["coffee", "soup", "fries"];

const entireOrder = lucianoOrder.concat(hollieOrder);

console.log(lucianoOrder);
// [ 'coffee', 'panini', 'cake' ]
console.log(hollieOrder);
// [ 'coffee', 'soup', 'fries' ]
console.log(entireOrder);
// [ 'coffee', 'panini', 'cake', 'coffee', 'soup', 'fries' ]
```

As you can see in the example above, `lucianoOrder` and `hollieOrder` stay the same. Instead, `.concat()` returns a new array with their combined orders. If not assigned to a variable like `allOrders`, the return value of `.concat()` would be lost.

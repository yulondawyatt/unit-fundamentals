# Common Methods and Tools

## Learning Objectives

- Be able to describe why JavaScript has built-in methods and tools.
- Be able to name a few names and functionality common built-in methods for numbers, strings and arrays.
- Be able to use resources like MDN or W3 schools to look up methods and implement them in order to solve coding problems.

<hr>

## Class activity

By the end of this program, you'll have built the skills to learn to code whatever you need on your own. You'll be able to teach yourself a new coding language, a new framework, and other tools.

To gain such a skill, you must begin practicing teaching yourself smaller things first and then work your way up.

In this class activity, your instructor will assign you into small groups and give you 15-25 minutes to research your JavaScript method. In that time you will write a short summary and create a demonstration and present it to your classmates. Your demonstration should be 2-5 minutes long and you should be prepared to share your written summary and demo with your classmates.

While this activity lists a number of common methods there are still more out there. Your goal is to learn how to research and utilize the tools, not memorize them all.

> **Note**: be on the lookout for methods that don't change the original data compared to the ones that change it.

For example, if you reverse an array, does the original array stay the same or does it change?

```js
const numsArray = [1, 2, 3, 4, 5];

console.log(numsArray.reverse());
console.log(numsArray);
```

Also notice that a method like `.pop()` not only changes the original array, but also returns the item that was removed.

```js
const poppedNumber = numsArray.pop();
console.log(poppedNumber);
console.log(numsArray);
```

These small details end up playing a critical role in how you design your logic in your functions.

| Group Number/Category |           Method(s)            |
| :-------------------: | :----------------------------: |
|  **Number methods**   |
|           1           |          `.toFixed()`          |
|           2           | `Math.ceil()` & `Math.floor()` |
|           3           |          `.toFixed()`          |
|           4           |  `Math.min()` & `Math.max()`   |
|  **String methods**   |
|           5           |        `.toLowerCase()`        |
|           6           |           `.slice()`           |
|           7           |         `.substring()`         |
|   **Array methods**   |
|           8           |         `.includes()`          |
|           9           |          `.indexOf()`          |
|          10           |          `.concat()`           |

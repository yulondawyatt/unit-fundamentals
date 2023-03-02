# Looping over Arrays of Objects

## Introduction

You've learned about loops, arrays, and objects. Each fundamental concept and skill by itself is not too hard to learn. But the challenge increases as you combine what you've learned to solve things.

## Learning Objectives

- Access deeply nested properties one at a time
- Learn the `for of` loop
- Loop over an array of objects to access deeply nested properties

<hr>

## Access deeply nested properties

Accessing nested properties is much like putting on pants. Usually, the best way is to put one pant leg on at a time. The same can be said for nested object properties: access each level and test it one level at a time. It can be tempting to do it all in one step, but for many of us, it can lead to awkward downfalls.

### Access an object inside an array

Here we have an array of crayons. Each crayon has a color and another property that lists if it is one of the original colors.

```js
const crayons = [
  { color: "red", original: true },
  { color: "blue", original: true },
  { color: "caput mortuum", original: false },
];
```

Let's access the blue `color` property. Start with the whole array:

```js
console.log(crayon);
```

Then the blue object:

```js
console.log(crayon[1]);
```

Then the blue object color property:

```js
console.log(crayon[1].color);
```

### Access an array element inside an object

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
};
```

First step:

```js
console.log(adventurer);
```

Second step:

```js
console.log(adventurer.backpack);
```

Third step:

```js
console.log(adventurer.backpack[2]);
```

### Access an object within an object

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
  pet: {
    name: "Kath",
    species: "kitten",
    type: "ferocious",
  },
};
```

First step:

```js
console.log(adventurer);
```

Second step:

```js
console.log(adventurer.pet);
```

Third step:

```js
console.log(adventurer.pet.name);
```

### Access a deeply nested object

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
  pet: {
    name: "Kath",
    species: "kitten",
    type: "ferocious",
    pet: {
      name: "Eee",
      species: "bat pup",
      type: "dangerously adorable",
      belongings: ["health insurance card", "diving flippers"],
    },
  },
};
```

First step:

```js
console.log(adventurer);
```

Second step:

```js
console.log(adventurer.pet);
```

Third step:

```js
console.log(adventurer.pet.pet);
```

Fourth step:

```js
console.log(adventurer.pet.type);
```

Can you figure out how to access the `diving flippers`?

### Access a function inside an object

You can put functions inside objects and call them.

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
  pet: {
    name: "Kath",
    species: "kitten",
    type: "ferocious",
    pet: {
      name: "Eee",
      species: "bat pup",
      type: "dangerously adorable",
      belongings: ["health insurance card", "diving flippers"],
    },
  },
  move(direction) {
    return `The adventurer moves one step ${direction}`;
  },
};
```

First step:

```js
console.log(adventurer));
```

Second step:

```js
console.log(adventurer.move);
```

Oops, nothing happens! The function must be invoked.

```js
console.log(adventurer.move("east"));
```

Notice we've been using a similar syntax for built-in methods. For example, we've done the following:

```js
myString.toLowerCase();
```

### Access a very deeply nested object

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
  pet: {
    name: "Kath",
    species: "kitten",
    type: "ferocious",
    pet: {
      name: "Eee",
      species: "bat pup",
      type: "dangerously adorable",
      belongings: ["health insurance card", "diving flippers"],
    },
  },
  food: [
    {
      name: "onion",
      layers: {
        first: {
          layer: {
            layer: {
              layer: "chewy center",
            },
          },
        },
      },
    },
  ],
  move(direction) {
    return `The adventurer moves one step ${direction}`;
  },
};
```

Try to access the layer with the `chewy center` string.

<details><summary>Solution</summary>

```js
console.log(adventurer.food[0].layers.first.layer.layer.layer);
```

</details>

## Call a function from inside a function

```js
const adventurer = {
  name: "Rynn",
  backpack: ["boomerang", "tent", "Tums"],
  pet: {
    name: "Kath",
    species: "kitten",
    type: "ferocious",
    pet: {
      name: "Eee",
      species: "bat pup",
      type: "dangerously adorable",
      belongings: ["health insurance card", "diving flippers"],
    },
  },
  move(direction) {
    return `The adventurer moves one step ${direction}`;
  },
  castSpell(spell) {
    return function () {
      return `${spell.toUpperCase()}!!!`;
    };
  },
};
```

```js
console.log(adventurer.castSpell("fireball")());
```

## For of loop

Return to the crayons array.

```js
const crayons = [{color: "red", original: true}, {color: "blue", original: true}. {color: "caput mortuum", original: false}]
```

Let's loop over it and log each color name.

```js
const crayons = [
  { color: "red", original: true },
  { color: "blue", original: true },
  { color: "caput mortuum", original: false },
];
```

Let's try to write a loop:

```js
for (let i = 0; i > crayons.legnth; i++) {
 console.log(crayon[i]color);
}
```

This loop fails because there are a lot of typos. For loops are pretty verbose, and there are a lot of places to mistype things.

Let's fix the loop:

```js
for (let i = 0; i < crayons.length; i++) {
  console.log(crayons[i].color);
}
```

Now it works. But what if there was an easier way?

There is! It's called a `for of` loop. Let's try it.

```js
for (let crayon of crayons) {
  console.log(crayon.color);
}
```

This syntax is much shorter and easier to read.

Start with the keyword `for`. Then declare a variable like `crayon`. You can make this variable anything you want, like `asdf`, but something more descriptive will be easier to maintain. Then use the keyword `of` and the name of the array you want to iterate over.

The for of loop is less flexible than a regular for loop. It can only iterate over every item (no skipping, no going back steps).

Try one more loop - log the values of the adventurer's backpack.

```js
for (let item of adventurer.backpack) {
  console.log(item);
}
```

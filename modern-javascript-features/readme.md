# Modern JavaScript Features

JavaScript has changed a lot since its creation in the 90s. New features and functions have been added infrequently since that time. One of the biggest jumps in features for JavaScript was with the release of ECMAScript 6. The features introduced in ES6 are typically referred to as `modern`.

In this lesson, you'll read about ECMAScript, the specification document that manages JavaScript. You'll also learn about some of the powerful features introduced by ES6.

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe what ECMAScript is.
- Apply destructuring when assigning variables.
- Apply destructuring in function definitions.
- Use object shorthand to construct objects.
- Write functions using the arrow function expression syntax.
- Implement the spread syntax.
- Implement the rest syntax.

---

## ECMAScript

ECMAScript is a scripting language that is the basis for JavaScript. You can think of it as a blueprint for implementing JavaScript. [The ECMA International organization standardizes the ECMAScript](https://en.wikipedia.org/wiki/Ecma_International).

Technically, there can be different implementations of JavaScript depending on the environment. This means the following:

- "Different implementations" means that a particular method could be written slightly differently, depending on the JavaScript implementation. This could lead to minor differences in how the same method operates depending on the JavaScript implementation.
- "Depending on the environment" means that, for example, the JavaScript running in Safari could be slightly different than the one running in Chrome. This could lead to some functionality not working in particular browsers.

In general, this is not something to worry about now. These nuances will only become meaningful when working on projects deployed to the web.

### Newer versions of JavaScript

One of the biggest jumps for JavaScript was the introduction of ES6 (because it succeeded ES5, which was released in 2009), also called ES2015 (because it was released in teh year 2015). Although not quite new anymore, it continues to be a significant milestone for JavaScript in that the changes introduced improved some of the weaker parts of JavaScript.

Since ES6, a new system of smaller updates that are added annually has been in place and it is unlikely such a major update will happen again. The newer the feature, the more critical it is to look at its compatibility with different browsers and versions of NodeJS.

In this course, we will cover standard features in the JavaScript industry. While there are dozens of features to learn, this content will only cover those most useful and standardized. You should feel free to explore -- keep in mind that some newer features can be more fragile depending on the environment.

## Many ways to do the same thing

With coding, you'll learn there are multiple ways to solve a problem and often multiple syntaxes to do the same thing.

Learning a few ways to do the same thing can feel frustrating at first, but the following examples represent common ways to do things JavaScript. As you research on your own, you'll likely see examples of the following things.

## Destructuring

Destructuring refers to the _pulling apart_ of objects and arrays, allowing you to declare multiple variables simultaneously. It can be an excellent tool for cleanly creating variables. Destructuring can occur both when declaring variables with `let` and `const` as well as in function definitions.

### Variable destructuring

Variable destructuring can be used by declaring variables with `let` or `const` and then using the appropriate syntax, as shown below.

#### Objects

Take a look at the code example below, which uses destructuring.

```js
const planet = {
  name: "Mercury",
  orbitalPeriodInDays: 88,
  radiusInMiles: 1516,
};

const { name, orbitalPeriodInDays } = planet;
console.log(name); //> "Mercury"
console.log(orbitalPeriodInDays); //> 88
```

The code above does the following:

1. Creates a new object with two key-value pairs. The names of the keys are essential for destructuring.

1. Creates two new constant variables: `name` and `orbitalPeriodInDays`. Curly braces (i.e., `{}`) must be added before and after the variables. A comma separates each variable name. Finally, the variable names _must match the keys exactly._

1. In the following lines, each variable is logged. The values of each key are now stored in variables with the same name.

You may have noticed that not every key was assigned to a new variable. `radiusInMiles` was not captured in a new variable. It is not required to apply destructuring to every key.

It's important to note that the names of the variables must be the same as the keys inside the object. While an error will not be thrown if you create a different variable name, it will return `undefined`.

```js
const planet = {
  name: "Mercury",
  orbitalPeriodInDays: 88,
  radiusInMiles: 1516,
};

const { surfaceArea } = planet;
console.log(surfaceArea); //> undefined
```

There's much more you can do with object destructuring. You can rename variables and even set defaults. You will only be asked to reproduce the above effects for now, but you can read more about object destructuring at the link below.

- [MDN: Destructuring assignment (Object destructuring)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring)

#### Arrays

Take a look at the code example below, which uses destructuring.

```js
const planets = ["Mercury", "Venus", "Earth", "Mars"];

const [mercury, venus, earth] = planets;
console.log(mercury); //> "Mercury"
console.log(earth); //> "Earth"
```

The syntax above is similar to object destructuring, but instead of curly braces, you will use square brackets (i.e., `[]`) around the variables you want to create. Also, similar to object destructuring, you need not apply destructuring to every element in the array.

Unlike object destructuring, you can name your variables however you want. Instead, the _order_ of your variables is what matches each element in the array.

```js
const planets = ["Mercury", "Venus", "Earth", "Mars"];

const [first, second, third] = planets;
console.log(first); //> "Mercury"
console.log(third); //> "Earth"
```

Finally, if you create more variables than there are elements in the array, those variables that do not match with an element will be `undefined`.

```js
const planets = ["Mercury", "Venus", "Earth", "Mars"];

const [first, second, third, fourth, fifth] = planets;
console.log(first); //> "Mercury"
console.log(fifth); //> undefined
```

There's much more you can do with array destructuring. You can set default values as well as skip over some elements of the array. You will only be asked to reproduce the above effects for now, but you can read more about object destructuring at the link below.

- [MDN: Destructuring assignment (Array destructuring)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#array_destructuring)

### Parameter destructuring

You can also use destructuring in function definitions. For this, you will _not_ use `const` or `let`; otherwise, the syntax will remain the same.

Before seeing this as an action, look at the code below.

```js
function planetRadiusInKilometers(planet) {
  const radiusInMiles = planet.radiusInMiles;
  return radiusInMiles * 1.609;
}

const planet = {
  name: "Mercury",
  orbitalPeriodInDays: 88,
  radiusInMiles: 1516,
};
planetRadiusInKilometers(planet); //> 2439.244
```

The function above takes an entire `planet` object and then returns a number, converting miles to kilometers.

You can apply destructuring to this function in the following way.

```js
function planetRadiusInKilometers({ radiusInMiles }) {
  return radiusInMiles * 1.609;
}
```

The function above is functionally the same as the previous version of it. The function above expects an object as its first argument, which you can see from the curly braces being used for destructuring.

This approach has a few pros and cons. The function is now shorter, and it is much clearer what data type the first argument should be. On the other hand, you no longer have access to the entire object as there's no variable to reference. Additionally, if a non-object is passed into the function, you may end up with a strange result, like in the example below.

```js
function planetRadiusInKilometers({ radiusInMiles }) {
  return radiusInMiles * 1.609;
}

planetRadiusInKilometers(1516); //> NaN
```

In the example above, the argument the function is called with is a number instead of an object. Instead of failing outright, the function runs and ends up returning `NaN`. The `radiusInMiles` parameter is assigned the value of `undefined` because there is no `radiusInMiles` key in the number `1516`. `undefined` is then multiplied by a number that returns `NaN`.

This is all to say that parameter destructuring can be a powerful tool but it's not the right tool for every job.

## Object shorthand

Take a look at the code below.

```js
const name = "Mars";
const orbitalPeriodInDays = 687;
const planet = {
  name: name,
  orbitalPeriodInDays: orbitalPeriodInDays,
};
console.log(planet); //> { name: "Mars", orbitalPeriodInDays: 687 }
```

The code above works just fine. Two variables, `name` and `orbitalPeriodInDays`, are created to store individual bits of data. Then, that data is collected into an object called `planet`.

Object shorthand refers to a particular syntax where instead of explicitly assigning a key-value pair, you do so by including a variable with the same name as the key you want.

```js
const name = "Mars";
const orbitalPeriodInDays = 687;
const planet = {
  name,
  orbitalPeriodInDays,
};
console.log(planet); //> { name: "Mars", orbitalPeriodInDays: 687 }
```

Notice in the above object there is no explicit value. JavaScript takes the variable's name and sets it to be the key. It then sets the value stored inside of that variable to be the value. Object shorthand can shorten your code and save you time repeating names.

## Arrow functions

Arrow functions are the newest syntax for functions in JavaScript. Arrow functions are anonymous functions because they don't have a name. Rather, the whole function is assigned to a variable.

```js
const planetRadiusInKilometers = function (planet) {
  const radiusInMiles = planet.radiusInMiles;
  return radiusInMiles * 1.609;
};
```

In the code above, notice that a variable of `planetRadiusInKilometers` is assigned the value of a function. This function includes the `function` keyword but does not have a name. The fact that functions are expressions allows you to create and use functions in as parameters JavaScript.

With newer versions of JavaScript, these functions can be rewritten to use arrow syntax.

```js
const planetRadiusInKilometers = (planet) => {
  const radiusInMiles = planet.radiusInMiles;
  return radiusInMiles * 1.609;
};
```

The above code removes the `function` keyword and instead creates an "arrow" (i.e., `=>`) between the parameter list and the start of the function body. Everything to the right of the first `=` sign is also an expression.

You can even write arrow functions in a single line if your function is short. When the function is one line long and you don't use curly braces, there is an implicit return statement.

```js
const planet = { name: "Mercury", orbitalPeriodInDays: 88 };

const returnPlanetName = (planet) => {
  return planet.name;
};

const returnPlanetOrbitPeriod = (planet) => planet.orbitalPeriodInDays;

console.log(returnPlanetName(planet));
console.log(returnPlanetOrbitPeriod(planet));
```

In the code above, the following has occurred:

- The curly braces (i.e., `{}`) have been removed.
- The `return` keyword has been removed. Anything that follows the arrow (i.e., `=>`) will be returned.

One-line arrow functions should only be used if the function is _very_ short. You cannot have more than a single line if you exclude the curly braces in an arrow function.

For now, you will only be asked to reproduce the above syntax, but you can read more about other powerful features of arrow functions at the link below.

- [MDN: Arrow function expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

## Spread and rest syntax

Spread and rest are two names for the same syntax. Represented by `...`, these three dots perform different operations depending on the context.

### Spread

The spread operator is used to _spread apart_ elements in an array or key-value pairs in an object. It is placed before the variable that needs to be spread.

#### Arrays

```js
const beforeEarth = ["Mercury", "Venus"];
const afterEarth = ["Mars", "Jupiter", "Saturn", "Uranus", "Neptune"];

const allPlanets = [...beforeEarth, "Earth", ...afterEarth];
console.log(allPlanets);
/*
  [
    "Mercury", "Venus",
    "Earth",   "Mars",
    "Jupiter", "Saturn",
    "Uranus",  "Neptune"
  ]
*/
```

In the example above, the following is happening:

1. Two variables are created: `beforeEarth` and `afterEarth`. Each is an array of strings.

1. The `allPlanets` variable is declared and assigned to a new array. Inside this array, `beforeEarth` is _spread apart._ This means that, instead of an array as the first element, all elements inside the `beforeEarth` array will appear before the `"Earth"` string. After the `"Earth"` string, the `afterEarth` array is also spread apart.

1. Finally, `allPlanets` is logged, showing an array of eight elements.

If the spread syntax _were not used,_ it would result in the following:

```js
const allPlanets = [beforeEarth, "Earth", afterEarth];
console.log(allPlanets);
/*
  [
    [ "Mercury", "Venus" ],
    "Earth",
    [ "Mars", "Jupiter", "Saturn", "Uranus",  "Neptune" ]
  ]
*/
```

#### Objects

Objects can also be spread. This can be a helpful way to join one more object together.

```js
const physicalRequirements = {
  visualAcuity: "20/20",
};
const workRequirements = {
  degree: "STEM field",
  minimumYearsOfExperience: 3,
};
const requirements = {
  mustBeUSCitizen: true,
  ...physicalRequirements,
  ...workRequirements,
};

console.log(requirements);
/*
  {
    mustBeUSCitizen: true,
    visualAcuity: '20/20',
    degree: 'STEM field',
    minimumYearsOfExperience: 3
  }
*/
```

In the code above, two objects are created that contain specific requirements for becoming an astronaut. Then, a `requirements` variable is created that includes a new key-value pair and _spreads apart_ all the keys and values from the previous objects. The resulting object has all of the key-value pairs.

Remember that an object can't have two keys of the same name. If more than one spread object has the same key, _the object spread last will overwrite the previous keys._

```js
const mercury = { name: "Mercury", orbitalPeriodInDays: 88 };
const mars = { name: "Mars", orbitalPeriodInDays: 687 };
const planet = {
  ...mercury,
  ...mars,
  orbitalPeriodInDays: 0,
};

console.log(planet);
//> { name: 'Mars', orbitalPeriodInDays: 0 }
```

In the code above, the `planet` variable is assigned to a new object which first contains all the key-value pairs from the `mercury` variable. Those key-value pairs are overwritten by the key-value pairs from the `mars` variable. Then, the `orbitalPeriodInDays` key-value pair is overwritten explicitly at the very end. This leads to the object you see at the end.

### Rest syntax

The rest syntax is just about the opposite of the spread syntax, even though it uses the same three dots. The rest syntax is primarily used in function definitions to access the _rest of the arguments._

```js
function listAstronauts(first, second, ...others) {
  return `${first}, ${second}, and ${others.length} more!`;
}

listAstronauts(
  "Jessica Watkins",
  "Robert Shane",
  "Nicole Mann",
  "Jasmin Moghbeli",
  "Frank Rubio"
);
//> "Jessica Watkins, Robert Shane, and 3 more!"
```

The `listAstronauts()` function is called in the function above with five arguments. However, in the function definition, only the first two are named explicitly. The _rest_ of the arguments are collected into an array called `others`. This array acts like any other. It has a length and can be looped over if needed. This allows for the `listAstronauts()` function to account for a variable number of arguments passed into it.

The rest syntax can also be used when destructuring values stored inside arrays.

```js
function listAstronauts(astronauts) {
  const [first, second, ...others] = astronauts;
  return `${first}, ${second}, and ${others.length} more!`;
}

const astronauts = [
  "Jessica Watkins",
  "Robert Shane",
  "Nicole Mann",
  "Jasmin Moghbeli",
  "Frank Rubio",
];
listAstronauts(astronauts);
//> "Jessica Watkins, Robert Shane, and 3 more!"
```

The code above has changed the function to accept an array under the name `astronauts` instead. Destructuring is then applied to this array to create a `first`, `second`, and `others` variable. The `others` variable is also an array of the _rest of the astronauts._

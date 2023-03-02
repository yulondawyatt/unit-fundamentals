# Data Representation with Code

Code exists to help us solve real problems. The most popular coding languages we use today allow us to express and solve real problems through code in a way that can, at times, read like plain language.

In this lesson, you'll think through how to represent real-world concepts in code. You'll also see a few examples of how to do this independently.

## Learning Objectives

By the end of this lesson, you should be able to:

- Represent object properties in the real world as code.
- Define a collection in terms of code.
- Represent real-world collections of objects through data structures.
- Define the purpose of unique identifiers when working with complex data.

---

## Understanding objects

Look around you -- there are likely lots of different _objects_ that you interact with on a daily basis.

In the context of programming, an object is just about anything. For example, your computer is an object, as is your desk, your chair, and you. Anything that is a noun could be considered an object.

Objects are not verbs, more typically, you can think of them as nouns. Instead, verbs can be conveyed through functions. For example, if you wanted to represent the concept of "running", it would make more sense to use a function. In contrast, you could represent a "runner" as an object.

Why might you want to represent these objects in code?

If you're building an app to track ratings for different hiking paths, you'll need to think about how you want to store that data. Your application will need to represent hikes, locations, and users.

Deciding how to represent these real-world ideas in code is critical for building all kinds of applications.

## Translating the real world

Recall the common data types in JavaScript: booleans; numbers; strings; `undefined`; `null`; and objects, including arrays. When creating a new object, you have different data types to represent that particular object.

For example, consider Mount Rainier, a mountain in Washington state. How might you represent it in code?

```js
const rainier = {
  name: "Mount Rainier",
};
```

To start, you might decide that Mount Rainier should be an object which is a collection of key-value pairs. In contrast to an array, or a simple string, it's easier to organize information in an object.

What other properties does Mount Rainier have that can be represented using JavaScript data types?

```js
// TODO: Update with data.
const rainier = {
  name: "Mount Rainier",
  state: "Washington",
  heightInMeters: 4395,
  isNationalPark: true,
  latitude: 46.8600215,
  longitude: -121.855005,
  hasHiking: true,
  hasSkiing: true,
};
```

The object above is now starting to represent the actual mountain more accurately. You could include a vast amount of data, but it depends on what you want to use it for. Additionally, there's not really a "right" way to always structure your data.

### Nested objects

You can put an object inside an object. Take a look at the new key `location`:

```js
// TODO: Update with data.
const rainier = {
  name: "Mount Rainier",
  heightInMeters: 4395,
  isNationalPark: true,
  activities: ["hiking", "skiing"],
  location: {
    latitude: 46.8600215,
    longitude: -121.855005,
    state: "Washington",
  },
};
```

In the example above, a few changes have taken place:

1. Location information (i.e., `latitude`, `longitude`, and `state`) have all been placed in a new object under the key `location`.
1. A new key of `activities` has been created that points to an array with two strings. These strings take the place of the `hasHiking` and `hasSkiing` keys from the previous iteration.

Is the above structure better or worse than the one before? It's hard to say without knowing what the data will be used for. But there are some benefits to both.

- The first example has a "flatter" structure, meaning you can access all the values using only a single key. Sometimes that can be simpler to think about.
- The second example is more organized in that related data is grouped by keys. And it has `activities` as an array, which means you can update it easily while keeping the organization.

### A few more examples

How you build an object depends on what it should be used for. Here are a few examples of objects, followed by a brief description.

### More detailed object

```js
const person = {
  name: {
    first: "William",
    middle: "Emmett",
    last: "Anderson",
    preferred: "Will",
  },
  birthday: {
    month: "December",
    day: 2,
    year: 1990,
  },
  phone: {
    mobile: "5551901789",
    home: "5556549912",
  },
};
```

The object above is very detailed and has key-value pairs broken down into different categories. It might be helpful for something like an address book.

## Collections

Above, you had information about one person. If you imagine that that information was for a contacts app, you'd want many person objects.

You can have an array of objects, which is often called a `collection`.

Here we see a simple collection of flavors and their popularity:

```js
const flavors = [
  { name: "Cherry", popularity: 3 },
  { name: "Watermelon", popularity: 4 },
  { name: "Orange", popularity: 2 },
  { name: "Lemon", popularity: 4 },
];
```

The above array contains a list of objects representing a list of some kind. Each object inside represents a flavor of something and its popularity. If you ever need to represent a collection of objects, you'll likely use an array.

### Tracking objects in a collection

If you think about a banking app, there is a lot of data you'd keep track of for an account:

- address
- bank account total
- phone number
- type of bank account
- user name

This user's account's data could all change: the person could:

- move
- add money to the account
- update their phone number
- open multiple savings accounts
- legally change their name

So how can you make sure that you are always updating the correct object?

```js
const accounts = [
  { id: 1, amount: 2015.3 },
  { id: 2, amount: 50.05 },
  { id: 3, amount: 450.0 },
  { id: 5, amount: -1.05 },
  { id: 6, amount: 2.35 },
];
```

Each object above represents a simplified user's account. Because the amounts aren't necessarily unique, a new key, `id`, was added to help distinguish each object. IDs can be helpful when you want to represent a real-world idea that needs some unique descriptor and they are never expected to change.

Here is a more detailed view of one user account object.

```js
const oneAccount = {
  id: 5,
  accountType: "Checking",
  interestRate: 0.00000001,
  firstName: "Rynn",
  lastName: "Tynn",
  email: "rTynn@yoyodene.net",
  phoneNumber: "718-867-5309",
  address: {
    street: "45-56 Davis Street",
    state: "NY",
    zip: 11101,
  },
  amount: -1.05,
  pastTransactions: [-100, -30, -20, -600, -3, -55, -63, -150, 1000],
};
```

Imagine that a user logs in to their account. The user Rynn, has two bank accounts, a saving's account with an `id` of 1 and a checking account with an `id` of 5. Rynn selects the checking account so they can deposit $1000 into the correct account. The app would look up the account by the `id` number and update the amount. Rynn could also change multiple details and the account could still be found, because the id never changes.

# Looping over Arrays of Objects

## Learning Objectives

- Access deeply nested properties one at a time
- Learn the `for of` loop
- Loop over an array of object to access deeply nested properties

<hr>

## Guiding Questions

- Can you make an array inside of an object that is inside of an array?

  - Can you model this with code?

- Can a function that is inside an object return another object?
- Can you model this with code?

- Here is an array of songs from an album

```js
const so = [
  "Don't Give Up",
  "Sledgehammer",
  "Big Time",
  "In Your Eyes",
  "Mercy Street",
  "Shaking the Tree",
];
```

- How would you loop over them with a `for` loop?

- How would you loop over them with a `for of` loop?

- What are the pros of using a `for` loop? What are cons?

- What are the advantages of using a `for of` loop? What are the disadvantages?

Using the object below:

- Log the show name
- Log each actor object
- Log each the first season's year
- Log the first season's episode objects
- Log the first season's episode names
- Only log the episodes that have a rating less than 8
- Create a new array and push all the episodes that have a rating higher than 8 into it

```js
const hcf = {
  showName: "Halt and Catch Fire",
  actors: [
    {
      character: "Joe McMillan",
      playedBy: "Lee Pace",
    },
    {
      character: "Gordon Clark",
      playedBy: "Scoot McNairy",
    },
    {
      character: "Cameron Howe",
      playedBy: "Mackenzie Davis",
    },
    {
      character: "Donna Clark",
      playedBy: "Kerry Bishé",
    },
    {
      character: "John Bosworth",
      playedBy: "Toby Huss",
    },
  ],
  seasons: [
    {
      name: 1,
      year: 2014,
      episodes: [
        {
          name: "I/O",
          number: 1,
          imdbRating: 8.0,
        },
        {
          name: "FUD",
          number: 2,
          imdbRating: 7.9,
        },
        {
          name: "High Plains Hardware",
          number: 3,
          imdbRating: 7.5,
        },
        {
          name: "Close to the Metal",
          number: 4,
          imdbRating: 8.1,
        },
        {
          name: "Adventure",
          number: 5,
          imdbRating: 8.1,
        },
        {
          name: "Landfall",
          number: 6,
          imdbRating: 8.0,
        },
        {
          name: "Giant",
          number: 7,
          imdbRating: 7.7,
        },
        {
          name: "The 214s",
          number: 8,
          imdbRating: 8.6,
        },
        {
          name: "Up Helly Aa",
          number: 9,
          imdbRating: 8.8,
        },
        {
          name: "1984",
          number: 10,
          imdbRating: 8.0,
        },
      ],
    },
  ],
};

console.log(hcf);
```

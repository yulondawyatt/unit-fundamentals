# Loops

## Learning Objectives

- Explain the purpose and utility of loops
- Write a `while` loop with a variable number of iterations.
- Write a `for` loop with a variable number of iterations.
- Use the `break` and `continue` keywords to modify loop execution.

<hr>

## Guiding Questions

- What is the purpose of loops? Feel free to reference the reading or documentation.

- Take a look at the following code. Before running it, make a guess as to what you think it will do.

  ```js
  let sheep = 0;
  console.log("Counting sheep...");
  while (sheep < 5) {
    sheep++;
    console.log(`${sheep} sheep...`);
  }
  ```

- What would happen if instead of the condition being `sheep < 5`, it was `sheep < 1`? Why?

- What would happen if instead of the condition being `sheep < 5`, it was `sheep < 0`? Why?

- What would happen if instead of the condition being `sheep < 5`, it was `sheep > -1`? Why?

- Take a look at the following code. Before running it, make a guess as to what you think it will do.

  ```js
  let sheep = 10;
  console.log("Counting sheep...");
  while (sheep > 0) {
    console.log(`${sheep} sheep...`);
    sheep--;
  }
  ```

- Take a look at the following code. Before running it, make a guess as to what you think it will do.

  ```js
  function countSheep(limit) {
    let sheep = 0;
    console.log("Counting sheep...");
    while (sheep < limit) {
      sheep++;
      console.log(`${sheep} sheep...`);
    }
  }

  countSheep(7);
  ```

- Take a look at the following code. Before running it, make a guess as to what you think it will do.

  ```js
  function countSheep(limit) {
    console.log("Counting sheep...");
    for (let sheep = 1; sheep <= limit; sheep++) {
      console.log(`${sheep} sheep...`);
    }
  }

  countSheep(7);
  ```

- A `for` loop is made up of an initial expression, condition expression, and an increment expression. Define each of these terms in your own words.

- When does the increment expression of a `for` loop run?

- What conditions would need to happen for a `for` loop to run infinitely?

## A quick introduction to the ternary operator

The ternary operator is shorthand for an `if-else` statement. You don't need to use it but you might see it a lot in other people's code.

Let's convert the following code to a ternary operation to see it in action.

```js
const pet = "rhino";
let isDangerous;

if (pet === "rhino") {
    isDangerous = true;
} else {
    isDangerous = false;
}
```

This would become:

```js
const pet = "rhino";

const isDangerous = pet === "rhino" ? true : false;
```

The part after the `?` is code that will run if the conditional statement is true.

The part after the `:` is code that will run if the conditional statement is not true.

Ternary operations require fewer lines of code than a normal `if-else` statement, but it's highly debatable whether the code is easier to read.

Readable code is always preferable to succinct code. The ternary operator is introduced here because it is popular among JavaScript developers, but often it's better to use an if/else.

If you ever find yourself trying to write a nested ternary operation, don't do it. Be kind to yourself and other people who may read your work and write easy to follow code.

---

## Practice questions

> The answers can be found [here](https://github.com/javascript-repositories/js1-lesson-answers/blob/module-3-lesson-1/js/script.js).

<h5 class="question">Question 1</h5>

Convert the function below to an arrow function:

```js
function multiply(a, b) {
    return a * b;
}
```

<h5 class="question">Question 2</h5>

Convert the function below to an arrow function:

```js
function() {
    console.log("Hello");
}
```

<!--
<h5 class="question">Question 3</h5>

Add a method to the object below that returns its colour property:

```js
const frog = {
    colour: "green"
};
```

<h5 class="question">Question 4</h5>

Create an IIFE that logs the current date and time. -->

<h5 class="question">Question 3</h5>

Convert the if statement below to use a ternary operator:

```js
const animal = "mongoose";

let difficultToSpell = false;

if (animal === "hippopotamus") {
    difficultToSpell = true;
}
```

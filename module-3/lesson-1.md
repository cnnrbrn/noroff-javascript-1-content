# Lesson 1 - Arrow functions and the ternary operator

## Fat arrow functions

We've worked with a few different types of functions up until now:

**Declared function:**

```js
function doSomething(anArgument) {
    console.log(anArgument);
}
```

**Function expression**

```js
const doSomething = function(anArgument) {
    console.log(anArgument);
};
```

**Anonymous function**

```js
function(anArgument) {
    console.log(anArgument);
}
```

ES6 introduced what are known as `fat arrow` or `arrow` functions, so called because of their use of this token: `=>`.

When using arrow functions, you don't use the word function to define them.

Arrow functions are anonymous, you don't declare them with a name.

Here is the function expression from above written as an arrow function:

```js
const doSomething = anArgument => {
    console.log(anArgument);
};
```

We can write this on one line:

```js
const doSomething = anArgument => {
    console.log(anArgument);
};
```

Here is the anonymous function re-written using fat arrow syntax:

```js
anArgument => {
    console.log(anArgument);
};
```

You can see there is no `function` keyword and there is now a `fat arrow`: `=>`.

If the function has only one argument, you don't need the parenthesis:

```js
const doSomething = anArgument => {
    console.log(anArgument);
};
```

```js
anArgument => {
    console.log(anArgument);
};
```

If the function has only one statement in it, you can omit the braces:

```js
const doSomething = anArgument => console.log(anArgument);
```

```js
anArgument => console.log(anArgument);
```

If the function has no arguments the parenthesis are required:

```js
const doSomething = () => console.log("hello");
```

```js
() => console.log("hello");
```

If the function has more than one argument the parenthesis are required:

```js
const doSomething = (argument1, argument2) => console.log(argument1, argument2);
```

```js
(argument1, argument2) => console.log(argument1, argument2);
```

A function always returns a value, even if you don't explicitly add a return statement. If there is no return statement, the function returns `undefined`.

> You'll often see `undefined` displayed after entering code directly in the console. This is because Chrome displays the return value of the last statement. If there is no explicit return value, the return value is undefined.

Let's return a value from an arrow function:

```js
const sum = (a, b) => a + b;
```

The `return` keyword is implicit in arrow functions, we can leave it out if body of the function consists of one statement.

<a id="ternary"></a>

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

<h5 class="question">Question 3</h5>

Add a method to the object below that returns its colour property:

```js
const frog = {
    colour: "green"
};
```

<h5 class="question">Question 4</h5>

Create an IIFE that logs the current date and time.

<h5 class="question">Question 5</h5>

Convert the if statement below to use a ternary operator:

```js
const animal = "mongoose";

let difficultToSpell = false;

if (animal === "hippopotamus") {
    difficultToSpell = true;
}
```

---

-   [Go to lesson 2](2)

---

# Lesson 1

In this lesson we will look at:

-   callback functions - passing functions into functions
-   forEach loops
-   the setTimeout method
-   the setInterval method

## Functions as arguments - passing functions into functions

Often called `callbacks`, it is very common to pass functions as arguments to other functions and have the receiving function execute them.

<iframe src="https://scrimba.com/c/cMgggbHG" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cMgggbHG" target="_blank">Scrimba link</a>

## forEach loops

The `forEach` loop is an alternative to the `for` loop.

When you use a `forEach` function, you will pass in a function to be executed by the `forEach` function for each item in the array you are looping over.

It does have some limitations though, such as the inability to use `break` or `continue`.

<iframe src="https://scrimba.com/c/cJggwKAN" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cJggwKAN" target="_blank">Scrimba link</a>

## setTimeout

The `setTimeout` method (function) is used to execute a function after a specified period of time.

It has the following structure:

```js
setTimeout(function () {
    // do something
}, 1000);
```

It has two required arguments:

1. the function to be executed
2. the delay - the delay in milliseconds before the function is executed

<iframe src="https://scrimba.com/c/cLgggqTQ" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cLgggqTQ" target="_blank">Scrimba link</a>

## setInterval

The `setInterval` method is similar to `setTimeout` but it executes a function at a certain interval until it is cleared.

It has the following structure:

```js
setInterval(function () {
    // do something
}, 1000);
```

<iframe src="https://scrimba.com/c/czLLpgfv" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/czLLpgfv" target="_blank">Scrimba link</a>

---

## Lesson Task

There are practice questions in the master branch of [this repo](https://github.com/NoroffFEU/lesson-task-js1-module2-lesson1).

Attempt the answers before checking them against the answers in the `script.js` file in the [answers branch](https://github.com/NoroffFEU/lesson-task-js1-module2-lesson1/tree/answers) of the repo.

---

-   [Go to lesson 2](2)

---

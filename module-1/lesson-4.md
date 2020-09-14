# Lesson 4 - Creating HTML in functions

This lesson covers:

-   function arguments
-   returning values from functions, together with a practical example
-   creating HTML inside a function from the values inside an array

---

## Function arguments

Function arguments are values that get passed into functions.

Technically, in function declarations the variables are called `parameters`.

In the code below, `name` is the parameter.

```js
// declare a function with one parameter called name
function printName(name) {
    console.log(name);
}
```

<!--
The argument becomes a variable available to the code inside the function.

When we call the function using round brackets like this: -->

When we call the function using round brackets the value that is passed in to the function parameter is called an argument.

```js
// call the printName function and pass in the value "Sofie". "Sofie" is an argument
printName("Sofie");
//
```

What we pass in in the brackets becomes the value of `name` in the function. In this case, `name` will receive the value `"Sofie"`.

So the console log inside the function will display `Sofie` in the console.

We want to be able to pass different values into a function so that the code inside can perform the same actions on different values (data).

<img src="/images/js1/function-explanation.png" alt="Argument explanation" style="max-width:600px">

The Scrimba below takes a further look at function arguments.

<iframe src="https://scrimba.com/c/crqy9NuP" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/crqy9NuP" target="_blank">Scrimba link</a>

## Returning values from functions

We can return a value from a function, and we can assign that return value to a variable:

```js
function returnAValue() {
    // the value after return statement is what gets returned from the function
    return "This is the return value";

    // any code after a return statement will never be reached
}

// the return value of the returnAValue function will be assigned to the myValue variable
const myValue = returnAValue();

console.log(myValue);
// This is the return value
```

The Scrimba below looks at returning values from functions.

<iframe src="https://scrimba.com/c/czLNwafP" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/czLNwafP" target="_blank">Scrimba link</a>

---

## An example of using the return value from a function

Below is an example of using the return value of a function.

In the Scrimba a simple age-checking function for a website is created.

<iframe src="https://scrimba.com/c/ceqmb6fB" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/ceqmb6fB" target="_blank">Scrimba link</a>

## Creating an HTML string with a function

Using functions to create HTML with the values inside an array is a common task you will perform when fetching data from APIs.

In this Scrimba:

-   an array is passed into a function as an argument
-   an HTML string is created inside the function from items in the array
-   the string is returned from the function and assigned to a variable
-   the variable is assigned to the innerHTML property of an existing HTML element

<iframe src="https://scrimba.com/c/ceqmWphQ" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/ceqmWphQ" target="_blank">Scrimba link</a>

---

## Lesson Task

There are practice questions in the master branch of [this repo](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson4).

Attempt the answers before checking them against the answers in the [answers branch](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson4/tree/answers) of the repo.

---

-   [Go to the module assignment](ma)

---

# Lesson 1 - Introductory concepts

In this lesson we'll look at:

-   using the browser console
-   declaring variables with the `const` and `let` keywords
-   a different way to create strings with backticks
-   accessing object properties using brackets-
-   functions as properties of objects

## The browser

All references to the "browser" refer to [Chrome](https://www.google.com/chrome/) or [FireFox](https://www.mozilla.org/en-US/firefox/new/).

## The browser console

In the video below we'll take a look at logging variable values using the console.

<iframe src="https://player.vimeo.com/video/443132927" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

## ES6

`ECMAScript` (`ES`) is the official specification for JavaScript. It decides what features should be in the language.

`ES6`, or `ES2015`, was released in 2015 and introduced many improvements to the language after a long gap in updates to the specification. New features are now continuously being added.

`ES6` is often, slightly confusingly, used to refer to the modern versions of JavaScript.

In the Programming Foundations course we didn't use any modern features of the language, but we will be using them throughout the JavaScript 1 course.

> You can check the browser support for a feature (JavaScript and CSS) by using [caniuse.com](https://caniuse.com/)

<a id="const-let"></a>

## `const` and `let`

In the Programming Foundations course we used `var` to declare every variable.

`ES6` introduced the `const` and `let` keywords for declaring variables.

A key difference between `const` and `let` is that `let` can have its value reassigned, where as `const` cannot.

If we declare a variable using `const` and assign it a value:

```js
const count = 1;
```

we cannot reassign its value - we can't give it a different value.

We can't do this

```js
count = 2;
```

or this

```js
count = count + 1;
```

There are more details on `const` and `let` in the Scrimba below.

The cast begins with a brief look at the `undefined` value.

<iframe src="https://scrimba.com/c/cDkbEWTM" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cDkbEWTM" target="_blank">Scrimba link</a>

## Strings using backticks `

Previously we've seen that we can create strings using double or single quotes, and that you should pick one and use it consistently (for any Noroff code use double quotes).

There is another way to create strings, with backticks `. On many keyboards the key is in the top left.

Using backticks gives us an easy way to split strings across lines:

```js
const sentences = `First sentence.
                   Second sentence.`;
```

This is a far cleaner way to get new lines in strings than using either double or single quotes.

<iframe src="https://player.vimeo.com/video/443988703" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/creating-strings-with-backticks" target="_blank">Code from the video</a>

## Accessing object properties using brackets

Previously we have accessed object properties using dot `.` notation.

We can also access them using brackets `[]`, with the key of the property as the value inside the brackets:

```js
const pet = {
    type: "dog"
};

console.log(pet["type"]);
// dog

// this is the same as
console.log(pet.type);
// dog
```

<iframe src="https://scrimba.com/c/cMgvkECv" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cMgvkECv" target="_blank">Scrimba link</a>

## Methods - Functions as properties of objects

We've previously seen `objects` with properties having `string`, `number` or `boolean` values.

```js
const dog = {
    name: "Burt",
    age: 7,
    dangerous: false
};

console.log(dog.age);
// 7
```

Objects can also have `functions` as properties:

```js
const dog = {
    name: "Burt",
    age: 7,
    dangerous: false,

    // bark is a property with a function as its value
    bark: function () {
        console.log("Woof!");
    }
};
```

If we log the `bark` property, the function declaration will be logged:

```js
console.log(dog.bark);

// function() {
//    console.log("Woof!");
// }
```

Because the `bark` property is a function, we can call it like any other function:

```js
dog.bark();
// Woof!
```

Functions inside objects are often called `methods`.

<iframe src="https://scrimba.com/c/cMgvJKHK" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cMgvJKHK" target="_blank">Scrimba link</a>

## Acivities

#### Watch

[YoutTube video: ECMAScript, TC39, and the History of JavaScript](https://www.youtube.com/watch?v=gytOcNFV1dM)

## Lesson Task

There are practice questions in the master branch of [this repo](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson1).

Attempt the answers before checking them against the answers in the `script.js` file in the [answer branch](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson1/tree/answer) of the repo.

---

[Go to lesson 2](2)

---

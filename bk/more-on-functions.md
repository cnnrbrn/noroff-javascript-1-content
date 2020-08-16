# Lesson 1 - More on functions

This first lesson covers some new concepts regarding functions that we need to address as we'll be using a lot of functions.

The concepts discussed here should become easier to understand once you start using them in your code.

We will get back to coding in lesson 2.

## Expressions

In JavaScript, an expression is any code that evaluates (or resolves) to a value.

There are two types of expressions:

-   those that assign a value to a variable
-   those that just have a value without assigning it

This is an example of the first type, where the `number` value `10` gets assigned to variable called `y`.

```js
const y = 10;
```

This is an example of the second type, where the expression evaluates to `10`, but doesn't get assigned to a variable.

```js
5 + 5;
```

This another example of the first type, where the value assigned to the variable is a `function`.

```js
const y = function () {
    // do some stuff
};
```

Here is another example of the second type, where the value the expression resolves to is a `function`, but doesn't get assigned to a variable:

```js
function() {
    // do some other stuff
}


```

## Function declarations vs function expressions

So far when we have used functions, we have `declared` them:

```js
function doSomething() {
    // do something here
}
```

This is called a `function declaration` and it creates a `named function` - the function has a name: `doSomething`.

We use that name to call the function:

```js
doSomething();
```

Functions can also be anonymous, they can be declared without a name:

```js
function () {
    console.log("I don't have a name");
}
```

This is, as we saw above, an expression, and it's value is a function. It's a `function expression`.

We can assign the function expression to a variable:

```js
const myValueIsAFunction = function () {
    console.log("I don't have a name");
};
```

The variable `myValueIsAFunction` has a function as its value, and it can be called like a declared function:

```js
myValueIsAFunction();
// I don't have a name
```

## Callback functions - functions as arguments

Previously, we've passed different kinds of values into function arguments.

> You can enter the code examples below in to the browser console to follow along, or save them in a .js file

```js
function logTheArgument(someFunction) {
    console.log(someFunction);
}
```

We've passed in `strings` and `numbers`:

```js
logTheArgument("Hello");
// Hello

logTheArgument(50);
// 50
```

In module 1, lesson 4, we passed in arrays of objects and looped through them:

```js
function makeGenres(genreArray) {
    // loop through the genreArray array
}

// create an empty array and pass it in to the makeGenres function
const genres = [];
makeGenres(genres);
```

We can also pass functions in as arguments, and call the function within the parent function. These are called `callback functions`.

Because an anonymous function is a valid expression in JavaScript, we can pass an anonymous function in to a function:

```js
function logTheArgument(someFunction) {
    console.log(someFunction);
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function () {
    console.log("I am in the anonymous function");
});
```

The code above logs the function, prints the function definition itself out, but doesn't call it, so the function is not executed.

The function itself gets displayed in the console:

```js
ƒ () {
    console.log("I am in the anonymous function");
}
```

If we change this line

```js
console.log(someFunction);
```

to this

```js
someFunction();
```

the function will be called (we're using round brackets to call the function that's passed in like we would call any function).

```js
function logTheArgument(someFunction) {
    someFunction();
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function () {
    console.log("I am in the anonymous function");
});
```

This time the function is called, and the console log is executed and prints its message to the console:

```js
// I am in the anonymous function
```

This might be better explained with an `alert`:

```js
function logTheArgument(someFunction) {
    alert(someFunction);
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function () {
    console.log("I am in the anonymous function");
});
```

If you run this code, the function definition is displayed in an alert window.

Change this

```js
alert(someFunction);
```

back to this

```js
someFunction();
```

and the function gets called and the console log message is displayed.

---

It's probably a little difficult to read, passing in functions like that.

You can assign the function to a variable (creating a function expression), and then pass it in.

```js
// assign the function to a variable
const myFunction = function () {
    console.log("I am in the function stored in the variable");
};
```

Full example:

```js
function logTheArgument(someFunction) {
    someFunction();
}

// assign the function to a variable
const myFunction = function () {
    console.log("I am in the function stored in the variable");
};

// call the logTheArgument function and pass in the variable whose value is a function
logTheArgument(myFunction);
```

You can also declare a function and then pass it in:

```js
// declare the function
function myFunction() {
    console.log("I am in the function stored in the variable");
}
```

Full example:

```js
function logTheArgument(someFunction) {
    someFunction();
}

// declare the function
function myFunction() {
    console.log("I am in the function stored in the variable");
}

// call the logTheArgument function and pass in the declared function
logTheArgument(myFunction);
```

Use whichever method you find easiest to read and write.

---

## Acivities

#### Read

medium.com: [Function Declarations vs Function Expressions](https://medium.com/@mandeep1012/function-declarations-vs-function-expressions-b43646042052)

#### Watch

[LinkedIn Learning: JavaScript Essential Training](https://www.linkedin.com/learning/javascript-essential-training-3/)

Watch the following videos:

Section 4. Functions and Objects:

-   Anonymous functions

---

-   [Go to lesson 2](2)

---

# Lesson 1 - More on functions

First up in this module, we need to cover some new concepts regarding functions, as we are going to be using a lot of functions.

The concepts discussed here should become easier to understand once you start using them in your code.

We will get back to coding as soon as these concepts have been addressed.

## Expressions

In JavaScript, an expression is any code that evaluates (or resolves) to a value.

There are two types of expressions:
- those that assign a value to a variable
- those that just have a value without assigning it

This is an example of the first type, where the `number` value `10` gets assigned to variable called `y`.
```js
const y = 10
```

This is an example of the second type, where the expression evaluates to `10`, but doesn't get assigned to a variable.
```js
5 + 5
```

This another example of the first type, where the value assigned to the variable is a `function`.

```js
const y = function() {
    // do some stuff
}
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


## IIFE

IIFE stands for `I`nstantly `I`nvoked `F`unction `E`xpression.

In programming, `invoke` is another word for `call`.

We saw above that this is what a `function expression` may look like:

```js
function() {
    console.log("Hi!");
}
```

To call a function we use round brackets - parenthesis - `()`, and we can call a function expression by wrapping it in round brackets, and using the usual way (`()`) at the end of the expression to call it:

```js
(function() {
    console.log("Hi!");
})();
```

## Hoisting

Function declarations are "lifted up" - hoisted - by the JavaScript engine to the top of the code, no matter where they are written. This makes them available to be called from anywhere, including before they are declared.

In the code below, we can call the `doSomething` function before it's declared.

```js
aDeclaredFunction();

function aDeclaredFunction() {
    console.log("I am a declared function");
}
```

Function expressions are not hoisted, they are not lifted up from where they are written in the code, so you can't do this:

```js

aFunctionExpression();

const aFunctionExpression = function() {
    console.log("I am a function expression");
};
```

The above code produces the following error:

```js
Uncaught ReferenceError: Cannot access 'aFunctionExpression' before initialization
```

## Callback functions - functions as arguments

Previously, we've passed different kinds of values into function arguments.

> You can enter the code examples below in to the browser console to follow along, or save them in a .js file

```js
function logTheArgument(valueToLog) {
    console.log(valueToLog);
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
function logTheArgument(valueToLog) {
    console.log(valueToLog);
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function() {
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
console.log(valueToLog);
```

to this
```js
valueToLog();
```

the function will be called (we're using round brackets to call the function that's passed in like we would call any function).


```js
function logTheArgument(valueToLog) {
    valueToLog();
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function() {
    console.log("I am in the anonymous function");
});
```

This time the function is called, and the console log is executed and prints its message to the console:

```js
// I am in the anonymous function
```

This might be better explained with an `alert`:


```js
function logTheArgument(valueToLog) {
    alert(valueToLog);
}

// call the logTheArgument function and pass in an anonymous function
logTheArgument(function() {
    console.log("I am in the anonymous function");
});
```

If you run this code, the function definition is displayed in an alert window.

Change this 

```js
alert(valueToLog);
```

back to this

```js
valueToLog();
```

and the function gets called and the console log message is displayed.

---

It's probably a little difficult to read, passing in functions like that.

You can assign the function to a variable, and then pass it in.

```js
// assign the function to a variable
const myFunction = function() {
    console.log("I am in the function stored in the variable");
};
```

Full example:

```js
function logTheArgument(valueToLog) {
    valueToLog();
}

// assign the function to a variable
const myFunction = function() {
    console.log("I am in the function stored in the variable");
};

// call the logTheArgument function and pass in the variable whose value is a function
logTheArgument(myFunction);
```



---


## Acivities

#### Read

flaviocopes.com: [JavaScript Expressions](https://flaviocopes.com/javascript-expressions/)

---
- [Go to lesson 2](2) 
---
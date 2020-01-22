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
}
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
doSomething();

function doSomething() {

}

```


## Callback functions - functions as arguments




#### setTimeout


#### setInterval


## Acivities

#### Read

flaviocopes.com: [JavaScript Expressions](https://flaviocopes.com/javascript-expressions/)

---
- [Go to lesson 2](2) 
---
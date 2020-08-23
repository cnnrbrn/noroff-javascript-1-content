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
const doSomething = function (anArgument) {
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
const doSomething = (anArgument) => {
    console.log(anArgument);
};
```

We can write this on one line:

```js
const doSomething = (anArgument) => {
    console.log(anArgument);
};
```

Here is the anonymous function re-written using fat arrow syntax:

```js
(anArgument) => {
    console.log(anArgument);
};
```

You can see there is no `function` keyword and there is now a `fat arrow`: `=>`.

If the function has only one argument, you don't need the parenthesis:

```js
const doSomething = (anArgument) => {
    console.log(anArgument);
};
```

```js
(anArgument) => {
    console.log(anArgument);
};
```

If the function has only one statement in it, you can omit the braces:

```js
const doSomething = (anArgument) => console.log(anArgument);
```

```js
(anArgument) => console.log(anArgument);
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

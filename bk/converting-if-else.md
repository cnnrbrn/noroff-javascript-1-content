## Converting an if-else-if to a switch

We looked at `switch` statements in Module 1, Lesson 3 of Programming Foundations, but we haven't coded one yet.

Let's convert the `if-else-if` statement that checks which array to assign to the `arrayToLoopThrough` variable to a `switch` statement.

This is our current code:

```js
const buttonId = event.target.id;

let arrayToLoopThrough = [];

if (buttonId === "action") {
    arrayToLoopThrough = actionGames;
} else if (buttonId === "shooter") {
    arrayToLoopThrough = shooterGames;
} else if (buttonId === "rpg") {
    arrayToLoopThrough = rpgGames;
}
```

When you have multiple `else-if` statements, it's time to consider a `switch` statement to make the code more readable and maintainable.

We begin a `switch` statement with the value we are checking in brackets. In this case we are checking the value of `buttonId`.

```js
switch (buttonId) {
}
```

We then create a `case` block for every value we want to check for. We'll add the check for `"action"` first:

```js
switch (buttonId) {
    case "action":
    // do something if buttonID === "action"
}
```

This is similar to writing:

```js
if (buttonId === "action") {
    // do something if buttonID === "action"
}
```

Let's make the array assignment inside the `case` block and then exit the switch with a `break` statement:

```js
switch (buttonId) {
    case "action":
        arrayToLoopThrough = actionGames;
        break;
}
```

If we don't use a `break` statement the code will keep going and move on to the next `case`.

Let's add the other cases:

```js
switch (buttonId) {
    case "action":
        arrayToLoopThrough = actionGames;
        break;

    case "shooter":
        arrayToLoopThrough = shooterGames;
        break;

    case "rpg":
        arrayToLoopThrough = rpgGames;
        break;
}
```

We now have all the checks we previously had when using the `else-if` statements.

We need to add a `default` statement block in case the `buttonId` is not equal to any of those strings.

```js
switch (buttonId) {
    case "action":
        arrayToLoopThrough = actionGames;
        break;

    case "shooter":
        arrayToLoopThrough = shooterGames;
        break;

    case "rpg":
        arrayToLoopThrough = rpgGames;
        break;

    default:
        // if buttonId is not equal to any of "action", "shooter" or "rpg", assign an empty array to arrayToLoopThrough
        arrayToLoopThrough = [];
}
```

Now `arrayToLoopThrough` will be assigned an empty array if `buttonId` doesn't match any of the values in the `case` statements.

We don't need to initilise `arrayToLoopThrough` with a value now.

Full code:

```js
const buttonId = event.target.id;

let arrayToLoopThrough;

switch (buttonId) {
    case "action":
        arrayToLoopThrough = actionGames;
        break;

    case "shooter":
        arrayToLoopThrough = shooterGames;
        break;

    case "rpg":
        arrayToLoopThrough = rpgGames;
        break;

    default:
        arrayToLoopThrough = [];
}
```

If we didn't add the `break` statements, the code would keep "falling through" to the next case and eventually the default statement, and the code in the default statement would always run, meaning `arrayToLoopThrough` would always be assigned an empty array.

> If you find yourself with a `return` statement inside a case block, you don't need the `break` statement as the `return` will exit the switch. Remember, no code after a `return` statement will get called.
>
> The break statement here will never be reached:
>
> ```js
> case "action":
>   return true;
>   break;
> ```

The main advantage of a `switch` statement over multiple `else-if` statements is readbility. If there were ten buttons instead of three, the `switch` code would be far easier to read and update.

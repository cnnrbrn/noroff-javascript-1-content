## setInterval

The `setInterval` method creates a timer that repeatedly calls a function at a specified interval.

It has two required arguments:

1. the function to be executed
2. the delay - the interval in milliseconds (thousands of a second) between function executions

Let's log the current time every second.

First we'll create the function that logs the time:

```js
function logTime() {
    console.log(new Date());
}
```

Next we'll pass the function and the number `1000` to `setInterval`. 1000 milliseconds is 1 second.

```js
setInterval(logTime, 1000);
```

If you run the code above you will see the current time logged every second. Increase or decrease the milliseconds to see it in action.

This code will keep running as long as the browser tab it's in is open. It's not a good idea to have code endlessly runnning like this - we need a way to stop it.

The return value from `setInterval` is a number value used to indentify the timer that is created by `setInterval`.

If we assign the return value to a variable, we can use that variable to cancel the timer and stop futher execution of the function.

The timer's id will be stored in `intervalId`:

```js
const intervalId = setInterval(logTime, 1000);
```

We want to stop the timer after the function has been called 5 times. We'll create a variable and give it a value of 0 and then increment (add one to it) every time the function is called. After the function has been called five times we'll cancel the timer.

```js
function logTime() {
    // first log the current date/time
    console.log(new Date());

    // if the counter is equal to 4 it means the function has been called 5 times (because we started the counter at 0)
    // cancel the timer - the logTime function won't be called again
    if (counter === 4) {
        clearInterval(intervalId);
    }

    // add one to the counter variable
    // this is shorthand for count = count + 1
    counter++;
}

// this is the variable we'll increment and use to check how of often the function has been called
let counter = 0;

// The timer's id will be stored in `intervalId`:
const intervalId = setInterval(logTime, 1000);
```

In the above code, the timer will call the function five times and then be cancelled.

---

In `index.html`, there is a `div` with a `counter` class:

```html
<div class="counter"></div>
```

Let's use `setInterval` to change the `innerHTML` of this div to be the value of a counter variable.

First we'll select the div using `querySelector`:

```js
const counterContainer = document.querySelector(".counter");
```

Then we'll create the function (that will update the div's `innerHTML`) and the counter variable:

```js
function updateDiv() {
    // set the div's innerHTML property to be the counter's value
    counterContainer.innerHTML = counter;
    counter++;
}

// we'll start the counter at 1
let counter = 1;
```

Now we'll use `setInterval` to call the function every one-and-a-half seconds:

```js
setInterval(updateDiv, 1500);
```

Run this code and you'll see the `counter` variable's value is displayed inside the div.

We don't want this to run forever, so let's cancel it after it counts to 4:

Full code:

```js
const counterContainer = document.querySelector(".counter");

function updateDiv() {
    counterContainer.innerHTML = counter;

    // cancel the timer after the counter reaches 4
    if (counter === 4) {
        clearInterval(intervalId);
    }

    counter++;
}

let counter = 1;

const intervalId = setInterval(updateDiv, 1500);
```

---

Check out the [step-8](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-8) branch from the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) to follow the next section.

---

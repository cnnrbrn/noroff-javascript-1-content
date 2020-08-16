## setTimeout

`setTimeout` is similar to `setInterval`, but it only calls a function once after a specified interval. It also has two required arguments:

1. the function to be executed
2. the delay - the delay in milliseconds before the function is executed

The div with a class of `counter` has been replaced by one with a class of `timeout` and a button has been added:

```html
<button class="btn btn-primary timeout">Test setTimeout</button>
<div class="timeout">setTimeout test</div>
```

Let's select the div and then update its `innerHTML` after two seconds using the `setTimeout` method. There are two elements with a class of `timeout` so we need to specify the tag type
when selecting it:

```js
const timeoutContainer = document.querySelector("div.timeout");

// the function to run after the delay
function updateDiv() {
    timeoutContainer.innerHTML = "This was set by the setTimeout function";
}

// 2000 milliseconds = 2 seconds
setTimeout(updateDiv, 2000);
```

The div's innerHTML will be updated after two seconds.

Let's add a CSS class in the function too:

```js
function updateDiv() {
    timeoutContainer.innerHTML = "This was set by the setTimeout function";
    timeoutContainer.classList.add("primary");
}
```

As well as its innerHTML changing, the div will now have a `primary` class added to it after two seconds and be styled accordingly.

---

Let's add a click event listener to the button.

First we'll select both the div and the button using their tag names in the selectors:

```js
const timeoutContainer = document.querySelector("div.timeout");
const timeoutButton = document.querySelector("button.timeout");
```

We'll add the `"click"` event lister to the button and pass in a function called `updateDivAfterClick` as the callback function:

```js
timeoutButton.addEventListener("click", updateDivAfterClick);
```

The first things we want to do in the function are clear the div of its text and add a class called `loader`:

```js
function updateDivAfterClick() {
    // clear the text inside the div
    timeoutContainer.innerText = "";
    // add the class "loader" to the div
    timeoutContainer.classList.add("loader");
}
```

If you run the full code so far

```js
const timeoutContainer = document.querySelector("div.timeout");
const timeoutButton = document.querySelector("button.timeout");

timeoutButton.addEventListener("click", updateDivAfterClick);

function updateDivAfterClick() {
    timeoutContainer.innerText = "";
    timeoutContainer.classList.add("loader");
}
```

you will see the text in the div disappears and the `loader` class adds a CSS loading animation to the div.

Let's let the animation run for three seconds, then remove the class and add the text `"Loaded"`.

```js
// add the text "Loaded" to the div and remove the "loader" class after 3 seconds
setTimeout(function () {
    timeoutContainer.innerText = "Loaded";
    timeoutContainer.classList.remove("loader");
}, 3000);
```

Full code:

```js
const timeoutContainer = document.querySelector("div.timeout");
const timeoutButton = document.querySelector("button.timeout");

timeoutButton.addEventListener("click", updateDivAfterClick);

function updateDivAfterClick() {
    timeoutContainer.innerText = "";
    timeoutContainer.classList.add("loader");

    setTimeout(function () {
        timeoutContainer.innerText = "Loaded";
        timeoutContainer.classList.remove("loader");
    }, 3000);
}
```

## Adding and removing an active class

We want to indicate to the user which button they've clicked.

When the user clicks a button we'll add an `active` class to it.

To avoid having a very long `script.js` file, we've moved the code that selects the buttons from `js/script.js` to `js/buttons.js` and added a link to the new `.js` file in `index.html`:

```html
<!-- other js files here -->
<script src="js/script.js"></script>
<script src="js/buttons.js"></script>
```

> We need to load `js/buttons.js` after `js/script.js` so that we can call the `loadGames` function from `js/buttons.js`.

`js/buttons.js` now contains the code below, and we'll add the `active` class code in this file:

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");

for (let i = 0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
}
```

We saw in Lesson 2 of Module 1 that we can use the `classList` property to see the classes on an element.

Previously we've used `querySelector` to select elements by `class`, `id` and `tag`. We can also select an element by its data attribute.

Let's select the action games button.

```js
const actionButton = document.querySelector("[data-genre='action']");
console.log(actionButton);
// <button class="btn btn-secondary" data-genre="action">Load action games</button>
```

The selector string is wrapped in square brackets and its value is in single quotes because the entire selector string uses double quotes.

To select the RPG button we would change the value from `action` to `rpg`:

```js
const rpgButton = document.querySelector("[data-genre='rpg']");
console.log(actionButton);
// <button class="btn btn-secondary" data-genre="rpg">Load RPG games</button>
```

If we log `actionButton`'s `classList` property we can see it has two classes, `btn` and `btn-secondary`.

```js
console.dir(actionButton.classList);
// value: "btn btn-secondary"
// 0: "btn"
// 1: "btn-secondary"
```

To add a class to an element, we can use the `classList.add()` method. Let's add an `active` class to `actionButton`:

```js
const actionButton = document.querySelector("[data-genre='action']");
actionButton.classList.add("active");
```

If we log `actionButton`'s `classList` property now we'd see the `active` class has been added:

```js
console.dir(actionButton.classList);
// value: "btn btn-secondary active"
// 0: "btn"
// 1: "btn-secondary"
// 2: "active"
```

We need to add the `active` class to whichever button is clicked, and we don't want to select each element button explicitly.

We could add the code that adds the `active` class in the `loadGames` function, but that function is quite long already and adding more code to it will make it difficult to read.

In the `for loop` in `js/buttons.js`, we are adding a click event listener and sending the `loadGames` functon in as a callback.

We can add a second click event listener to each button in that loop.

We are going to call the function that adds the `active` class `handleActiveClass`.

In the for loop we'll pass that in as the function to a second click event listener:

```j
buttons[i].addEventListener("click", handleActiveClass);
```

Full for loop code:

```js
for (let i = 0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
    buttons[i].addEventListener("click", handleActiveClass);
}
```

Inside the loop, we are now adding two click event listeners to every button. Every time a button is clicked, the first listener will execute and the `loadGames` callback function will be calledand then the `handleActiveClass` callback will be called.

Now we need to create the `handleActiveClass` function:

```js
function handleActiveClass(event) {
    console.log(event);
}
```

Just like in the `loadGames` function, there is an argument that we are calling `event`. This is the event object that gets sent every time the user clicks a button, and we can again use `event.target` to know which button was clicked.

```js
function handleActiveClass(event) {
    console.log(event.target);
}
```

`event.target` will give us the button that was clicked, and above we used `classList.add("active")` to add the `active` class.

If we combine those, every button that is clicked will receive the `active` class:

```js
function handleActiveClass(event) {
    event.target.classList.add("active");
}
```

Full code in `js/buttons.js`:

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");

for (let i = 0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
    buttons[i].addEventListener("click", handleActiveClass);
}

function handleActiveClass(event) {
    event.target.classList.add("active");
}
```

Now every time a button is clicked, the `active` class gets added to it. But if we click them all they'll all receive the class and we won't know which one is active.

Every time a button is clicked, we need to remove the `active` class from all the buttons before adding the class to the button that was just clicked.

We are already selecting all the buttons at the top of the file:

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");
```

Inside the `handleActiveClass` function, we can loop through the buttons and, using the for loops counter variable as an index, we can use the `classList.remove()` to remove the `active` class from each button.

```js
function handleActiveClass(event) {
    for (let i = 0; i < buttons.length; i++) {
        buttons[i].classList.remove("active");
    }

    event.target.classList.add("active");
}
```

Every time the function gets called, the for loop will run first and remove the `active` class from all the buttons.

Then, using `event.target`, the button that was just clicked will have the class added to it.

# Lesson 3 - Data attributes and toggling classes

Check out the [step-5](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-5) branch from the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) to follow this lesson.


## Converting an if-else-if to a switch

We looked at `switch` statements in Module 1, Lesson 3 of Programming Foundations, but we haven't coded one yet.

Let's convert the `if-else-if` statement that checks which array to assign to the `arrayToLoopThrough` variable to a `switch` statement.

This is our current code:

```js
const buttonId = event.target.id;

let arrayToLoopThrough = [];

if(buttonId === "action") {
    arrayToLoopThrough = actionGames;
}
else if (buttonId === "shooter") {
    arrayToLoopThrough = shooterGames;
}
else if (buttonId === "rpg") {ugh
    arrayToLoopThrough = rpgGames;
}
```

When you have multiple `else-if` statements, it's time to consider a `switch` statement to make the code more readable and maintainable.

We begin a `switch` statement with the value we are checking in brackets. In this case we are checking the value of `buttonId`.

```js
switch(buttonId) {

}
```

We then create a `case` block for every value we want to check for. We'll add the check for `"action"` first:

```js
switch(buttonId) {

    case "action":
        // do something if buttonID === "action"
}
```

This is similar to writing:

```js
if(buttonId === "action") {
    // do something if buttonID === "action"
}
```

Let's make the array assignment inside the `case` block and then exit the switch with a `break` statement:


```js
switch(buttonId) {

    case "action":
        arrayToLoopThrough = actionGames;
        break;
}
```

If we don't use a `break` statement the code will keep going and move on to the next `case`.

Let's add the other cases:

```js
switch(buttonId) {

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
switch(buttonId) {

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

switch(buttonId) {

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
> ```js
> case "action":
>   return true;
>   break;
> ```

The main advantage of a `switch` statement over multiple `else-if` statements is readbility. If there were ten buttons instead of three, the `switch` code would be far easier to read and update.

## Data attributes

Data attributes are used to store data and information on HTML elements.

They are created by adding a name for the data you want to store to the `data-` prefix.

If we wanted to add a data attribute to the buttons to store their genre information, we would use a data attribute called `data-genre`.

The value of the attribute is assigned using an equals sign like any other attribute:

```js
data-genre="action"
```

Let's add a `data-genre` attribute to each button:

```html
<button class="btn btn-secondary" data-genre="action" id="action">Load action games</button>
<button class="btn btn-secondary" data-genre="shooter" id="shooter">Load shooter games</button>
<button class="btn btn-secondary" data-genre="rpg" id="rpg">Load RPG games</button>
```

This is a better place to store the genre type, as the `id` shouldn't really be used to store meaningful data, but rather for DOM selection and possibly styling, though using classes for styling is considered the better practice.

Let's select the button with an id of `shooter`:

```js
const shooterButton = document.querySelector("#shooter");
```

To access the data attributes on an element, we use its `dataset` property:

```js
console.dir(shooterButton.dataset);
```

This will display a `DOMStringMap` object. Click on it to see its properties:

<img src="/images/js1/dataset-1.png" alt="dataset" style="max-width:300px">

There is one property as the element has only one data attribute.

We can add as many data attributes as we like. Let's add two more to the shooter button, one for `pet` and one for `numberOfGames`:

```html
<button class="btn btn-secondary" data-genre="shooter" data-pet="dog" data-numberOfGames="12" id="shooter">Load shooter games</button>
```
If we log `shooterButton.dataset` now we'll see three data properties:

```js
console.dir(shooterButton.dataset);
```

<img src="/images/js1/dataset-2.png" alt="dataset" style="max-width:300px">

We can access each data property value using dot notation:

```js
console.dir(shooterButton.dataset.genre);
// shooter
```

This is how we can check which button was clicked in the `loadGames` function using data attributes.

Let's remove the extra data attributes from the shooter button and the ids from all the buttons.

```html
<button class="btn btn-secondary" data-genre="action">Load action games</button>
<button class="btn btn-secondary" data-genre="shooter">Load shooter games</button>
<button class="btn btn-secondary" data-genre="rpg">Load RPG games</button>
```

Delete the `shooterButton` variable too as we can't get a button by its id anymore.

Inside the `loadGames` function, the following line won't work:

```js
const buttonId = event.target.id;
```

Replace it with:

```js
const genre = event.target.dataset.genre;
```

- `event` - the click event
- `target` - the element the event happened on
- `dataset` - the data attributes on the element
- `genre` - the value of the `data-genre` attribute


Now we need to change the variable the switch statement is checking from `buttonId` to `genre`:

```js
switch(genre) {
```

The full switch code:

```js
// get genre value from the data-genre attribute
const genre = event.target.dataset.genre;
   
let arrayToLoopThrough;

switch(genre) {

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

---

Check out [step-6](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-6) of the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code). It contains all the code we've now added.

---

## Adding and removing an active class

We want to indicate to the user which button they've clicked.

When the user clicks a button we'll add an `active` class to it.

To avoid having a very long `script.js` file, we've moved the code that selects the buttons from `js/script.js` to `js/buttons.js` and added a link to the new `.js` file in `index.html`:

```html
<!-- other js files here -->
<script src="js/script.js"></script>
<script src="js/buttons.js"></script>
```

> We need to load `js/buttons.js` after `js/script.js` so that we can call the `loadGames` function from `js/buttons.js`. We saw in lesson 1 of this module that JavaScript uses `hoisting` to lift function declarations to the top of the code, no matter where they are placed by the developer, but this doesn't apply to code loaded in different script files.

`js/buttons.js` now contains the code below, and we'll add the `active` class code in this file:

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");

for(let i = 0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
}
```

We saw in Lesson 2 of Module 1 that we can use the `classList` property to see the classes on an element.

Previously we've used `querySelector` to select elements by `class`, `id` and `tag`. We can also select an element by its data attribute.

Let's select the action games button.

```js
const actionButton = document.querySelector("[data-genre='action']");
console.log(actionButton)
// <button class="btn btn-secondary" data-genre="action">Load action games</button>
```

The selector string is wrapped in square brackets and its value is in single quotes because the entire selector string uses double quotes. 

To select the RPG button we would change the value from `action` to `rpg`:

```js
const rpgButton = document.querySelector("[data-genre='rpg']");
console.log(actionButton)
// <button class="btn btn-secondary" data-genre="rpg">Load RPG games</button>
```

If we log `actionButton`'s `classList` property we can see it has two classes, `btn` and `btn-secondary`.

```js
console.dir(actionButton.classList)
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
console.dir(actionButton.classList)
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
for(let i = 0; i < buttons.length; i++) {
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

for(let i = 0; i < buttons.length; i++) {
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

    for(let i = 0; i < buttons.length; i++) {
        buttons[i].classList.remove("active");
    }

    event.target.classList.add("active");
}
```

Every time the function gets called, the for loop will run first and remove the `active` class from all the buttons.

Then, using `event.target`, the button that was just clicked will have the class added to it.

## Activities

### Watch

YouTube: [Switch statements](https://www.youtube.com/watch?v=UeXDAu7SdmY)

---
- [Go to lesson 4](4) 
---
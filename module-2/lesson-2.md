# Lesson 2 - Events

[step-2](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-2) of the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) contains the code completed in Module 1, Lesson 4.

---

Check out the [step-3](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-3) branch from the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) to follow this lesson.

---

## Events

When something happens in the browser - such as a page loading, a form being submitted or a user clicking a button, the DOM sends an `Event`.

We can write code to respond to that event. 

Some examples of events include:

- `click` - when the mouse button is clicked
- `keydown` - when any key is pressed
- `keyup` - when any key is released
- `mouseover` - when the mouse cursor moves over a DOM element or its children elements
- `mouseout` - when the mouse cursor moves off an element  
- `submit` - when a form is submitted

You can find a full list of events [here](https://developer.mozilla.org/en-US/docs/Web/Events).

An event is an object with properties.

## Responding to events

Make sure you are on `step-3` of the repo.

In `js/script.js`, the code that loops over the array of game objects has been wrapped in a function. Because the function is not being called, no games are being displayed.

Because another `div` with a class of `container` has been added to the HTML

```html
<div class="container">
    <input class="text-input" name="firstname">
    <button class="btn btn-primary">Click me</button>
</div>

<div class="container results"></div>
```

the query selector has been updated to include a second class so that we select the right element:

```js
const container = document.querySelector(".container.results");
```

We can select elements with multiple classes the same way we do with CSS: `.container.results`.

Follow along with the code below by adding it to `js/script.js`.

### click event

We've added a button to the HTML

```html
<button class="btn btn-primary">Click me</button>
```

We can listen to events on elements in a few different ways.

We can listen to a click event, for example, by adding an `onclick` attribute and adding code as its value:

```html
<button class="btn btn-primary" onclick="console.log('The button was clicked');">Click me</button>
```

Writing code inline like that will quickly become messy and difficult to read.

We could write a function and call that funtion instead:

```js
function respondToClick() {
    console.log('The button was clicked');
}
```

```html
<button class="btn btn-primary" onclick="respondToClick()">Click me</button>
```

You may see this method used in code examples from time to time, but we want to keep our JavaScript and our HTML separate.


## addEventListener()

> Remove the `onclick` attribute from the button and any code you added to `js/script.js`.

With the `addEventListener` method, we can add a function to the DOM that will be called when an event occurs.

`addEventListener` has two required arguments:

- a `string` indicating which type of event to listen for, e.g. `"click"`
- a function that will be called when the event occurs, a `callback` function

Let's add an event listener to the entire document.

Add this to `js/scripts.js`:

```js
document.addEventListener("click", function() {
    console.log("A click event happened");
});
```

We've added an event listener to the entire document - the whole page - and if you click anywhere on the page the function will be called and `A click event happened` will be logged.

We can declare the function first, and then pass the function name in as the second argument. This may be easier to read:

```js
function callAfterClick() {
    console.log("A click event happened");
};

document.addEventListener("click", callAfterClick);
```

We can also assign the function expression to a variable, and then pass the variable in: 

```js
const callAfterClick = function() {
    console.log("A click event happened")
};

document.addEventListener("click", callAfterClick);
```

> <b>Note: </b> we don't use parenthesis `()` when passing the function in as the second argument, we just use the name of the function (if it's a declared function) or the name of the variable it was assigned to (if it's a function expression).

All of the above three ways to add an event listener are valid. Use the one you find easiest.

---

We added the click event listener to the entire document. Let's add it only to the button.

Select the button using its two classes:

```js
const button = document.querySelector(".btn.btn-primary");
```

Add an event listener with the `addEventListener` method. We'll add a `click` event again:

```js
function callAfterButtonClick() {
    console.log("A click event happened on the button");
};

button.addEventListener("click", callAfterButtonClick);
```

Now, only when we click on the button will the function be called.

#### mouseover

Let's change the event type. We'll change it to `mouseover` which will happen when the mouse cursor moves over the button, similar to how the hover pseudo-class works in CSS.

```js
function callOnHover() {
    console.log("The cursor moved over the button");
};

button.addEventListener("mouseover", callOnHover);
```

Every time you move the cursor over the button the function will be called. You'll need to move the cursor off the button first to get it to fire again.

#### keyup

Let's listen for every time a key is released when we type in the text input.

The event that occurs when a key is released is the `keyup` event.

First we'll select the input by its class:

```js
const textInput = document.querySelector(".text-input");
```

Then we'll delare a function that we'll pass in to the `addEventListener` method:

```js
function callAfterAKeyIsReleased() {
    console.log("A key was released");
};
```

Now we'll call the `addEventListener` method on the `textInput` variable and pass the string `"keyup"` and the `callAfterAKeyIsReleased` function into it:

```js
textInput.addEventListener("keyup", callAfterAKeyIsReleased);
```

Now `A key was released` is displayed in the console every time we type in the input.

## The Event object

The callback function passed in to `addEventListener` - in the last example the callback function is `callAfterAKeyIsReleased` - receives as an argument the Event object, the object that is sent every time the event happens.

In the `callAfterAKeyIsReleased` function, add an argument. We are going to call this argument `event` and we are going to log it:

```js
function callAfterAKeyIsReleased(event) {
    console.dir(event);
    console.log("A key was released");
};
```

Now the event object will be logged to the console every time you press a key.

This is what your console will look like if you type the letter `a`:

<img src="/images/js1/keyboard-event.png" alt="KeyboardEvent" style="max-width:700px">

If you click the arrow in the console, you will see a list of its properties including the `target` property:

<img src="/images/js1/keyboard-event-target.png" alt="KeyboardEvent target property" style="max-width:450px">

The `target` property is the element the event happened on.

Instead of logging `event` in the function, log `event.target`:

```js
function callAfterAKeyIsReleased(event) {
    console.dir(event.target);
};
```

<img src="/images/js1/keyboard-event-target-list.png" alt="KeyboardEvent target properties" style="max-width:340px">

There is a long list of properties on `event.target`. Because this is a `text input`, a lot of the properties it has, such as `checked`, don't apply to it, but all input elements have these properties.

Two important properties on `event.target` are `name` and `value`. 

Inside the function log `event.target.name` and `event.target.value`. We are going send two arguments to the `console.log()` method, the first being a string which will be a label for the property we are logging:

```js
function callAfterAKeyIsReleased(event) {
    console.log("name: ", event.target.name);
    console.log("value: ", event.target.value);
};
```

Every time you type in the input, the `name` and the current `value` of the input are logged.

Later in the course, we'll use the `value` property when filtering games on the page, and both the `name` and `value` properties when working with forms.

---

Check out the [step-4](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-4) branch from the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) to follow the next section.

---

There are now three buttons in `index.html`:

```html
<div class="container">                        
    <button class="btn btn-secondary" id="action">Load action games</button>
    <button class="btn btn-secondary" id="shooter">Load shooter games</button>
    <button class="btn btn-secondary" id="rpg">Load RPG games</button>
</div>
```

The code that loops over the array of games and dislays them is now inside a function called `loadGames`.

Let's call the function to display them when the button with the id of `action` is clicked.

First, let's select the button by its id:

```js
const loadActionGamesButton = document.querySelector("#action");
```

Now we'll use `addEventListener` to listen for a `click` event on the button. The `loadGames` function already exists, so we can just pass it in as the second argument:

```js
const loadActionGamesButton = document.querySelector("#action");

loadActionGamesButton.addEventListener("click", loadGames);
```

Click the button and the `loadGames` function will run and the games will be displayed.

---

In `js/data/`, there are three different files with three different arrays of game objects, `actionGames`, `shooterGames` and `rpgGames`. These are all available to us to use as we are loading them in `index.html`.

We want to display the different arrays depending on which button is clicked.

We could copy the `loadGames` function and make three functions called `loadActionGames`, `loadShooterGames` and `loadRPGGames`. Then we could get each button by its id, and pass a different function into each button's event listener as a callback function:

```js
loadActionGamesButton.addEventListener("click", loadActionGames);
loadShooterGamesButton.addEventListener("click", loadShooterGames);
loadRPGGamesButton.addEventListener("click", loadRPGGames);
```

But this a bad idea. We would have three very similar funtions, the only difference being which array of games they looped over.

Duplicating code like this means there are more lines of unnecessary code to make mistakes in, and it makes it far more difficult to find and fix bugs and to maintain and update.

We want to use the same function no matter which button is clicked, so we need to add the same event listener to all the buttons. Then inside the function we'll figure out which button was clicked and load the appropriate array of games.

We don't want to select the buttons by their ids, we'd then have to add the event listener three times and this is again duplicated code.

Instead we'll select all the buttons by their classes, loop through them and add the event listener inside the loop.

Select all the buttons:

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");
console.log(buttons);
```

As we saw in module 1, lesson 2, `querySelectorAll` will return a `NodeList` of all the selected elements.

<img src="/images/js1/button-nodelist.png" alt="Button NodeList" style="max-width:630px">

We can loop through the list and add the `loadGames` callback to a `click` event listener:

```js
for(let i =0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
}
```

The `loadGames` callback function will now run every time any of the buttons is clicked.

But the function only loops through the `actionGames` array, so no matter which button is clicked the same array of games is displayed.

We need to change which array is looped through depending on which button is clicked. We'll do this by checking the `id` of the button clicked.

In the load games function, give it an argument of `event` and at the top of the function, log the `event.target` property:

```js
function loadGames(event) {
    console.log(event.target);
    // rest of the function code 
```

If you click on the shooter games button, the following will be logged:

```html
<button class="btn btn-secondary" id="shooter">Load shooter games</button>
```

If you use `console.dir` instead, a clickable list of the button's properties will be logged. 

<img src="/images/js1/button-event-target-properties.png" alt="Button event.target properties" style="max-width:630px">

We can see we have access to the `id` property, which we can access like this:

```js
event.target.id
```

At the top of the `loadGames` function, assign the button's id to a variable:

```js
const buttonId = event.target.id;
console.log(buttonId)
```

Click the buttons and you'll see their id gets logged in the console.

The value of the id will decide which array we loop through. 

We'll create a variable to hold the array to loop through. We'll declare it with `let` and give it an empty array as an initial value.

```js
let arrayToLoopThrough = [];
```

Now we'll write an if-else-if statement to set the value of `arrayToLoopThrough`:

```js
if(buttonId === "action") {
    arrayToLoopThrough = actionGames;
}
else if (buttonId === "shooter") {
    arrayToLoopThrough = shooterGames;
}
else if (buttonId === "rpg") {
    arrayToLoopThrough = rpgGames;
}

console.log(arrayToLoopThrough);
```

`arrayToLoopThrough` will now hold a different array value depending on which button was clicked.

The new code in the function:

```js
function loadGames(event) {

    // assign the value of the button id to buttonId
    const buttonId = event.target.id;

    // declare a variable that will hold a different value depending on the button clicked
    let arrayToLoopThrough = [];

    if(buttonId === "action") {
        // if the button with the id of "action" is clicked, assign actionGames to arrayToLoopThrough
        arrayToLoopThrough = actionGames;
    }
    else if (buttonId === "shooter") {
        // if the button with the id of "shooter" is clicked, assign shooterGames to arrayToLoopThrough
        arrayToLoopThrough = shooterGames;
    }
    else if (buttonId === "rpg") {
        // if the button with the id of "rpg" is clicked, assign rpgGames to arrayToLoopThrough
        arrayToLoopThrough = rpgGames;
    }

    // the previous code
    const container = document.querySelector(".container.results");
    let newHTML = "";

    for (let i = 0; i < actionGames.length; i++) {
    // the rest of the previous code ...
}
```

We are still looping through `actionGames` though, so no matter which button has been clicked and which array has been assigned to `arrayToLoopThrough`, only the games in `actionGames` will be displayed.

The solution is to loop over `arrayToLoopThrough` instead. We can replace `actionGames` with `arrayToLoopThrough` in the for loop:

```js
for (let i = 0; i < arrayToLoopThrough.length; i++) {

    let ratingValue = "Not rated";

    if (arrayToLoopThrough[i].rating) {
        ratingValue = arrayToLoopThrough[i].rating;
    }

    const genres = arrayToLoopThrough[i].genres;
    const genresHTML = makeGenres(genres);

    const platforms = arrayToLoopThrough[i].platforms;
    const platformsHTML = makePlatforms(platforms);

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${arrayToLoopThrough[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${arrayToLoopThrough[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                            ${genresHTML}
                            <div class="platforms">${platformsHTML}</div>
                        </div>
                    </div>`;

    newHTML += details;
}
```

Now different games will be displayed when the different buttons are clicked.

---

#### The full code

```js
// select all the buttons by their classes
const buttons = document.querySelectorAll(".btn.btn-secondary");

// loop through each button and add an event listener
for(let i =0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
}

// add an argument called event to the func
function loadGames(event) {

    // assign the value of the button id to buttonId
    const buttonId = event.target.id;

    // declare a variable that will hold a different value depending on the button clicked
    let arrayToLoopThrough = [];

    if(buttonId === "action") {
        // if the button with the id of "action" is clicked, assign actionGames to arrayToLoopThrough
        arrayToLoopThrough = actionGames;
    }
    else if (buttonId === "shooter") {
        // if the button with the id of "shooter" is clicked, assign shooterGames to arrayToLoopThrough
        arrayToLoopThrough = shooterGames;
    }
    else if (buttonId === "rpg") {
        // if the button with the id of "rpg" is clicked, assign rpgGames to arrayToLoopThrough
        arrayToLoopThrough = rpgGames;
    }

    const container = document.querySelector(".container.results");
    let newHTML = "";

    for (let i = 0; i < arrayToLoopThrough.length; i++) {

        let ratingValue = "Not rated";

        if (arrayToLoopThrough[i].rating) {
            ratingValue = arrayToLoopThrough[i].rating;
        }

        const genres = arrayToLoopThrough[i].genres;
        const genresHTML = makeGenres(genres);

        const platforms = arrayToLoopThrough[i].platforms;
        const platformsHTML = makePlatforms(platforms);

        const details = `<div class="card">
                            <div class="image" style="background-image: url(${arrayToLoopThrough[i].background_image});"></div>
                            <div class="details">
                                <h4 class="name">${arrayToLoopThrough[i].name}</h4>
                                <div class="rating">${ratingValue}</div>
                                ${genresHTML}
                                <div class="platforms">${platformsHTML}</div>
                            </div>
                        </div>`;

        newHTML += details;
    }

    container.innerHTML = newHTML;
}

function makeGenres(genreArray) {

    let genreHTML = "";

    for (let i = 0; i < genreArray.length; i++) {
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    return genreHTML;
}

function makePlatforms(platformsArray) {

    let platformsHTML = "";

    for (let i = 0; i < platformsArray.length; i++) {
        platformsHTML += `<span>${platformsArray[i].platform.name}</span>`;
    }

    return platformsHTML;
}
```

#### Without the comments

```js
const buttons = document.querySelectorAll(".btn.btn-secondary");

for(let i =0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", loadGames);
}

function loadGames(event) {

    const buttonId = event.target.id;

    let arrayToLoopThrough = [];

    if(buttonId === "action") {
        arrayToLoopThrough = actionGames;
    }
    else if (buttonId === "shooter") {
        arrayToLoopThrough = shooterGames;
    }
    else if (buttonId === "rpg") {
        arrayToLoopThrough = rpgGames;
    }

    const container = document.querySelector(".container.results");
    let newHTML = "";

    for (let i = 0; i < arrayToLoopThrough.length; i++) {

        let ratingValue = "Not rated";

        if (arrayToLoopThrough[i].rating) {
            ratingValue = arrayToLoopThrough[i].rating;
        }

        const genres = arrayToLoopThrough[i].genres;
        const genresHTML = makeGenres(genres);

        const platforms = arrayToLoopThrough[i].platforms;
        const platformsHTML = makePlatforms(platforms);

        const details = `<div class="card">
                            <div class="image" style="background-image: url(${arrayToLoopThrough[i].background_image});"></div>
                            <div class="details">
                                <h4 class="name">${arrayToLoopThrough[i].name}</h4>
                                <div class="rating">${ratingValue}</div>
                                ${genresHTML}
                                <div class="platforms">${platformsHTML}</div>
                            </div>
                        </div>`;

        newHTML += details;
    }

    container.innerHTML = newHTML;
}

function makeGenres(genreArray) {

    let genreHTML = "";

    for (let i = 0; i < genreArray.length; i++) {
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    return genreHTML;
}

function makePlatforms(platformsArray) {

    let platformsHTML = "";

    for (let i = 0; i < platformsArray.length; i++) {
        platformsHTML += `<span>${platformsArray[i].platform.name}</span>`;
    }

    return platformsHTML;
}
```

## Code improvement practice

Switch statements were covered in Programming Foundations Module 1, Lesson 3.

Convert the `if-else-if` statement to a `switch` statement. Remember to include a `default` code block. 

Try it on your own, and we'll convert it in the next lesson.

## Acivities

#### Watch

[LinkedIn Learning: JavaScript Essential Training](https://www.linkedin.com/learning/javascript-essential-training-3/what-are-dom-events)

Watch the following videos:

Section 7. JavaScript and the DOM, Part 2: Events:

- What are DOM events?
- Some typical DOM events
- Trigger functions with event handlers
- Add and use event listeners
- Pass arguments via event listeners

---
- [Go to lesson 3](3) 
---

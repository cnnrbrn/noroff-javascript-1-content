## Data attributes

Data attributes are used to store data and information on HTML elements.

They are created by adding a name for the data you want to store to the `data-` prefix.

If we wanted to add a data attribute to the buttons to store their genre information, we would use a data attribute called `data-genre`.

The value of the attribute is assigned using an equals sign like any other attribute:

```js
data - genre = "action";
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

-   `event` - the click event
-   `target` - the element the event happened on
-   `dataset` - the data attributes on the element
-   `genre` - the value of the `data-genre` attribute

Now we need to change the variable the switch statement is checking from `buttonId` to `genre`:

```js
switch(genre) {
```

The full switch code:

```js
// get genre value from the data-genre attribute
const genre = event.target.dataset.genre;

let arrayToLoopThrough;

switch (genre) {
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

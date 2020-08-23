### createElement

So far we've created new HTML elements using a string and assigning it to an element's `innerHTML` property.

There is another way to create elements using the `createElement` method.

First let's create a new `h1` tag:

```js
const heading = document.createElement("h1");
console.log(heading);
// <h1></h1>
```

Let's add class to it using the `className` property rather than the `classList` object:

```js
heading.className = "details-title";
```

The `createTextNode` method allows us to create a new `text node`. The argument to the method will be text value that is created.

```js
const headingContent = document.createTextNode("Heading");
```

We can add this text node as child node the `h1` tag using the `appendChild` method:

```js
heading.appendChild(headingContent);
console.log(heading);
// <h1>Heading</h1>
```

To add this `h1` to the DOM and display it on the page, we can use the `appendChild` method again.

We'll appened it to the `container` from above:

```js
container.appendChild(heading);
```

Now the `h1` is visible on the page, but we want to display the game's name in the heading, not a static string. We can use the `details.name` property for this:

```js
const headingContent = document.createTextNode(details.name);
```

Now the game's name is displayed in the `h1`.

Using `createTextNode` and then appending it to the element is quite a verbose way to go about it.

Now that you know that way exists, let's go back to using `innerText`/`innerHTML`:

```js
heading.innerText = details.name;
```

Full function code so far:

```js
function createDetails(details) {
    const container = document.querySelector(".container");
    const loader = document.querySelector(".loader");
    container.removeChild(loader);

    const heading = document.createElement("h1");
    heading.innerText = details.name;

    container.appendChild(heading);
}
```

Let's add a div that will display the game's image as a background image.

First we create the div:

```js
const backgroundImage = document.createElement("div");
```

Then add a class to it:

```js
backgroundImage.className = "details-image";
```

Then set its background-image property as `details.background_image`:

```js
backgroundImage.style.backgroundImage = `url("${details.background_image}")`;
```

And finally append it to the container. The appendChild method adds the element after the existing elements:

```js
container.appendChild(backgroundImage);
```

We'll follow a similar process for the game's description:

```js
const description = document.createElement("div");
description.className = "details-description";
// we'll innerHTML as description contains HTML
description.innerHTML = details.description;

container.appendChild(description);
```

Let's add the release date using a `time` tag

```js
const releaseDate = document.createElement("time");
releaseDate.className = "details-date";
releaseDate.innerText = `Released: ${details.released}`;

container.appendChild(releaseDate);
```

That will place the `releaseDate` element at the bottom of the other elements.

If we wanted to place it before another element, we can use the `before` method. Let's place it before the description:

```js
description.before(releaseDate);
```

> The `after` method will insert an element after another element.

The complete `createDetails` function:

```js
function createDetails(details) {
    const container = document.querySelector(".container");

    // select the loader and then remove it from the DOM
    const loader = document.querySelector(".loader");
    container.removeChild(loader);

    // create the heading
    const heading = document.createElement("h1");
    heading.innerText = details.name;

    container.appendChild(heading);

    // add the div with a background image
    const backgroundImage = document.createElement("div");
    backgroundImage.className = "details-image";
    backgroundImage.style.backgroundImage = `url("${details.background_image}")`;

    container.appendChild(backgroundImage);

    // add the description
    const description = document.createElement("div");
    description.className = "details-description";
    description.innerHTML = details.description;

    container.appendChild(description);

    // add the release date
    const releaseDate = document.createElement("time");
    releaseDate.className = "details-date";
    releaseDate.innerText = `Released: ${details.released}`;

    description.before(releaseDate);
}
```
---
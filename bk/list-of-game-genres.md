Let's use the return value from a function to build a list of genres for each game.

If you look at the objects inside `js/data/actionGames.js`, you will see each object has a property called `genres` with an array of objects as its value:

```js
genres: [
    {
        name: "Shooter",
        slug: "shooter"
    },
    {
        name: "Action",
        slug: "action"
    }
];
```

We're going to take the `genres` property for each game, and pass it to a function that will loop through each object in the array and create an HTML string. This string will be returned from the function and used to display all the genres inside each game card.

In `js/script.js`, let's first assign the `genres` in each game object to a variable and log it:

```js
// assign the genres in each game object to a variable
const genres = actionGames[i].genres;

// log the genres array
console.dir(genres);
// Array(2)
// Array(2)
// Array(2)
// Array(3)
```

The full code:

```js
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    let ratingValue = "Not rated";

    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    // assign the genres in each game object to a variable
    const genres = actionGames[i].genres;
    // log the genres array
    console.dir(genres);

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                        </div>
                    </div>`;
    newHTML += details;
}

container.innerHTML = newHTML;
```

Each array gets logged in the console:

```js
Array(2);
Array(2);
Array(2);
Array(3);
```

You can click each array in the console to view the objects inside. This what is inside the first array:

```js
0: {name: "Shooter", slug: "shooter"}
1: {name: "Action", slug: "action"}
```

We could write a loop inside the existing for loop to create the HTML for the genres, but loops within loops become difficult to read.

Instead, we'll create a function that we will pass the `genres` to. So the function will have one argument, `genreArray`:

```js
function makeGenres(genreArray) {}
```

Inside the function, we will loop through the array of objects - `genres` - that gets passed in as the `genreArray` argument:

```js
function makeGenres(genreArray) {
    // loop through the genreArray array
    for (let i = 0; i < genreArray.length; i++) {
        // log each object in the array
        console.log(genreArray[i]);
    }
}
```

Back inside our first loop, we can pass in the `genres` property to this function:

```js
const genres = actionGames[i].genres;
makeGenres(genres);
```

The full code so far:

```js
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    let ratingValue = "Not rated";

    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    // assign the genres in each game object to a variable
    const genres = actionGames[i].genres;
    // call the makeGenres function and pass in the genres array
    makeGenres(genres);

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                        </div>
                    </div>`;
    newHTML += details;
}

container.innerHTML = newHTML;

function makeGenres(genreArray) {
    // loop through the genreArray array
    for (let i = 0; i < genreArray.length; i++) {
        // log each object in the array
        console.log(genreArray[i]);
    }
}
```

Inside the `makeGenres` function, the loop will log each object in the array that gets passed in:

```js
{name: "Shooter", slug: "shooter"}
{name: "Action", slug: "action"}
{name: "Action", slug: "action"}
{name: "RPG", slug: "role-playing-games-rpg"}
{name: "Shooter", slug: "shooter"}
{name: "Action", slug: "action"}
{name: "Shooter", slug: "shooter"}
{name: "Action", slug: "action"}
{name: "RPG", slug: "role-playing-games-rpg"}
```

Like we did in the first loop, we want to create an HTML string in the loop inside the function.

First let's declare a variable that will hold the HTML:

```js
let genreHTML = "";
```

Then inside the loop, we'll add the new HTML to the existing HTML stored in `genreHTML`:

```js
genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
```

The function code so far:

```js
function makeGenres(genreArray) {
    let genreHTML = "";

    for (let i = 0; i < genreArray.length; i++) {
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    console.log(genreHTML);
}
```

The console log after the loop will display the created HTML in the console:

```html
<a class="genre">Shooter</a><a class="genre">Action</a> <a class="genre">Action</a><a class="genre">RPG</a> <a class="genre">Shooter</a><a class="genre">Action</a> <a class="genre">Shooter</a
><a class="genre">Action</a><a class="genre">RPG</a>
```

There are four lines of HTML, as the function gets called four times in the loop.

We want to return the HTML from the function each time it's called so that we can display it inside our game card:

```js
return genreHTML;
```

Full function code:

```js
function makeGenres(genreArray) {
    let genreHTML = "";

    for (let i = 0; i < genreArray.length; i++) {
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    return genreHTML;
}
```

Back inside the original for loop, we want to assign the return value of the function to a variable when we call the function:

```js
const genresHTML = makeGenres(genres);
```

The function will return the HTML it creates and it will be assigned to the variable `genresHTML`.

We can then embed that variable (beneath the rating) inside the string we use to create the other HTML:

```js
const details = `<div class="card">
                    <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                    <div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${ratingValue}</div>
                        ${genresHTML}
                    </div>
                </div>`;
```

The full code:

```js
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    let ratingValue = "Not rated";

    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    // assign the genres in each game object to a variable
    const genres = actionGames[i].genres;
    // assign the return value of the function (the HTML the function creates) to a variable
    const genresHTML = makeGenres(genres);

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                            ${genresHTML}
                        </div>
                    </div>`;
    newHTML += details;
}

container.innerHTML = newHTML;

function makeGenres(genreArray) {
    // variable that will hold the HTML string we create in the loop
    let genreHTML = "";

    // loop through each object in the genreArray
    for (let i = 0; i < genreArray.length; i++) {
        // add the new HTML to the existing HTML stored in genreHTML
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    // return the HTML that was created
    return genreHTML;
}
```

Your `index.html` should look similar to this:

<img src="/images/js1/site-2.png" alt="Site example 2" style="max-width:800px">

---

### Creating the platforms HTML

We're going to repeat the above process, this time for the `platForms` array in `js/data/actionGames.js`.

This is what the `platforms` property looks like for the first object:

```js
platforms: [
    {
        platform: {
            name: "PC"
        }
    },
    {
        platform: {
            name: "Xbox One"
        }
    }
];
```

Each object has one property called `platform`. This property has an object as a value:

```js
{
    name: "PC";
}
```

Let's create the `makePlatforms` function:

```js
function makePlatforms(platformsArray) {
    for (let i = 0; i < platformsArray.length; i++) {
        console.dir(platformsArray[i]);
    }
}
```

In the original loop, let's get the `platforms` property and pass it to the `makePlatforms` function:

```js
const platforms = actionGames[i].platforms;
makePlatforms(platforms);
```

The `makePlatforms` now logs each object in the `platformsArray` argument:

```js
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
{platform: {…}}
```

If you click on one of the objects in the console, you will see the `platform` property's value is an object:

```js
platform: {
    name: "PC";
}
```

So we'll need to use dot notation twice to get to the `name` property we need:

```js
console.log(platformsArray[i].platform.name);
```

Full function code so far:

```js
function makePlatforms(platformsArray) {
    // loop through the platformsArray array
    for (let i = 0; i < platformsArray.length; i++) {
        // use dot notation twice to get to the name property
        console.log(platformsArray[i].platform.name);
    }
}
```

The function above will log each `name` value in the for loop.

Like in the `makeGenres` function, let's create an HTML string in the loop and then return it:

```js
function makePlatforms(platformsArray) {
    // variable that will hold the HTML string we create in the loop
    let platformsHTML = "";

    for (let i = 0; i < platformsArray.length; i++) {
        // add the new HTML to the existing HTML stored in platformsHTML
        platformsHTML += `<span class="platform">${platformsArray[i].platform.name}</span>`;
    }

    // return the HTML that was created
    return platformsHTML;
}
```

Back in the original loop, we'll assign the return value of the `makePlatforms` function to a variable:

```js
// assign the platforms property in each game object to a variable
const platforms = actionGames[i].platforms;

// assign the return value of the makePlatforms function to a variable
const platformsHTML = makePlatforms(platforms);
```

Then we'll embed the `platformsHTML` variable - wrapped in a div - below the `genresHTML` variable:

```js
const details = `<div class="card">
                    <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                    <div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${ratingValue}</div>
                        ${genresHTML}
                        <div class="platforms">${platformsHTML}</div>
                    </div>
                </div>`;
```

Full code:

```js
// we declare both these variables outside the for loop
const container = document.querySelector(".container");
// newHTML's value will change so we use let to declare it
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    // create a default value for the rating
    let ratingValue = "Not rated";

    // if the object contains a rating property
    // set the ratingValue equal to the rating property
    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    // assign the genres property in each game object to a variable
    const genres = actionGames[i].genres;

    // assign the return value of the makeGenres function (the HTML the function creates) to a variable
    const genresHTML = makeGenres(genres);

    // assign the platforms property in each game object to a variable
    const platforms = actionGames[i].platforms;

    // assign the return value of the makePlatforms function to a variable
    const platformsHTML = makePlatforms(platforms);

    // each time the loop is executed, assign the details variable a template literal
    // this is a string with embedded variables
    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                            ${genresHTML}
                            <div class="platforms">${platformsHTML}</div>
                        </div>
                    </div>`;
    // add the value of details to the existing value of newHTML
    newHTML += details;
}

// set container's innerHTML property to be the HTML that was created in the loop
container.innerHTML = newHTML;

function makeGenres(genreArray) {
    // variable that will hold the HTML string we create in the loop
    let genreHTML = "";

    for (let i = 0; i < genreArray.length; i++) {
        // add the new HTML to the existing HTML stored in genreHTML
        genreHTML += `<a class="genre">${genreArray[i].name}</a>`;
    }

    // return the HTML that was created
    return genreHTML;
}

function makePlatforms(platformsArray) {
    // variable that will hold the HTML string we create in the loop
    let platformsHTML = "";

    for (let i = 0; i < platformsArray.length; i++) {
        // add the new HTML to the existing HTML stored in platformsHTML
        platformsHTML += `<span>${platformsArray[i].platform.name}</span>`;
    }

    // return the HTML that was created
    return platformsHTML;
}
```

Without comments:

```js
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    let ratingValue = "Not rated";

    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    const genres = actionGames[i].genres;
    const genresHTML = makeGenres(genres);

    const platforms = actionGames[i].platforms;
    const platformsHTML = makePlatforms(platforms);

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                            ${genresHTML}
                            <div class="platforms">${platformsHTML}</div>
                        </div>
                    </div>`;

    newHTML += details;
}

container.innerHTML = newHTML;

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

---

Your `index.html` should look similar to this:

<img src="/images/js1/site-3.png" alt="Site example 3" style="max-width:800px">

---

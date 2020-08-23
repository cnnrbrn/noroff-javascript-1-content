- Fetching a specific item from an API

Check out [step-16](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-16) branch from the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) to follow this lesson.

---

The following changes have been made to the projects files in this branch:

- The `makeGenres` and `makePlatforms` functions have been moved from `js/script.js` to a new file called `js/tags.js`.
- `js/details.js` has been added
- `details.html` has been added and loads `js/details.js` and `js/tags.js`

```html
<script src="js/details.js"></script>
<script src="js/tags.js"></script>
```

---

## Fetching details of a particular game

In `js/script.js` a `Details` link styled like a button has been added to each card:

```js
<a class="btn details">Details</a>
```

At the moment the link doesn't do anything. We want to use it to link to a details page with the game's `id` in the query string.

On the details page, we'll retrieve the id and use it in a call to the API to fetch the game's details.

First, let's add the `href` attribute including the id to the link:

```js
<a class="btn details" href="details.html?id=${games[i].id}">Details</a>
```

Now the links will take us to the details page with the game id in the query string.

```js
http://127.0.0.1:5502/details.html?id=5679
```

On `details.html`, there is a `Back to games` link and the loader.

We'll code the following in `js/details.js`.

First we'll get the query string and the params from it:

```js
const queryString = document.location.search;
const params = new URLSearchParams(queryString);
```

We'll declare a variable to hold the `id` if it exists

```js
let id;
```

We want to check if the `id` param exist and if it does, assign it to the `id` variable:

```js
if (params.has("id")) {
    id = params.get("id");
}
```

If the `id` param doesn't exist, there is no point running the rest of the code in the file, let's go back to the home page. We can redirect to the home page using 

```js
document.location.href = "/";
```

Full code so far:

```js
const queryString = document.location.search;
const params = new URLSearchParams(queryString);

let id;

if (params.has("id")) {
    id = params.get("id");
} else {
    document.location.href = "/";
}
```

We're not loading the `js/script.js` file so we'll need to create the `baseUrl` and `gamesUrl` variables here:

```js
const baseUrl = "https://api.rawg.io/api/";
const gamesUrl = `${baseUrl}games/`;
```

The format of the URL to fetch a specific game is 

`
https://api.rawg.io/api/games/id
`

so we'll create `detailsUrl` variable that includes the id:

```js
const baseUrl = "https://api.rawg.io/api/";
const gamesUrl = `${baseUrl}games/`;
const detailsUrl = `${gamesUrl}${id}`;
```

This is the URL we'll use in the `fetch`:

```js
fetch(detailsUrl)
    .then(function(response) {
        return response.json();
    })
    .then(function(json) {
        createDetails(json);
    })
    .catch(function(error) {
        console.dir(error);
    });
```


Next we'll need the `createDetails` function that we're calling from the second `then` method. This time we'll call the argument `details`.

```js
function createDetails(details) {
    console.dir(details);
}
```

If we log the `details` argument we'll see it's an object with a lot of properties about the retrieved game. 

<img src="/images/js1/game-details.png" alt="promise" style="max-width:400px">

We'll use those properties to build the page elements.




### Adding the genre links to the details page

One of the things that makes functions so useful is that we can reuse their functionality. 

Let's reuse the `makeGenres` function on this page to create the genre links.

We've moved both the `makreGenres` and `makePlatforms` functions from `js/script.js` to `js/tags/js` and are loading it in `details.html`.

This means me can use both functions on this page.

First, let's create a div to hold the genres:

```js
const genres = document.createElement("div");
genres.className = "details-genres";
```

Now we want to assign the return value of the `makeGenres` function to the innerHTML of the `genres` element and append it to the container.

```js
genres.innerHTML = makeGenres(details.genres);

container.appendChild(genres);
```

No genres are being displayed and the console is displaying an error:

```
ReferenceError: genres is not defined
```

If we look inside the `makeGenres` function in `js/tags.js`, we have the `if` statement checking if the `genres` variable is equal to the `slug` of the `genre` being looped through:

```js
if (genres === genre.slug) {
    activeClass = "active";
}
```

Because `genres` is declared in `js/api.js` and we aren't loading that file on this page, the `genres` variable doesn't exist in this context and the error is thrown.

We need to check if `genres` exists before using it in the comparison inside the if. We can do this using the `typeof` operator and checking it's not equal to the string value `"undefined"`:

```js
if (typeof genres !== "undefined" && genres === genre.slug) {
    activeClass = "active";
}
```

Now the `genre` links will be displayed after the description and we can use them to search for games in different genres.

### Updating the page title

We can update the page title using `document.title`.

Let's set the title to the game's name, a pipe symbol `|` plus whatever is currently in the title. We'll add this at the bottom of the `createDetails` function.

```js
document.title = details.name + " | " + document.title;
```

---

Branch [step-17](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-17) of the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) contains the code so far.
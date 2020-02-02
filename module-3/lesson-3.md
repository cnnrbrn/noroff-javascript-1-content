# Lesson 3 

--- 

Make sure you are on the [step-12](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-12) branch of the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code).

---

<!-- ## Adding headers to fetch

The RAWG [Terms of Use](https://rawg.io/apidocs) require an active link on every page the API is used and that _every API request should have a User-Agent header with your app name_.

We already have the active link in the footer.

To add the User-Agent header, we can add a header object as a second argument to the `fetch` method.

First let's create a headers object. It is just a variable so we can it anything, but `headers` is an appropriate name: -->

<!-- ```js
const headers = {

}
```

We need the property `User-Agent` in the object whose value should be the app name:

```js
const headers = {
    "User-Agent": "JavaScript 1 Lessons"
}
``` -->

<!-- > Object properties that have characters like hyphens in them need to be enclosed in quotes. -->

Currently our app is fetching the first 20 games of any genre from the API.

We can use the query string to send parameters to the API and retrieve games of a specific genre. These paramters come after the `?` in a URL and have the format `parameter=value`.

If we look at the [docs](https://api.rawg.io/docs/#operation/games_list) we can see there is a `genres` parameter we can use. If we wanted to select `action` games the parameter would be `genres=action`.

If we added that to our `gamesUrl` variable the full URL for the call would be:

`
https://api.rawg.io/api/games?genres=action
`

`Action` is the first item in our genre menu, so let's make that call the default one.

In `js/api.js`, create variabe to hold the genre. We'll call it `genres` and it's possible to fetch more than one genre at a time. This value is updateable, so we'll use `let` to declare it.

```js
let genres = "action";
```

We also want to add an empty genres parameter to the `gamesUrl` variable:

```js
const gamesUrl = `${baseUrl}games?genres=`;
```

We'll create a new variable called `genreUrl` composed of these two variables:

```js
const genreUrl = `${gamesUrl}${genre}`
```

Or using concatenation:

```js
const genreUrl = gamesUrl + genre;
```

This will give us the URL from above `https://api.rawg.io/api/games?genres=action`

`genreUrl` is the variable we now need to use in the fetch method:

```js
fetch(gamesUrl)
```

Full code so far:

```js
const baseUrl = "https://api.rawg.io/api/";
const gamesUrl = `${baseUrl}games?genres=`;
let genres = "action";
const genreUrl = gamesUrl + genres;

fetch(genreUrl)
    .then(function(response) {
        return response.json();
    })
    .then(function(json) {
        loadGames(json);
    })
    .catch(function(error) {
        console.dir(error);
    });
```

Run this code and you'll see games in the `action` genre are returned - the games' genre tags all include `action`.

To view API calls made this way, we can look at the `Network` tab in dev tools:

<img src="/images/js1/network-tab-xhr.png" alt="fetch" style="max-width:499px">

`XHR` stands for `XMLHttpRequest`. Click on the `XHR` filter to only display network calls and hide all other network requests.

Click on the URL in the left pane to view details of the call:

<img src="/images/js1/network-tab-xhr-details.png" alt="fetch" style="max-width:697px">

--- 

When we click on a genre in the menu, we want to fetch games in that genre.

There are several ways to about it. We are going to do the following:

- add a `genres` parameter to the current querystring and reload the page
- when the page loads, retrieve the `genres` parameter and update the `genres` variable

This isn't the most elegant way to achieve the desired result, but allows us to showcase a couple new techniques.



---
- [Go to lesson 4](4) 
---
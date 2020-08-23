
### String manipulation

In branch `step-14`, we've added a `h1 tag to the HTML.

Let's display the current genre inside this element. We'll do this at the bottom of `js/api.js`.

First let's select the element:

```js
const genreHeading = document.querySelector("h1");
```

We can assing the `genres` variable value to the `innerText` property of the element:

```js
genreHeading.innerText = genres;
```

We are using a CSS property to capitalise the genre (`text-transform: capitalize;`) but if we click on the `RPG` genre, what's displayed isn't very user-friendly.

```html
Role-Playing-Games-Rpg
```

#### replace()

JavaScript has several built-in methods we can use to manipulate strings.

The `replace` method takes to arguments:

- the first is what we want to replace
- the second is what we want to replace the first with

Let's replace any hyphens `-` in the genre with blank spaces `" "`:

```js
const formattedGenres = genres.replace("-", " ");

genreHeading.innerText = formattedGenres;
```

```html
Role Playing-Games-Rpg
```

Looks like the `replace` method has only replaced the first instance of what we were looking to replace. 

We'll need to use a regular expression to replace all the instances.

`Regular expressions` are used to match patterns. We place the pattern we are looking in between two forward slashes `/ /`.

In this case we are looking for a very simple pattern, just a hyphen. Our regular expression would look like this:

```js
/-/
```

To find all the matches for the pattern we can use the `g` modifier which will perform a `global` search in the string we are searching:

```js
/-/g
```

We can use that regular expression in the `replace` method to replace all hyphens:

```js
const formattedGenres = genres.replace(/-/g, " ");
```

The full code we've added at the bottom of `js/api.js` so far:

```js
const genreHeading = document.querySelector("h1");

const formattedGenres = genres.replace(/-/g, " ");

genreHeading.innerText = formattedGenres;

```

We also don't want the ` Rpg` part of `Role Playing Games Rpg`.

Let's use another `replace` method to replace it with nothing: `""`. It's the CSS property that's responsible for the capitalisation, so the string we're searching for to replace is ` rpg`. 

We'll chain the two replace methods:

```js
const formattedGenres = genres.replace(/-/g, " ").replace(" rpg", "");
```

The full code we've added at the bottom of `js/api.js`:

```js
const genreHeading = document.querySelector("h1");

const formattedGenres = genres.replace(/-/g, " ").replace(" rpg", "");

genreHeading.innerText = formattedGenres;
```

--- 
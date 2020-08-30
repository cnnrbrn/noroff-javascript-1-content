# Lesson 4 - String manipulation and form validation

In this lesson we are going to look at:

- 
- 

## Regular Expressions

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

[Go to the module assignment](ma)

---

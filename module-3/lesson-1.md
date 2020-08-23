# Lesson 1

In this lesson we will take a look at:

-   truthy and falsy values
-   querystrings
-   GET requests

## Truthy and falsy values

Each value in JavaScript has a `boolean` value associated with it, known as `truthy` or `falsy`.

The following values are `falsy`:

-   false
-   0 - the number zero
-   "", '' or `` - empty strings
-   null
-   undefined
-   Nan - `N`ot `a` `N`umber

Every other value is `truthy`.

If we are trying to check if a value exists, if it isn't `null` or `undefined`, for example, we can do this:

```js
if (someVariable) {
    console.log("someVariable exists");
}
```

rather than having to check for both `null` and `undefined` like this:

```js
if (someValue !== null && someValue !== undefined) {
    console.log("someValue exists");
}
```

That applies to all the falsy values, so we can check that a variable's value is not one of the `falsy` values by writing an `if statement` like the one above and below:

```js
if (someVariable) {
    // someVariable has a truthy value
}
```

<iframe src="https://scrimba.com/c/c7qJwDS4" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/c7qJwDS4" target="_blank">Scrimba link</a>

---

## Querystrings

The querystring is the part of the URL after the `?`. It can be used to pass values around.

In the URL

```
https://youtube.com/watch?v=abcd1234
```

`?v=abcd1234` is the querystring. It has one parameter called `v` with a value of `abcd1234`.

<iframe src="https://player.vimeo.com/video/449681615" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

---

## Introduction to GET requests

One of the main things you will need to do as a frontend developer is to connect to APIs.

In this introduction to GET requests we are going make a first call to fetch data from an API.

This data will be in JSON format, and we can loop over it to create HTML like we have before with arrays of objects.

 <iframe src="https://player.vimeo.com/video/449846877" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

---

The following video takes another look at the same code.

<iframe src="https://player.vimeo.com/video/450070174" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/get-requests-introduction" target="_blank">Code from both videos</a>


---

[Go to lesson 2](2)

---

# Lesson 4 - String manipulation and form validation

In this lesson we are going to look at:

-   regular expressions
-   preventing the default behaviour of forms
-   simple form validation

## Regular Expressions

`Regular expressions` are used to match patterns. We place the pattern we are looking in between two forward slashes `/ /`.

We can use the `test()` method to see if there is a match between a regular expression and a string. The return value is a boolean value.

The below will test if there is match between the regular expression `/hello/` and the string `"Oh hello there"`. In other words, does the string contain the chracters `hello`.

```js
const stringToTest = "Oh hello there";

// the expression is placed between / /
const expression = /hello/;

const result = expression.test(stringToTest);

console.log(result);
// true
```

A common use for regular expressions is to test if form input values match a certain pattern, e.g. does a value look like an email address.

The function below could be used to test if the argument passed in looks like an email address:

```js
function validateEmail(email) {
    const regEx = /\S+@\S+\.\S+/;
    const patternMatches = regEx.test(email);
    return patternMatches;
}
```

This function will return true if the argument looks like an email adress, and false if it doesn't.

You will not often have to create your own regular expressions. You can see in the `regex` example above that they can be difficult to read. Most of the time you can find regular expressions on the internet that you can use to test for patterns, e.g. is a phone number in a certain format or is a password complicated enough.

Here is a [list of common regular expressions](https://digitalfortress.tech/tricks/top-15-commonly-used-regex/).

---

## Preventing the default behaviour of forms

To prevent the default behaviour of submitted forms, which includes reloading the page, when can use:

```js
event.preventDefault();
```

<iframe src="https://player.vimeo.com/video/453361604" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/453361604/765aa36966" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/submit-event-preventDefault" target="_blank">Code from the video</a>

---

## Simple form validation

We're going to use the `trim()` method and `length` property we have looked at [before](https://scrimba.com/c/cQRRVdTq) to help us add simple validation to a form.

<iframe src="https://player.vimeo.com/video/453789618" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/453789618/501a1e3296" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/simple-form-validation" target="_blank">Code from the video</a>

---

[Go to the module assignment](ma)

---

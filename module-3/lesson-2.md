# Lesson 2

In this lesson we will take a look at:

-   default parameters values in functions
-   creating dynamic HTML inside a function based on arguments
-   handling errors with a `try-catch-finally` statement

## Default parameter values

To provide default values for parameters we assigning in the function parameter list, e.g.

```js
function printMessage(message = "No message provided") {
    // do something
}
```

If we call `printMessage()` and don't pass in an argument to the `message` parameter, message will have the default value of `"No message provided"`.

<iframe src="https://scrimba.com/c/cB3qn6u7" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cB3qn6u7" target="_blank">Scrimba link</a>

---

## Creating a reusable function that returns dynamic HTML

In this video we look at passing arguments to a function that will return different HTML based on what we pass in.

We might call this function a `component`. It will return a limited amount of HTML that we can use elsewhere in our code.

<iframe src="https://player.vimeo.com/video/450469640" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/reusable-html-function" target="_blank">Code from the video</a>

---

## Handling errors with a `try-catch-finally` statement

In the following video we look at how to use the `try-catch-finally` statement to catch errors and provide feedback to the user, rather than simply logging an error to the console that the user will never see.

<iframe src="https://player.vimeo.com/video/450419821" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/try-catch-finally" target="_blank">Code from the video</a>

---

## Adding error handling to an API call

In this video we will add error handling to our API call with a `try-catch` statement.

<iframe src="https://player.vimeo.com/video/450417105" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/get-requests-handling-errors" target="_blank">Code from the video</a>

---

[Go to lesson 3](3)

---

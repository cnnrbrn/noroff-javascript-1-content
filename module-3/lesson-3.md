# Lesson 3

In this lesson we will take a look at:

- arrow functions
- making API calls with the `then` and `catch` methods - regular promise syntax

## Arrow functions

Arrow functions don't use the `function` keyword and use the `=>` characters instead, hence their name.

We can rewrite the following function:

```js
function logMessage(message) {
    console.log(message);
}
```

like this:

```js
const logMessage = (message) =>  console.log(message);
```

<iframe src="https://scrimba.com/c/cg29pns6" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cg29pns6" target="_blank">Scrimba link</a>


## Asynchronous code

In the GET request API call we used the `async` and `await` keywords to make the call.

That was an example of <b>asynchronous code</b>.

Previously the code we wrote had been executed or returned a value as soon as it was encountered in the program, apart from in the `setTimeout` method where we deliberately delay the execution.

Async/await is a recent(ish) addition to JavaScript that allows us to work with promises in a more readable fashion, but we need to also look at using promises in the regular way as you will encounter this syntax in other people's code.

---

If you log a message

```js
console.log("I am the first log");
```

the message is displayed as soon as the code is run.

If you declare a function

```js
function logMessage() {
    console.log("Function called");
}
```

the function is run as soon as it's called:

```js
logMessage();
// Function called
```

The following will be executed after the function has been called.

```js
console.log("I am the second log");
```

Running all the statements above will log:

```js
// I am the first log
// Function called
// I am the second log
```

The code is called statement by statement and each statement waits for the previous one to finish before running. This is called `synchronous` code.

<img src="/images/js1/synchronous-code.png" alt="synchronous code" style="max-width:500px">

That seems quite obvious, but sometimes it's not a good idea to wait for the previous statement to finish before executing the next one.

If we made a call to a server and the user's internet connection was slow or the server was busy, waiting for the call to return before running the next code would create a poor user experience as the interface would appear unresponsive.

`Asynchronous` code doesn't wait for the current statement to finish running before executing the next statement.

## Promises

`Promises` are a way to execute code `asynchronously`. When we call a promise our code doesn’t wait for a response, but moves on to the next line of code.

<img src="/images/js1/promise-1.png" alt="promise" style="max-width:500px">

<!-- They are objects we can use to handle the successful completion or failure of code that will finish running some time in the future. -->

Once executed, the promise is `pending`. At some point it will return and will either have been `fulfilled` or `rejected`.

<img src="/images/js1/promise-2.png" alt="promise" style="max-width:550px">

<!-- 
When we execute asynchronous code we can use a `Promise` to run a function when the code is successful and returns a value, or when the code is not successful and returns an error. -->

Form [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise):

> A Promise is in one of these states::
>
> - `pending`: initial state, neither fulfilled nor rejected.
> - `fulfilled`: meaning that the operation completed successfully.
> - `rejected`: meaning that the operation failed.

### Promise chaining

Sometimes what is executed in our fulfilled function also returns a promise. This is called promise chaining.

<img src="/images/js1/promise-chaining.png" alt="promise chaining" style="max-width:550px">

`Fulfilled` states are handled by a `Promise`'s `then` method and `rejected` states are handled by a `catch` method.

Both these methods take a function as an argument. This is where we can write code to handle the return value of the promise. 

These functions in turn recieve an argument which is the return value of the promise (if successful and the promise has resolved) or the error from a rejected promise.

<img src="/images/js1/promise-3.png" alt="promise" style="max-width:550px">

--- 

Most of the time you won't write your own promises but will rather use libraries and other existing code built on promises.


## then/catch example

In this video we will rewrite the `async/await` API call to use regular promise syntax.


<iframe src="https://player.vimeo.com/video/450776515" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/get-request-with-regular-promise-syntax" target="_blank">Code from the video</a>

---
- [Go to lesson 4](4) 
---
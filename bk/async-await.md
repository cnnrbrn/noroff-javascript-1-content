## Async/await

Async/await is a recent(ish) addition to JavaScript that allows us to work with promises in a more readable fashion.

Let's look at how we can rewrite a fetch call using `async/await`.

Given this call to fetch a list of games:

```js
const url = "https://api.rawg.io/api/games";

fetch(url)
    .then(function (response) {
        return response.json();
    })
    .then(function (json) {
        console.log(json);
    })
    .catch(function (error) {
        console.log(error);
    });
```

Or using arrow syntax:

```js
const url = "https://api.rawg.io/api/games";

fetch(url)
    .then(response) => response.json())
    .then(json => console.log(json))
    .catch(error => console.log(error));
```

We can rewrite that using async/await like this:

```js
// the function must be marked as async
async function callApi() {
    const url = "https://api.rawg.io/api/games";
    // use the await keyword before the fetch call
    const response = await fetch(api);
    // use the await keyword before the json() call
    const json = await response.json();
    console.log(json);
}

// call the function
callApi();
```

To use the `await` keyword the function it is used in must be marked as `async`.

Previously we caught errors using the `catch` method. That doesn't exist when using async/await but we can wrap the code in a `try/catch` block.

```js
async function callApi() {
    try {
        const url = "https://api.rawg.io/api/games";
        const response = await fetch(api);
        const json = await response.json();
        console.log(json);
    } catch (error) {
        console.log(error);
    }
}

callApi();
```

We `try` to run the code in the first block, and `catch` any errors in the second block.

Lessons 1 and 2 in this module will use the async/await syntax to make API calls.
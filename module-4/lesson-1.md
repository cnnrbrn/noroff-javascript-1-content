# Lesson 1

<!-- This lesson contains a quick note on CORS and then introduces basic form validation.

The rest of the lessons in this module won't introduce any new concepts.

- [Lesson 2](2) will cover displaying an array of results from an API call
- [Lesson 3](3) will cover displaying a specific result returned from an API call
- Lesson 4 will contain practice questions with answers provided in a repo -->

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

## Finding free APIs to use

The are many free APIs available to write frontend code against and a Google search for "free APIs" will return several lists of APIs you can use.

One such list can be found at <a href="https://rapidapi.com/collection/list-of-free-apis" target="_blank">https://rapidapi.com/collection/list-of-free-apis</a>.

Log in with your Github account or create a new account. You can skip/close the screen that asks you for your name and organisation.

Many of the APIs, although free, still require keys to use. Logging in to the service will give you access to automatically created keys.

<img src="/images/js1/rapid-api.png" alt="Rapid API" style="max-width:900px">

We are going to scroll down and select `Urban Dictionary` from this free list, but you can browse by category or collection. Some require subscription but offer free limited subscriptions.

On the Urban Dictionary page you can test the API endpoint. An API key has been created to use in the call.

<img src="/images/js1/rapid-api-urban-dictionary.png" alt="Rapid API - Urban Dictionary" style="max-width:900px">

From the dropdown menu select `JavaScript` -> `fetch`:

<img src="/images/js1/rapid-api-dropdown.png" alt="Rapid API code select" style="max-width:700px">

Click the Test Endpoint button to test the API. The results will be returned in the right panel in the Response Body section.

<img src="/images/js1/rapid-api-response.png" alt="Rapid API response body" style="max-width:700px">

The Code Snippet tab in the right panel has example code for the call that uses `fetch`.

<img src="/images/js1/rapid-api-example-fetch.png" alt="Rapid API example fetch" style="max-width:700px">

You can copy that code and use it in your script file or test it in the browser console. Note that the example code doesn't include the second `then` method which you will need to add.

We can take that code and rewrite it using `async/await`.

The extra object added to the fetch call contains the header property with the required API key values.

```js
async function callUrbanDictionary() {
    const response = await fetch("https://mashape-community-urban-dictionary.p.rapidapi.com/define?term=wat", {
        headers: {
            "x-rapidapi-host": "mashape-community-urban-dictionary.p.rapidapi.com",
            "x-rapidapi-key": "your-key-here"
        }
    });

    const json = await response.json();
    console.log(json);
}

callUrbanDictionary();
```

## API call headers

The second argument to a fetch call is an object we can use to set options, like header properties. We are setting two header properties, `x-rapidapi-host` and `x-rapidapi-key`.

Header properties sent by API calls executed in the browser can be viewed in the Network tab in dev tools. Filter by XHR, click on a call URL and look in the Request Headers section:

<img src="/images/js1/request-headers.png" alt="Request headers" style="max-width:900px">

We can move the options object to a variable to make the code more readable:

```js
const options = {
    headers: {
        "x-rapidapi-host": "mashape-community-urban-dictionary.p.rapidapi.com",
        "x-rapidapi-key": "your-key-here"
    }
};

async function callUrbanDictionary() {
    const response = await fetch("https://mashape-community-urban-dictionary.p.rapidapi.com/define?term=wat", options);
    const json = await response.json();
    console.log(json);
}

callUrbanDictionary();
```

The header properties you set, for APIs that require them, will vary between APIs. The RAWG API that you have used in previous modules requires no header properties.

## CORS

CORS stands for `C`ross-`O`rigin `R`esource `S`haring.

For security reasons, browsers don't allow calls to be made to URLs pointing to a different server (a different origin) than the one the website is on, which means that if the website lives on http://www.example-1.com, the browsers won't allow the code to make a call to
http://www.example-2.com.

A lot of websites make calls to different APIs living on different servers, so we need a way around this.

There are two ways to solve this issue:

1. the API can be configured to tell the browser it should allow `cross-origin` requests
2. we can send the API calls through a proxy service

Because we don't have control over how the API is configured unless we develop the API, option 2 is our only solution.

The API found at [https://noroffcors.herokuapp.com/](https://noroffcors.herokuapp.com/) is service we you use to enable cross-origin.

To use it we simply have to prepend that URL to the URL of the API we want to use.

The following API endpoint returns a list of elephants:

```js
https://elephant-api.herokuapp.com/elephants
```

If you called that URL with `fetch` like this

```js
const elephantUrl = "https://elephant-api.herokuapp.com/elephants";

fetch(elephantUrl)
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

an error similar to this would be returned:

```
Access to fetch at 'https://elephant-api.herokuapp.com/elephants' from origin 'http://127.0.0.1:5502' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

To get around this, we can add the `cors-anywhere` URL to the beginning of the URL:

```js
const elephantUrl = "https://elephant-api.herokuapp.com/elephants";
const corsEnabledUrl = "https://noroffcors.herokuapp.com/" + elephantUrl;

fetch(corsEnabledUrl)
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

Now the API call will work.

The RAWG API does not require this workaround as it has been configured to accept cross-origin requests.

---

### Free API lists

-   <a href="https://apilist.fun/" target="_blank">https://apilist.fun/</a>
-   <a href="https://rapidapi.com/collection/list-of-free-apis" target="_blank">https://rapidapi.com/collection/list-of-free-apis</a>.

---

[Go to lesson 2](2)

---

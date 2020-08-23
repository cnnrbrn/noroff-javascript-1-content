# Lesson 4 

In this lesson we will take a look at:

- fixing CORS errors
- how to find free APIs to use
- adding header values to API calls

## CORS

CORS stands for `C`ross-`O`rigin `R`esource `S`haring.

APIs that are not configured to accept requests from different origins, or domains, to their own will block the requests.

A lot of websites make calls to different APIs living on different servers, so we need a way around this.

There are two ways to solve this issue:

1. the API can be configured to allow cross-origin requests
2. we can send the API calls through a proxy service

Because we don't have control over how the API is configured unless we develop the API, option 2 is our only solution.

The API found at [https://noroffcors.herokuapp.com/](https://noroffcors.herokuapp.com/) is a service we can use to enable cross-origin requests.

To use it we simply have to prepend that URL to the URL of the API we want to use.

The following API endpoint returns a list of elephants:

```js
https://elephant-api.herokuapp.com/elephants
```

If you called that URL with `fetch` like this

```js
const elephantUrl = "https://elephant-api.herokuapp.com/elephants";

const response = await fetch(elephantUrl);
const results = await response.json();
```

an error similar to this would be returned:

```
Access to fetch at 'https://elephant-api.herokuapp.com/elephants' from origin 'http://127.0.0.1:5501' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

To get around this, we can add the `cors-anywhere` URL to the beginning of the URL:

```js
const elephantUrl = "https://elephant-api.herokuapp.com/elephants";
const corsEnabledUrl = "https://noroffcors.herokuapp.com/" + elephantUrl;

const response = await fetch(corsEnabledUrl);
const results = await response.json();
```

Now the API call will work.

<iframe src="https://player.vimeo.com/video/450829010" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/get-request-with-cors-fix" target="_blank">Code from the video</a>



---


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

The header properties you set, for APIs that require them, will vary between APIs. 

---

### Free API lists

-   <a href="https://apilist.fun/" target="_blank">https://apilist.fun/</a>
-   <a href="https://rapidapi.com/collection/list-of-free-apis" target="_blank">https://rapidapi.com/collection/list-of-free-apis</a>
-   <a href="https://github.com/public-apis/public-apis" target="_blank">https://github.com/public-apis/public-apis</a>


---

> For the CA you will be required to find your own API to use

---
- [Go to the module assignment](ma) 
---

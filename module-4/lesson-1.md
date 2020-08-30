# Lesson 1

In this lesson we will take a look at:

-   inspecting the results of API calls
-   skipping certain objects when looping over an array of objects

# Inspecting the results of API calls

**_The most important thing to do when making API calls is to inspect the JSON that the call returns_**.

You can't make assumptions about what the JSON will contain and what properties you can access.

You can use similar code to the below (if the API doesn't require a CORS fix or extra headers) to make API calls, but you must always inspect the results first before trying to access any properties.

```js
const url = "path/to/api";

async function callApi() {
    const response = await fetch(url);
    const json = await response.json();

    // inspect what gets returned from the call and see which properties it contains
    console.log(json);
}

callApi();
```

You can use a simple `console.log` or software like [Postman](https://www.postman.com/downloads/).

<iframe src="https://player.vimeo.com/video/452802372" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/452802372/41b688b066" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/inspecting-the-results-of-api-calls" target="_blank">Code from the video</a>

---

# Skipping certain objects when looping over an array of objects

Sometimes you will want to ignore certain objects in array. Perhaps they are missing certain properties or the properties have unuseful values. 

We can do this using the `continue` keyword inside a for loop.

`continue` causes the loop to not execute the code in its current iteration and jumps to the next iteration.

Like `break`, `continue` cannot be used inside a `forEach` function.

- `break` - exit the loop entirely
- `continue` - skip this particular iteration of the loop

<iframe src="https://player.vimeo.com/video/452856488" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/452856488/7bd3c974a7" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/get-requests-skipping-certain-results" target="_blank">Code from the video</a>

---

[Go to lesson 2](2)

---

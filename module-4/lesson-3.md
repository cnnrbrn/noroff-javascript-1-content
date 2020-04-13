# Lesson 3 - Displaying a specific result after an API call

In this lesson we'll fetch and display the result of retrieving a single item from an API.

We'll create the page below.

The example page can be found <a href="https://api-calls.netlify.com/detail.html?name=Balarama" target="_blank">here</a>.

<iframe src="https://api-calls.netlify.com/detail.html?name=Balarama" style="height:400px"></iframe>

You can use the <a href="https://github.com/javascript-repositories/javascript-1-api-calls/tree/step-1" target="_blank">step-1 branch</a> from the repo to add the code in this lesson or continue on the previous branch if you added the code in the last lesson.

---

We will add the code below to the `js/detail.js` file.

In the previous lesson we added the elephant name to a `name` parameter in the querystring in the link to the detail page:

```html
<a href="detail.html?name=${elephants[i].name}">Details</a>
```

This will produce URLs such as

```
https://api-calls.netlify.com/detail.html?name=Balarama
```

We need to get this name from the querystring so we can use it in an API call to fetch a single element by its name.

We need to do the following in the script for this page:

-   get the `name` value from the querystring
-   create the URL we will use to fetch the element
-   make the API call
-   populate the HTML elements on the `detail.html` page with values returned from the API call

The following code will achieve the above:

```js
// get the name parameter from the querystring
// get the query string
const queryString = document.location.search;
// get all the parameters in the query string
const params = new URLSearchParams(queryString);

// get the name parameter from the querystring
const name = params.get("name");

// we can see the various API endpoints in the API docs https://elephant-api.herokuapp.com/

// add the name to the URL
const url = "https://elephant-api.herokuapp.com/elephants/name/" + name;
// add the CORS fix
const corsEnabledUrl = "https://noroffcors.herokuapp.com/" + url;

// we will do everything in one function this time
async function getElephantBYName() {
    // get the heading element
    // we will use this element to display the name if the call is successful
    // if the call is not successful we will display a message in this element
    const heading = document.querySelector("h2");

    // try to make the API call
    try {
        const response = await fetch(corsEnabledUrl);
        const details = await response.json();

        // always inspect the result of the API call
        console.log("details", details);

        // we will use the name, species and not properties from the return value

        // display the name
        heading.innerHTML = details.name;

        // get the species element and display the species value
        const species = document.querySelector(".species");
        species.innerHTML = "Species: " + details.species;

        // get the note element and display the note value
        const note = document.querySelector(".note");
        note.innerHTML = details.note;
    } catch (error) {
        // if there is an error indicate it in the heading element
        heading.innerHTML = "An error occured";
        console.log(error);
    } finally {
        // the finally block runs at the end, whether there was an error or not
        // hide the loading indicator
        const loading = document.querySelector(".loading");
        loading.style.display = "none";
    }
}

// call the function
getElephantBYName();
```

First we get the name from the querystring:

```js
const queryString = document.location.search;
const params = new URLSearchParams(queryString);
const name = params.get("name");
```

We can view the various API endpoints in the API docs <a href="https://elephant-api.herokuapp.com/">https://elephant-api.herokuapp.com/</a>.

We need to use the following URL format to get the elephant by its name:

```js
https://elephant-api.herokuapp.com/elephants/name/{NAME}
```

Then we add the name to URL we need to use to get the elephant by its name:

```js
const url = "https://elephant-api.herokuapp.com/elephants/name/" + name;
const corsEnabledUrl = "https://noroffcors.herokuapp.com/" + url;
```

This time we will do everything in one function. We again use the async/await method of making API calls.

```js
async function getElephantBYName() {
    // everything else goes in here
}
```

We select the `h2` element on the page. This will be used to display the elephant's name or a message if the API call fails.

```js
const heading = document.querySelector("h2");
```

In a `try` block, we make the API call and log the return value:

```js
try {
    const response = await fetch(corsEnabledUrl);
    const details = await response.json();

    console.log("details", details);
```

These are the properties in the return value.

<img src="/images/js1/elephant-by-name-properties.png" alt="Elephant properties" style="max-width:750px">

We will use the `name`, `species` and `note` properties.

We'll display the name property in the h2 tag:

```js
heading.innerHTML = details.name;
```

We select two elements with the `species` and `note` classes by their class and add the `species` and `note` properties as their innerHTML values:

```js
const species = document.querySelector(".species");
species.innerHTML = "Species: " + details.species;

const note = document.querySelector(".note");
note.innerHTML = details.note;
```

Some of the calls will fail, for example if the elephant name has a space in it, the call will not succeed.

We use the `catch` block to execute code if there is an error. We will display a message that there was an error in the `h2` element:

```js
} catch (error) {
    heading.innerHTML = "An error occured";
    console.log(error);
```

The `finally` block runs after all the other code has completed, whether there was an error or not. We want to hide the loading indicator whether the call was successful or not, so this is a good place to hide it.

```js
} catch (error) {
    heading.innerHTML = "An error occured";
    console.log(error);
```

The code added in this lesson can be found in the <a href="https://github.com/javascript-repositories/javascript-1-api-calls/blob/step-2/js/index.js" target="_blank">step-2</a> branch of the repo.

---

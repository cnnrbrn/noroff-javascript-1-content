We'll assign `json.results` to a variable and then loop through it and log each `name` property in the objects.

> Refer to [Programing Foundations Module 2 Lesson 3](https://interactive-content.now.sh/programming-foundations/2/3) for info on looping through arrays of objects using `for loops`

```js
function handleJson(json) {
    const results = json.results;

    for (let i = 0; i < results.length; i++) {
        console.log(results[i].name);
    }
}
```

Let's change the `for loop` to a `forEach` which arguably has a cleaner syntax.

> Refer to [Module 2 Lesson 4](https://interactive-content.now.sh/javascript-1/2/4) for info on forEach

```js
function handleJson(json) {
    const results = json.results;

    results.forEach(function (result) {
        console.log(result.name);
    });
}
```

In `creators.html` there is placeholder HTML for one card. The background image is a placeholder image.

```html
<div class="col-sm-6 col-md-4 col-lg-3">
    <div class="card">
        <div class="image creator" style="background-image: url('https://via.placeholder.com/250');"></div>
        <div class="details">
            <h4 class="name">Name</h4>
            <p>Game count: 0</p>
            <a class="btn details" href="creator-detail.html?id=">Details</a>
        </div>
    </div>
</div>
```

This is the HTML we want to create in a loop for each creator object in the results returned by the API call.

First let's select the element we want to add the HTML to:

```js
const resultsContainer = document.querySelector(".row.results");
```

We'll then declare a variable to hold the HTML we create, and then keeping adding HTML to this variable inside the loop:

```js
let html = "";

results.forEach(function (result) {
    html += `<div class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                        <div class="image creator" style="background-image: url('https://via.placeholder.com/250');"></div>
                        <div class="details">
                            <h4 class="name">Name</h4>
                            <p>Game count: 0</p>
                            <a class="btn details" href="creator-detail.html?id=">Details</a>
                        </div>
                    </div>
                </div>`;
});
```

After the loop finishes we'll assign the newly created HTML string to be the `innerHTML` property of `resultsContainer`:

```js
resultsContainer.innerHTML = html;
```

Full code for the `handleJson` function so far:

```js
function handleJson(json) {
    const results = json.results;
    console.dir(results);

    const resultsContainer = document.querySelector(".row.results");

    let html = "";

    results.forEach(function (result) {
        html += `<div class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                        <div class="image creator" style="background-image: url('https://via.placeholder.com/250');"></div>
                        <div class="details">
                            <h4 class="name">Name</h4>
                            <p>Game count: 0</p>
                            <a class="btn details" href="creator-detail.html?id=">Details</a>
                        </div>
                    </div>
                </div>`;
    });

    resultsContainer.innerHTML = html;
}
```

Because there 10 objects in the `results` array, 10 cards are now displayed on the page.

<img src="/images/js1/api-results-placeholders.png" alt="API results" style="max-width:700px">

Let's populate the HTML with variables from the `results` objects:

-   `result.image` for the background image
-   `result.name` for the name
-   `result.games_count` for the games count
-   `result.id` for the id in the query string of the `Details` link

We'll embed the variables in the string using `${}`.

```js
results.forEach(function (result) {
    html += `<div class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                        <div class="image creator" style="background-image: url('${result.image}');"></div>
                        <div class="details">
                            <h4 class="name">${result.name}</h4>
                            <p>Game count: ${result.games_count}</p>
                            <a class="btn details" href="creator-detail.html?id=${result.id}">Details</a>
                        </div>
                    </div>
                </div>`;
});
```

Now the cards are populated by real data and images and the Details tag links to a `creator-detail.html` page with an `id` in the query string. We'll create this page in [Lesson 3](3).

The function code so far:

```js
function handleJson(json) {
    const results = json.results;
    console.dir(results);

    const resultsContainer = document.querySelector(".row.results");

    let html = "";

    results.forEach(function (result) {
        html += `<div class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                        <div class="image creator" style="background-image: url('${result.image}');"></div>
                        <div class="details">
                            <h4 class="name">${result.name}</h4>
                            <p>Game count: ${result.games_count}</p>
                            <a class="btn details" href="creator-detail.html?id=${result.id}">Details</a>
                        </div>
                    </div>
                </div>`;
    });

    resultsContainer.innerHTML = html;
}
```

### Providing default values for missing properties

To test providing a default value for a missing property, let's fetch the second page of results from the API call. We can do this by adding a `page` parameter to the query string of the URL and setting its value to `2`.

```js
const creatorsUrl = "https://api.rawg.io/api/creators?page=2";
```

If you inspect the JSON returned from this call, you'll see the first object has a missing `image` property, it's set to `null`

```js
image: null;
```

The card therefore has a missing image.

<img src="/images/js1/api-results-missing-property.png" alt="Missing property" style="max-width:700px">

Inside the loop, we'll create a variable with a placeholder value for the image

```js
let imageUrl = "https://via.placeholder.com/250";
```

Then we'll write an `if` statement to check if the `result.image` property is `truthy`. If it is, we'll assign it to the `imageUrl` variable:

```js
if (result.image) {
    imageUrl = result.image;
}
```

Then inside the HTML we are creating, we will use `imageUrl` for the background image property, not `result.image`:

```js
<div class="image creator" style="background-image: url('${imageUrl}');"></div>
```

Now any object that is missing an image property will display the placeholder image instead.

Full code in `js/creators.js`:

```js
const creatorsUrl = "https://api.rawg.io/api/creators?page=2";

fetch(creatorsUrl)
    .then(function (response) {
        return response.json();
    })
    .then(function (json) {
        handleJson(json);
    })
    .catch(function (error) {
        console.log(error);
    });

function handleJson(json) {
    const results = json.results;
    console.dir(results);

    const resultsContainer = document.querySelector(".row.results");

    let html = "";

    results.forEach(function (result) {
        let imageUrl = "https://via.placeholder.com/250";

        if (result.image) {
            imageUrl = result.image;
        }

        html += `<div class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                        <div class="image creator" style="background-image: url('${imageUrl}');"></div>
                        <div class="details">
                            <h4 class="name">${result.name}</h4>
                            <p>Game count: ${result.games_count}</p>
                            <a class="btn details" href="creator-detail.html?id=${result.id}">Details</a>
                        </div>
                    </div>
                </div>`;
    });

    resultsContainer.innerHTML = html;
}
```

In `creators.html` we'll replace the example card HTML with the loader div.

```html
<main class="container content">
    <div class="row results">
        <div class="loader"></div>
    </div>
</main>
```

Branch [step-22](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-22) of the [repo](https://github.com/javascript-repositories/javascript-1-lesson-code) contains the code so far.

---

The fetch call using arrow functions would look like this:

```js
fetch(creatorsUrl)
    .then(response => return response.json())
    .then(json => handleJson(json))
    .catch(error => console.log(error));
```

> Refer to [Module 3 Lesson 1](https://interactive-content.now.sh/javascript-1/3/1) for a discussion of arrow functions.

---

## Code improvement practice

Instead of displaying a placeholder image if the `image` property is missing, check if the `result` object has an `image_background` property and display that instead. If both are missing the placeholder image will be displayed.

You can find the example code for this in [step-23](https://github.com/javascript-repositories/javascript-1-lesson-code/tree/step-23).

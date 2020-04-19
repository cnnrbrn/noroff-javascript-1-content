# JavaScript 1 Course Assignment

Level 1 is required.

Level 2 is optional.

Choosing appropriate variable and function names will form part of your assessment, as will proper and consistent formatting of your code.

---

## Instructions

### Find an API

Search for a public, free-to-use API.

You will need to make two calls to this API:

1. to fetch an array of results
2. to fetch a single result using an id, name or other property.

You will need to read the API's documentation to see what URLs are available, if they require a key to be sent in the header, and any other configuration they might need.

There are many free APIs discoverable by a google search and there is a list in lesson 1 of this module.

### APIs you may not use

You may not use the APIs used in the lessons and you may not use the Rick and Morty API found at https://rickandmortyapi.com/.

---

The HTML and CSS needed for the level 1 requirements is provided in the [repo](https://github.com/javascript-assignments/javascript-1-ca). Download or clone this repo and add your code to it.

Add your JavaScript code to the `.js` files provided.

## Level 1

### `index.html`

Make a call to your API URL, loop through the results and create similar HTML to that below for each result. Your HTML will look different depending on the properties returned from your API. You might not have an image in your results, for example. Add, edit and remove any HTML you require.

> The focus of the CA is on JavaScript, so styling is not important, but feel free to edit and add to the CSS.

You must display <b>at least 3 different properties</b> inside the HTML.

Example HTML:

```html
<div class="col-sm-6 col-md-4 col-lg-3">
    <div class="card">
        <img class="image" src="https://via.placeholder.com/300" alt="Title/Name" />
        <div class="details">
            <h4 class="name">Title/Name</h4>
            <p><b>Property:</b> Property value</p>
            <p><b>Property:</b> Property value</p>
            <a class="btn btn-primary" href="details.html?id=">Details</a>
        </div>
    </div>
</div>
```

You will need to link to the `details.html` page and to pass a parameter in the querystring to that page.

If you are going to fetch the invididual result on the details page by its `id`, then pass an `id` in the querysting:

```html
<a class="btn btn-primary" href="details.html?id=1234">Details</a>
```

If you will be retrieving by another property, like `name` for example, pass the `name` in the querystring.

```html
<a class="btn btn-primary" href="details.html?name=someName">Details</a>
```

You will fetch this parameter from the querystring in the details page code.

Catch any errors and display a message in the heading element on the page if an error occurs.

---

### `details.html`

(Remember you will need a parameter in the querystring on this page, so either click through to it from the index page or manually add an id parameter to the URL).

Retrieve the `id`, `name` or other parameter from the query string.

Once you have the parameter, add it to the API URL in the format the API requires.

> For example, in the RAWG API from the lessons, the `id` of the the game to retrieve was added to the `games` url: `https://api.rawg.io/api/games/1234`

Make an API call using the URL you create.

Populate the HTML on the details page with properties from the results. Again, the properties and HTML you create on this page will depend on the result of the API call.

You must display <b>at least 3 different properties</b> on this page.

Example HTML:

```html
<div class="detail-container">
    <img class="details-image" src="https://via.placeholder.com/250" alt="Title/Name" />
    <div class="detail-details">
        <h1>Title/Name</h1>
        <p>Property: <span class="value" id="propertyName">Property value</span></p>
        <p>Property: <span class="value" id="propertyName">Property value</span></p>
    </div>
</div>
```

Set the title of the page to be one of the property values, like `name`,`title` or another relevant property.

Catch any errors and display a message in the heading element on the page if an error occurs.

---

### `about.html`

Three seconds after this page loads, replace each occurence of the word `the` and `The` with the word `banana` and `Banana` respectively - `the` becomes `banana` and `The` becomes `Banana`.

---

### `contact.html`

When the form on this page is submitted, write code to validate the inputs with the following rules:

-   `Name` - required
-   `Answer` - must have a value with a minimum length of 10
-   `Email` - must have a value and be formatted like an email address
-   `Address` - must have a value with a minimum length of 15

If any of the inputs fail validation display the relevant error message.

---

## Level 2

### `contact.html`

Use a single function for the length checks for the inputs.

If all validation passes, add a message above the form indicating the form passed validation.

## Rules

-   Sharing APIs and copying and sharing of any code will result in your assignment being given a mark of zero.
-   You may only use plain JavaScript for this assignment, no libraries or frameworks. You will be given a mark of zero if you use a library or framework for your JavaScript code.

## Submission

-   Create a repository in your GitHub account called `your-name-js1-ca`, e.g. `mary-smith-js1-ca`, and **make sure it's public**
-   If you downloaded the repository you can simply commit and push your code to your repository
-   If you cloned the repository you can change the origin url so that pushes will be sent to your repo:

```js
git remote set-url origin NEW_URL
```

where `NEW_URL` is your repo's URL.

-   Submit the repo link

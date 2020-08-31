# Module Assignment 4

## Level 1

<h5 class="question">Question 1</h5>

Add the following HTML and CSS to a page called `question1.html`.

```html
<form id="contactForm">
    <div>
        <input type="text" id="lastName" placeholder="First name (minimum 5 characters)" />
        <div id="lastNameError" class="error">Your last name must be at least 5 characters</div>
    </div>
    <div>
        <button type="submit">Submit</button>
    </div>
</form>
```

```css
.error {
    color: red;
    display: none;
}
```

Write code that checks that the `lastName` input's value is at least 5 characters long when the form is submitted.

Show/hide the error message every time the validation runs.

---

<h5 class="question">Question 2</h5>

Add the following to a page called `question2.html`:

Make a call to `https://api.rawg.io/api/games?dates=1999-01-01,1999-12-31&ordering=-rating`.

For each game object in the results, create HTML that displays at least 3 properties from the objects. You can include an image property or leave it out. 

Link from each game to `question3.html` and pass the id of each game in the querystring.

---

<h5 class="question">Question 3</h5>

Retrieve the id paramater from the querystring and add it to the following URL: `https://api.rawg.io/api/games/`

Make a call to the API with the new URL and display at least 4 properties from the result.


## Submission

-   Create a repository in your GitHub account called `your-name-js1-ma4`, e.g. `mary-smith-js1-ma4`, and **make sure it's public**
-   Create an `.html` file and a `.js` file for each question
    -   question1.html
    -   question2.html
    -   question3.html
    -   /js/question1.js
    -   /js/question2.js
    -   /js/question3.js

You can also add `.css` files or add the styles on the page with `<style>` tags.

-   Add, commit and push these files to your repo
-   Submit the repo link

# Module Assignment 3

## Level 1

<h5 class="question">Question 1</h5>

Convert the function below to an arrow function:

```js
function division(a, b) {
    return a % b;
}
```

<h5 class="question">Question 2</h5>

Make a call to the following API endpoint:

```
https://api.rawg.io/api/games?dates=2019-01-01,2019-12-31&ordering=-rating
```

Loop through the results and display the following properties in HTML, but only for the first 8 results:

- name
- rating
- number of tags (not the tag details, just the amount of tags)

The styling for this assingment is not important. but some kind of loading indicator should be displayed while the API call is in progress.

Be sure to handle any potential errors in the code.

You can use either regular promise or async/await syntax to make the call.

Be sure to arrange all file types appropriately, consult the repos from the lessons for examples.

---

## Submission

-   Create a repository in your GitHub account called `js1-ma3` and **make sure it's public**
-   Add your answer for question 1 in a file called `question-1.js`
-   Add your answer for question 2 in a file called `question-2.js`
-   Add, commit and push your files - both `.js` files and any `.html` and `.css` files you may create - to this repo
-   Submit the repo link

# Module Assignment 1

The HTML and JS file for this assignment can be found in <a href="https://github.com/NoroffFEU/ma-javascript1-module1" target="_blank">this repo</a>.

## Level 1

<h5 class="question">Question 1</h5>

Create an object called `cat`.

Give the object one property called `complain`. `complain`'s value should be a method (a function) which logs the string `"Meow!"`.

<h5 class="question">Question 2</h5>

Select the `h3` from the HTML using the `querySelector` method and assign it to a variable called `heading`.

Change its `innerHTML` value to "Updated heading". 

<h5 class="question">Question 3</h5>

Use the `style` property on the `heading` variable from the question above to change its font size to `"2em"`.

<h5 class="question">Question 4</h5>

Add a class to the `heading` variable called `subheading`.

<h5 class="question">Question 5</h5>

Write code that selects all the `p` elements on a page and assigns them to a variable called `paragraphs`.

Loop through the `p` elements and change the colour of each to "red". 

<h5 class="question">Question 6</h5>

Select the `div` with a class of `results`, assign it to a variable called `resultsContainer` and set its inner HTML to be `<p>New paragraph</p>` and its background colour to be `yellow`.

<h5 class="question">Question 7</h5>

Create a function that has one parameter called `list`.

Inside the function, loop through the `list` parameter and console log the `name` property in each object.

Call the function and pass in the `cats` variable in the `script.js` file in the repo.


<h5 class="question">Question 8</h5>

Create a function called `createCats`. The function will have one parameter called `cats`.

Inside the function loop through the value passed in as `cats` and create HTML for each object in the array.

Wrap each item in a div, each `name` property in an `h5` tag and each `age` property in a `p` tag.

If the `age` property is missing, it should display `Age unknown` instead. 

Return the HTML from the function.

Call the function and pass in the `cats` array as the argument.

Assign the return value of the function to the `innerHTML` property of the element on the HTML page with a class of `cat-container`.

The function should return the following:

```html
<div>
    <h5>Blob</h5>
    <p>10</p>
</div>
<div>
    <h5>Harold</h5>
    <p>Age unknown</p>
</div>
<div>
    <h5>Blurt</h5>
    <p>21</p>
</div>
```

It doesn't have to be formatted like that, yours will look more like a single string, similar to below:

```html
<div><h5>Blob</h5><p>10</p></div><div><h5>Harold</h5><p>Age unknown</p></div><div><h5>Blurt</h5><p>21</p></div>
```
---

## Submission

- Create a repository in your GitHub account called `your-name-js1-ma1`, e.g. mary-smith-js1-ma1, and __make sure it's public__
- All your answers can go in `script.js`.
- Place a comment above each answer indicating the question number:


```js

// question 1

// your answer for question 1 goes here

// question 2

// your answer for question 2 goes here

// etc

```

- Add, commit and push this file to your repo
- Submit the repo link


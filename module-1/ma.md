# Module Assignment 1

## Level 1

<h5 class="question">Question 1</h5>

Create an object called `cat`.

Give the object one property called `complain`. `complain`'s value should be a method (a function) which logs the string `"Meow!"`.

<h5 class="question">Question 2</h5>

Select the `h3` from the HTML below using the `querySelector` method and assign it to a variable called `heading`.

```html
<h3>Subheading</h3>
```

<h5 class="question">Question 3</h5>

Use the `style` property on the `heading` variable from the question above to change its font size to `"2em"`.

<h5 class="question">Question 4</h5>

Add a class to the `heading` variable called `subheading`.

<h5 class="question">Question 5</h5>

Write code that selects all the `p` elements on a page and assigns them to a variable called `paragraphs`.

<h5 class="question">Question 6</h5>

Select the `div` by its class from the HTML below, assign it to a variable called `resultsContainer` and set its inner HTML to be `<p>New paragraph</p>`.

```html
<div class="results"></div>
```

<h5 class="question">Question 7</h5>

Create a function that has one argument called `catArray`.

Inside the function, loop through the `catArray` argument and console log the `name` property in each object.

Call the function and pass in the `cats` variable below.

```js
const cats = [
    {
        name: "Blob",
        age: 10
    },
    {
        name: "Harold",
    },
    {
        name: "Blurt",
        age: 21
    }
];
```

<h5 class="question">Question 8</h5>

Using the function and `cats` variable from the above question, instead of logging the `name` property, wrap each `name` property in an `h5` tag, add it to a variable you declare before the loop and return the variable from the function after the loop.

The function should return the following:

```html
<h5>Blob</h5>
<h5>Harold</h5>
<h5>Blurt</h5>
```

<h5 class="question">Question 9</h5>

Call the function from question 8, pass it the `cats` variable from question 7 and 
set the inner HTML of the `resultsContainer` variable from question 6 to the return value of the function.

<h5 class="question">Question 10</h5>

Using the function from question 8, add a `p` element containing the `age` property from each object. If the `age` property is missing, it should display `Age unknown` instead. 

Warp the `h5` and `p` in a `div`.

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

---

## Submission

- Create a repository in your GitHub account called `js1-ma1` and __make sure it's public__
- Create a file called `{your-name}-js1-ma1.js`, e.g. `mary-smith-js1-ma1.js`
- Write your answers inside this file with a comment above each answer indicating the question number:


```js

// question 1

// your answer for question 1 goes here

// question 2

// your answer for question 2 goes here

// etc

```


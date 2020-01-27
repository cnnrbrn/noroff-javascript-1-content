# Module Assignment 2

## Level 1

<h5 class="question">Question 1</h5>
<small>Refer: lesson 1</small>

Create a function expression by assigning an anonmyous function to a variable called `myFunctionExpression`. The function should console log your name. 


<h5 class="question">Question 2</h5>
<small>Refer: lesson 2</small>

Select the `button` in the HTML below by its **class**. Add a `click` event listener. The callback function passed to the event listener should log the sentence `I was clicked`.

You can pass the function in directly, declare it and pass it in by its name or assign it to a variable and pass it in by the variable name.

```html
<button class="btn">Click me</button>
```

<h5 class="question">Question 3</h5>
<small>Refer: lesson 2</small>

Select the `input` in the HTML below by its **id**. Add a `keydown` event listener. The callback function passed to the event listener should log the value of the key that was pressed.

```html
<input class="input" id="firstName"></div>
```


<h5 class="question">Question 4</h5>
<small>Refer: lesson 2 / 3</small>

Select the `button` in the HTML below by its **tag**. Add a `mouseover` event listener. The callback function should add a class called `hover` to the button.

```html
<button class="btn" data-animal="dog">Hover over me</button>
```

<h5 class="question">Question 5</h5>
<small>Refer: lesson 2 / 3 </small>

Select the `button` in the HTML below by its **data attribute** and add a `mouseout` event listener to it. The callback function should remove the class called `hover` from the button.

```html
<button class="btn" data-animal="dog">Hover over me</button>
```

<h5 class="question">Question 6</h5>
<small>Refer: lesson 3 </small>

Select all the `li` tags from the HTML below. Using a loop, add a `mouseover` event listener to each tag.

The callback function should log the value of the data attribute on each element when the cursor moves over it.

```html
<ul>
    <li data-animal="goose">Animal 1</li>
    <li data-animal="frog">Animal 2</li>
    <li data-animal="elephant">Animal 3</li>
</ul>
```


<h5 class="question">Question 7</h5>
<small>Refer: lesson 3</small>

Convert the `if-else-if` statement below to a `switch` statement. Use the code inside the `else` block in the default block in the switch.

```js
const animal = "cow";

if(animal === "cat") {
    console.log("Meow");
}
else if(animal === "cow") {
    console.log("Moo");
}
else if(animal === "bird") {
    console.log("Tweet");
}
else {
    console.log("Harrumph");
}
```


<h5 class="question">Question 8</h5>
<small>Refer: lesson 4 </small>

Convert the `for loop` code below to a `forEach` loop.

```js
const sheep = ["Malcolm", "Anders", "Marie"];

for(let i = 0; i < sheep.length; i++) {
    console.log(sheep[i]);
}
```

<h5 class="question">Question 9</h5>
<small>Refer: lesson 4 </small>

Create a timer that logs the word `hello` every half a second. It must stop after its logged the word 6 times. 


<h5 class="question">Question 10</h5>
<small>Refer: lesson 4 </small>

Select the div from the HTML below. Write code that updates the div's text to say `Text updated` after waiting 2 seconds. You can use either `innerText` or `innerHTML` to update the text.

```html
<div class="container">Placeholder text</div>
```

---

## Submission

- Create a repository in your GitHub account called `js1-ma2` and __make sure it's public__
- Create a file called `{your-name}-js1-ma2.js`, e.g. `mary-smith-js1-ma2.js`. This is the only file you need to submit.
- Write your answers inside this file with a comment above each answer indicating the question number:


```js

// question 1

// your answer for question 1 goes here

// question 2

// your answer for question 2 goes here

// etc

```

- Add, commit and push this file to your repo
- Submit the repo link


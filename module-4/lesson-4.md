# Lesson 4 - Practice questions

<h5 class="question">Question 1</h5>

Looping through arrays of objects is important because that's how lists of results get returned from API calls.

---

<small>
    Refer: 
    <ul>
        <li>
            Loops - <a href="https://interactive-content.now.sh/programming-foundations/1/4">Programming Foundations Module 1 Lesson 4</a>
        </li>
        <li>
            Arrays of objects - <a href="https://interactive-content.now.sh/programming-foundations/2/3">Programming Foundations Module 2 Lesson 4</a>
        </li>
        <li>
            forEach - <a href="https://interactive-content.now.sh/javascript-1/2/4">JavaScript 1 Module 2 Lesson 4</a>
        </li>
    </ul>
</small>

Loop through the array below (with a `for` loop or a `forEach` loop) and log each property's age value. Log `"Unknown"` if it is missing.

```js
const cars = [
    {
        type: "BMW",
        age: 4,
        beenInAccident: false
    },
    {
        type: "Toyota",
        beenInAccident: true
    },
    {
        type: "Ford",
        beenInAccident: true
    }
];
```
> The answer can be found [here](https://github.com/javascript-repositories/js1-lesson-answers/blob/module-4-lesson-4-question-1/script.js).

---

<h5 class="question">Question 2</h5>

Functions allow us to create reusable code. We can return values from functions and assign those return values to variables.

<small>
    Refer: 
    <ul>
        <li>
            Functions - <a href="https://interactive-content.now.sh/programming-foundations/2/4">Programming Foundations Module 2 Lesson 4</a>
        </li>
        <li>
            Creating HTML from arrays of objects - <a href="https://interactive-content.now.sh/javascript-1/1/3">JavaScript 1 Module 1 Lesson 3</a>
        </li>
    </ul>
</small>

```js
const elephants = [
    { image: "https://elephant-api.herokuapp.com/pictures/001.jpg", note: "Given to a Carolingian emperor." },
    { image: "https://elephant-api.herokuapp.com/pictures/missing.jpg", note: "From the Mysore Dasara procession." },
    { image: "https://elephant-api.herokuapp.com/pictures/missing.jpg", note: "Known for her tightrope walking act." }
];
```

Create a function that receives one argument. When you call the function pass the `elephants` array above into the function.

Inside the function, loop through the array and create an `img` tag for each object, with `src` and `alt` attributes created from the properties in each object.

Return the created HTML from function.

Assign the return value of the function to a variable and console log it.

It will look similar to this (though it will be one long string).

```js
<img src="https://elephant-api.herokuapp.com/pictures/001.jpg" alt="Given to a Carolingian emperor.">
<img src="https://elephant-api.herokuapp.com/pictures/missing.jpg" alt="From the Mysore Dasara procession.">
<img src="https://elephant-api.herokuapp.com/pictures/missing.jpg" alt="Known for her tightrope walking act.">
```

> The answer can be found [here](https://github.com/javascript-repositories/js1-lesson-answers/blob/module-4-lesson-4-question-1/script.js).

---
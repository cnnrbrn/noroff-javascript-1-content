# Lesson 3 - Creating HTML from arrays of objects

## Arrays as properties of objects

We've seen that objects can have `strings`, `numbers`, `booleans` and `functions` as property values. Object properties can also hold `arrays`:

```js
const dogs = {
    breeds: ["golden retriever", "labrador", "poodle"]
};

console.log(dogs.breeds);
// ["golden retriever", "labrador", "poodle"]

```

## JSON

`JSON` stands for `J`ava`S`cript `O`bject `N`otation.

It is used to exchange data, and is used by REST APIs to send data between browsers (or apps) and servers.

It looks like a normal JavaScript object:

```js
{   
    id: 1,
    age: 7,
    type: "dog",
    dangerous: true,
    likes: ["barking", "sleeping"]
}
```

If we made an API call to get the data for a specific pet, it may look something like the above.

If we made an API call to get a list of pets, it may look like something like this:

```js
{   
    count: 2,
    pets: [
        {
            id: 1,
            age: 7,
            type: "dog",
            dangerous: false,
            likes: ["barking", "eating"]
        },
        {
            id: 2,
            age: 4,
            type: "cat",
            dangerous: true,
            likes: ["sleeping", "complaining"]
        }
    ]
}
```

The `pets` property is an array of objects. We would get it from the JSON object using dot notation and loop through it to create HTML and display its contents.
 
### Loading multiple JavaScript files

You can link to multiple JavaScript files from an HTML page, and variables and statements will be available in the order they are included.

If you load multiple files like this:

```html
<script src="js/script1.js"></script>
<script src="js/script2.js"></script>
```

Anything declared in `script1.js` will be available to the code in `script2.js`.

For example, if the following code was in `script1.js`

```js
// this is in script1.js
const pet = "dog";

function bark() {
    console.log("Woof!");
}
```

we could use both `pet` and `bark()` in `script2.js`:

```js
// this is in script2.js
console.log(pet);
// dog

bark();
// Woof!
```

> If you tried to declare a variable called `pet` or `bark` in `script2.js`, you would get an error saying they've already been declared.

 ---

## Creating HTML

You will need to clone the course repository to follow along from here.

> If you don't like working in the terminal or command line when using `git`, you can use the git functionality in VSCode (to checkout branches) or a GUI like [GitKraken](https://www.gitkraken.com/).

 Clone the repo from [here](https://github.com/javascript-repositories/javascript-1-lesson-code). You will be on the `step-0` branch.

At the end of `index.html` we are loading four script files:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>JavaScript 1</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" crossorigin="anonymous" />
        <link rel="stylesheet" href="css/style.css" />
    </head>

    <body>
        <div class="container"></div>

        <script src="js/data/actionGames.js"></script>
        <script src="js/data/shooterGames.js"></script>
        <script src="js/data/rpgGames.js"></script>
        <script src="js/script.js"></script>
    </body>
</html>
```

The variables declared in `js/data/actionGames.js`, `js/data/shooterGames.js` and `js/data/rpgGames.js` will be available in `js/script.js` because they are loaded before `js/script.js`.

The array of objects assigned to the variables in `actionGames.js`, `shooterGames.js` and `rpgGames.js` were created (and edited) from calls to the [RAWG](https://api.rawg.io/docs/) API, using the `genres` variable in the `query string` (the part of the URL after the `?`) to fetch the different genres.

You can make the calls in [Postman](https://www.getpostman.com/downloads/) and see what they return.

You can use the following URLs to make the GET requests:

- action games - `https://api.rawg.io/api/games?genres=action`
- shooter games - `https://api.rawg.io/api/games?genres=shooter`
- RPG games - `https://api.rawg.io/api/games?genres=role-playing-games-rpg`

In a later lesson we will make live calls to the API, but for now we will use the variables  in the `js/data/*` files.

In `js/script.js`, we will first select the `div` with the `container` class.

```js
const container = document.querySelector(".container");
```

We'll then create a variable to hold the `HTML` strings we'll be creating. Because the value assigned to this variable will change, we'll declare the variable with `let`:

```js
let newHTML = "";
```

The variable `actionGames`, declared in `js/data/actionGames.js` is available in our `js/script.js` file.

```js
// js/data/actionGames.js
const actionGames = [
    {...}
]
```

If you open `actionGames.js` you will see it contains an array of four objects assigned to a variable.

Let's loop over the array and log the name of the games:

```js
for (let i = 0; i < actionGames.length; i++) {
    console.log(actionGames[i].name);
}
// Grand Theft Auto V
// The Elder Scrolls V: Skyrim
// Left 4 Dead 2
// Borderlands 2
```

What your `js/script.js` should look like now:

```js
// we declare both these variables outside the for loop
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {

    console.log(actionGames[i].name);
}
```

### Template literals

We've seen before that we can join strings together using the `+` sign.

We could create an HTML string with the name of the game in the loop like this:

```js
    const name = "<h4>" + actionGames[i].name + "</h4">;
```

We could do that inside the loop and log each `name` variable wrapped in an `h4` tag:

```js
for (let i = 0; i < actionGames.length; i++) {
    // create the HTML string by joining the strings together
    const name = "<h4>" + actionGames[i].name + "</h4">;
    console.log(name);
}
```

That would log:

```js
// <h4>Grand Theft Auto V</h4>
// <h4>The Elder Scrolls V: Skyrim</h4>
// <h4>Left 4 Dead 2</h4>
// <h4>Borderlands 2</h4>
```

If we wanted to create a lot of HTML across multiple lines, this way of doing it would quickly become messy and difficult to read.

[Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) give us a more readable way to create multiline strings with variables inside them.

Template literals use backticks and we embed variables inside a dollar sign `$` and curly braces `{}`: `${}`

Using template literals we could rewrite this

```js
const name = "<h4>" + actionGames[i].name + "</h4">;
```

like this 

```js
const name = `<h4>${actionGames[i].name}</h4>`;
```

Let's make that a multiline line string by adding more HTML elements. We'll change the variable name from `name` to `details`:

```js
const details = `<div>
                    <h4>${actionGames[i].name}</h4>
                </div>`;
```

Let's add a class to the `div` and `h4`:

```js
const details = `<div class="details">
                    <h4 class="name">${actionGames[i].name}</h4>
                </div>`;
```

Let's add the `rating` property in a div with a class of `rating`:

```js
const details = `<div class="details">
                    <h4 class="name">${actionGames[i].name}</h4>
                    <div class="rating">${actionGames[i].rating}</div>
                </div>`;
```

What your `js/script.js` should look like now:

```js
// we declare both these variables outside the for loop
const container = document.querySelector(".container");
// newHTML's value will change so we use let to declare it
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    // each time the loop is executed, assign the details variable a template literal
    // this is a string with embedded variables
    const details = `<div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${actionGames[i].rating}</div>
                    </div>`;
}
```

Inside the loop, let's add the value of the `details` variable to the `newHTML` variable:

```js
// assign the existing value of newHTML plus the details variable to newHTML
newHTML = newHTML + details;
```

We can use the `+=` shorthand:

```js
// assign the existing value of newHTML plus the details variable to newHTML
newHTML += details;
```

Once the loop has finished, the `newHTML` variable will hold all the HTML created in the loop.

We can assign that to be the value of the `container` variable's (the `div` tag with the class of `container` we selected in the beginning) `innerHTML` property. 

We do this assignment after the loop has finished:

```js
container.innerHTML = newHTML;
```

What your `js/script.js` should look like now:


```js
// we declare both these variables outside the for loop
const container = document.querySelector(".container");
// newHTML's value will change so we use let to declare it
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    // each time the loop is executed, assign the details variable a template literal
    // this is a string with embedded variables
    const details = `<div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${actionGames[i].rating}</div>
                    </div>`;
    // add the value of details to the existing value of newHTML
    newHTML += details;
}

// set container's innerHTML property to be the HTML that was created in the loop
container.innerHTML = newHTML;
```

Without the comments:

```js
const container = document.querySelector(".container");
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {

    const details = `<div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${actionGames[i].rating}</div>
                    </div>`;
    newHTML += details;
}

container.innerHTML = newHTML;
```

Your `index.html` page will now contain the following HTML:

```html
<div class="container">
    <div class="details">
        <h4 class="name">Grand Theft Auto V</h4>
        <div class="rating">4.48</div>
    </div>
    <div class="details">
        <h4 class="name">The Elder Scrolls V: Skyrim</h4>
        <div class="rating">undefined</div>
    </div>
    <div class="details">
        <h4 class="name">Left 4 Dead 2</h4>
        <div class="rating">4.09</div>
    </div>
    <div class="details">
        <h4 class="name">Borderlands 2</h4>
        <div class="rating">4.07</div>
    </div>
</div>
```

Let's add a `div` with its `background-image` CSS property set to the `background_image` property from the object and a `div` with a class of `"card"` to wrap each game:

```js
const details = `<div class="card">
                    <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                    <div class="details">
                        <h4 class="name">${actionGames[i].name}</h4>
                        <div class="rating">${actionGames[i].rating}</div>
                    </div>
                </div>`;
```

Your `index.html` page should look similar to this now, depending on the size of your screen:

<img src="/images/js1/site-1.png" alt="Site example 1" style="max-width:800px">

### Default values for missing properties

Sometimes data returned from an API call will contain missing properties in the objects. The `The Elder Scrolls V` game is missing its rating property and is displaying `undefined`.

Let's provide a default value for that property if it's missing so that we give the user a more meaningful message than `undefined`.

Inside the loop, we'll create a variable called `ratingValue` with a value of `"Not rated"`. This value may change so we'll use `let` to declare it.

```js
// create a default value for the rating
let ratingValue = "Not rated";
```

Then we'll check if the `rating` property on the object exists, if it's not one of the `falsy` values (null, undefined, an empty string, etc) we looked at in lesson 1.

If it exists, we'll assign its value to the `ratingValue` variable.

```js
// if the object contains a rating property
// set the ratingValue equal to the rating property
if (actionGames[i].rating) {
    ratingValue = actionGames[i].rating;
}
```

Then when we create the `HTML` we'll use the `ratingValue` variable, not the `rating` property from the object.

This way, if the `rating` property is missing, the user will see the default value for `ratingValue` - `"Not rated"` - instead of `undefined`.

```js
`<div class="rating">${ratingValue}</div>`
```

---

#### The full code

```js
// we declare both these variables outside the for loop
const container = document.querySelector(".container");
// newHTML's value will change so we use let to declare it
let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {
    // create a default value for the rating
    let ratingValue = "Not rated";

    // if the object contains a rating property
    // set the ratingValue variable equal to the rating property
    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    // each time the loop is executed, assign the details variable a template literal
    // this is a string with embedded variables
    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                        </div>
                    </div>`;
    // add the value of details to the existing value of newHTML
    newHTML += details;
}

// set container's innerHTML property to be the HTML that was created in the loop
container.innerHTML = newHTML;
```

#### Without the comments

```js
const container = document.querySelector(".container");

let newHTML = "";

for (let i = 0; i < actionGames.length; i++) {

    let ratingValue = "Not rated";

    if (actionGames[i].rating) {
        ratingValue = actionGames[i].rating;
    }

    const details = `<div class="card">
                        <div class="image" style="background-image: url(${actionGames[i].background_image});"></div>
                        <div class="details">
                            <h4 class="name">${actionGames[i].name}</h4>
                            <div class="rating">${ratingValue}</div>
                        </div>
                    </div>`;
    newHTML += details;
}

container.innerHTML = newHTML;
```

---
- [Go to lesson 4](4) 
---
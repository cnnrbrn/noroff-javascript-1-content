# Lesson 3 - Creating HTML from objects

In this lesson we'll look at:

-   arrays as properties of objects
-   JSON - JavaScript Object Notation
-   loading multiple JavaScrpipt files
-   creating HTML from objects

## Arrays as properties of objects

We've seen that objects can have `strings`, `numbers`, `booleans` and `functions` as property values. Object properties can also hold `arrays`:

```js
const dogs = {
    breeds: ["golden retriever", "labrador", "poodle"]
};

console.log(dogs.breeds);
// ["golden retriever", "labrador", "poodle"]
```

<iframe src="https://scrimba.com/c/cKg2e7uP" width="640" height="440" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://scrimba.com/c/cKg2e7uP" target="_blank">Scrimba link</a>

---

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

The `pets` property is an array of objects. We would select it from the JSON object and loop through it to create HTML and display its contents.

The video below takes a look at how JSON is sent from a server through an API call.

<iframe src="https://player.vimeo.com/video/444361111" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

---

### Loading multiple JavaScript files

You can link to multiple JavaScript files from an HTML page, and variables and functions will be available in the order they are included.

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

> If you tried to declare a variable called `pet` or `bark` in `script2.js` with the const or let keywords, you would get an error saying they've already been declared.

<iframe src="https://player.vimeo.com/video/444338027" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

---

## Creating HTML from objects

The next three videos examine creating HTML from objects.

### Using a single object to create HTML

The first video looks at creating HTML from a single object's properites and adding default values for missing properties.

<iframe src="https://player.vimeo.com/video/444562202" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

The code from the video is on the [master branch](https://github.com/NoroffFEU/creating-html-from-an-array-of-objects) of this repo.

---

### Setting the innerHTML of individual elements

This video looks at setting the innerHTML property of individual DOM elements from a single object.

<iframe src="https://player.vimeo.com/video/444582197" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

The code from the video is on the [part-2 branch](https://github.com/NoroffFEU/creating-html-from-an-array-of-objects/tree/part-2) of the repo.

---

### Creating HTML from an array of objects

In this video HTML is created by looping through an array of objects.

<iframe src="https://player.vimeo.com/video/444696340" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

The code from the video is on the [part-3 branch](https://github.com/NoroffFEU/creating-html-from-an-array-of-objects/tree/part-3) of the repo.

---

## Lesson Task

There are practice questions in the master branch of [this repo](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson3).

Attempt the answers before checking them against the answers in the [answers branch](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson3/tree/answers) of the repo.

---

[Go to lesson 4](4)

---

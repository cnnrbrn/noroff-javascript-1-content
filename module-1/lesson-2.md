# Lesson 2 - Manipulating the DOM

Manipulating the DOM means adding, editing and deleting content on a web page.

---

> **It is a good idea to type out the code examples as you follow the lessons.**

---

## DOM selectors

To manipulate the DOM, we first need to select an element on which we can do this manipulation.

A lot of tutorials use `getElementById` to select a node - an HTML element - by its id attribute. This was one of the first ways to select something in the DOM and is still valid. We, however, will be using the newer:

- `querySelector` - to select one element, such as a single `h1` element on a page.
- `querySelectorAll`  - to select many elements, such as all the `li` tags in a `ul` element.

We can call both these methods from the `document` object:

```js
document.querySelector();
document.querySelectorAll();
```

The argument we pass in to each of these methods is the element we want to select: a tag (`"h1"`), a class (`".heading2"`) or an id (`"#accordion"`).

```js
// this will select the first h1 element on the page
document.querySelector("h1");

// this will select the first element on the page that has a class of .heading2
document.querySelector(".heading2");

// this will select the first element on the page that has an id of accordion.
// There shouldn't be more than one element with a particular id on a page.
document.querySelector("#accordion");

// this will select all li elements on the page
document.querySelectorAll("li");
```

Create an `index.html` page and link a `script.js` file to it. Add the following HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>The DOM</title>
    <style>
        .container {
            border: 2px solid red;
            height: 200px;
        }
        .red {
            color: red;
        }
    </style>
</head>
<body>
    <h1>Hello</h1>

    <h2 class="heading2">World</h2>

    <ul id="list">
        <li>Dog</li>
        <li>Cat</li>
        <li>Donkey</li>
    </ul>
    
    <div></div>

    <script src="js/script.js"></script>
</body>
</html>
```

First, we'll use `querySelector` to select single elements on the page.

We'll select the `h1` by its tag name and log it using `dir` so that a clickable list of its properties is displayed:
```js
console.dir(document.querySelector("h1"));
```

<img src="/images/js1/h1-dir.png" alt="h1 dir" style="max-width:350px">

There are a lot of properties that get displayed. Some notable ones are:

- `style` - this is an object which has all the CSS properties on it. We can change these properties using JavaScript. Notice that the CSS properties don't use hyphens `-` like they do in CSS, but rather `camelCase` - they start with a small letter and "joined" words are capitalised, not hyphenated. Using hyphens in variable names and properties is not allowed in JavaScript.
- `className` - a string value of all the classes on an element. If the element has no classes, this is an empty string.
- `classList` - this is an object of the CSS classes on the element. The `h1` tag has no classes on it.
- `innerText` - this is a string value of the text inside the selected element.
- `innerHTML` - this is a string containing the HTML content inside the element. The `h1` tag doesn't contain any HTML, just the string `"Hello"`. We will soon use the `innerHTML` property to create HTML content inside a selected element.


Let's select the `h2` element by its tag name and assign it to a variable:
```js
const heading2 = document.querySelector("h2");
console.dir(heading2);
```

This time the `classList` property is not empty, it has the value `"heading2"`.

Because the `h2` element has a class, we can select it by its class.

```js
const headingByClass = document.querySelector(".heading2");
console.dir(headingByClass);
```

This will display the same list of properties as above because the same element has been selected.

Let's select the `ul` by its id:

```js
const list = document.querySelector("#list");
console.dir(list);
```

The above is the same as the `getElementById` method that you may see in other study material:
```js
const list = document.getElementById("list");
console.dir(list);
```

The `innerHTML` property for `list` displays a `string` version of the HTML inside the `ul`.

If we use `querySelector` and the selection string (the value used to select the element) occurs more than once on the page, the first occurence of the element is selected.

We can see that if we select `"li"` using `querySelector`: 

```js
const listItem = document.querySelector("li");
console.dir(listItem);
```

This diplays only one `li` element, the first one with the `innerText` value of `"Dog"`.

To select all the `li` elements, use `querySelectorAll`:

```js
const listItems = document.querySelectorAll("li");
console.dir(listItems);
```

This displays a `NodeList` (a type of object) with all the `li` elements as properties.

<img src="/images/js1/nodelist.png" alt="NodeList" style="max-width:350px">


Although this is not an array, we can loop over the NodeList using brackets to get each item. The syntax looks the same as looping over an array:

```js
for(let i =0; i < listItems.length; i++) {
    console.dir(listItems[i]);
}
```

This will log each `li` element object.

We can log any property on the `li` object using dot notation. 

Let's use a `for loop` to log the `innerText` value of each `li`:

```js
for(let i =0; i < listItems.length; i++) {
    console.dir(listItems[i].innerText);
}

// Dog
// Cat
// Donkey
```

## Manipulating the elements

> If you enter the following code examples in the browser console you will be able to see the changes to the DOM happening in real-time.

### style

Let's select the `h1` element and change its `color` property on its `style` object:

```js
const heading1 = document.querySelector("h1")
heading1.style.color = "purple";
```

If you inspect the `h1` element you will see an inline style has been added:

```html
<h1 style="color: purple;">Hello</h1>
```

The `style` object on an element contains all the CSS properties, so we can change any of those properties by assigning string values to them.

Let's add a border:

```js
heading1.style.border = "1px green solid";
```

Now let's add a background colour and some padding:

```js
heading1.style.backgroundColor = "lightGray";
heading1.style.padding = "1em";
```

As we noted above, all hyphenated CSS properties become camel cased when using JavaScript, e.g. `background-color` becomes `backgroundColor`.

### className and classList

Most of your styling is done through CSS classes on HTML elements. Let's add a class to the `div` element.

If we select the div using the `"div"` selector and log its `className` property, we can see it's empty:

```js
const div = document.querySelector("div");
console.log(div.className);
// nothing will be displayed
```

We can add a class using the `add` method on the `classList` object:
```js
div.classList.add("container");
console.log(div.className);
// container
```

We can add a second class:
```js
div.classList.add("second-class");
console.log(div.className);
// container second-class
```

### innerText

Let's use `innerText` to change the `h1` element's text value:

```js
const pageHeading = document.querySelector("h1");
pageHeading.innerText = "Updated using innerText";
```

Let's update the text value of all the `li`s.

We need to use `querySelectorAll` because we want to select more than one element:
```js
const allTheListItems = document.querySelectorAll("li");

// loop through all the li elements and change their innerText value
for(let i =0; i < allTheListItems.length; i++) {
    allTheListItems[i].innerText = i + " changed";
}
```

### innerHTML

We can also use `innerHTML` to change the `h1`'s value:

```js
const pageHeading = document.querySelector("h1");
pageHeading.innerHTML = "Updated using innerHTML";
```

We can also add `HTML` content to other elements using `innerHTML`. We will use backticks that we discussed in lesson 1:

```js
const container = document.querySelector("div");
container.innerHTML = `<p>
                        <b>Bold text:</b> unbolded text
                    </p>`;
```

We looked at joining strings together using `+` in Programming Foundations.

If we wanted to add an `li` to the `ul` element, we could do that by joining the existing `innerHTML` string value of the `ul` with a new string value containing the `li`:

```js
// select the ul
const list = document.querySelector("ul");

// get the existing HTML inside the ul element and assign it to a variable
const existingHTML = list.innerHTML;

// create the new li HTML
const newHTML = "<li>New item at the end</li>";

// set the ul's new HTML to the existing HTML plus the new HTML 
list.innerHTML = existingHTML + newHTML;
```

A new `li` element containing the text `New item at the end` will be added to the end of the list.

We could do that with fewer lines of code:

```js
const list = document.querySelector("ul");

list.innerHTML = list.innerHTML + "<li>New item at the end</li>";
```

If we wanted to put the new item at the beginning of the list we can reverse the order of the two strings:

```js
const list = document.querySelector("ul");

list.innerHTML = "<li>New item at the beginning</li>" + list.innerHTML;
```

A new `li` element containing the text `New item at the beginning` will be added as the first item in the list.

We can add a class to the new element inside the string:

```js
const list = document.querySelector("ul");

const newHTML = `<li class="red">
                    New item at the end
                </li>`;

list.innerHTML = list.innerHTML + newHTML;
```

When we are adding the HTML string to the end of the existing HTML string, we can use the shorthand `+=` operator:

```js
list.innerHTML += newHTML;
```

The `+=` operator adds the new string to the existing string, so is the same as:

```js
list.innerHTML = list.innerHTML + newHTML;
```

If we used the assignment operator `=` on its own like this:

```js
list.innerHTML = newHTML;
```

The existing HTML string would be replaced by `newHTML` and that's all the `list` would contain.

```html
<ul>
    <li class="red">
        New item at the end
    </li>
</ul>
```

---

In the [next lesson](3) we will loop through an array of objects and create new HTML elements from the objects using some of the above methods.

---

## Acivities

#### Read


#### Watch

[LinkedIn Learning: JavaScript Essential Training](https://www.linkedin.com/learning/javascript-essential-training-3/)

Watch the following videos:

Section 5. JavaScript and the DOM, Part 1: Changing DOM Elements:

- Target elements in the DOM with querySelector methods
- Access and change elements
- Access and change classes
- Access and change attributes
- Add DOM elements
- Apply inline CSS to an element

---
- [Go to lesson 3](3) 
---

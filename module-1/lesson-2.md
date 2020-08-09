# Lesson 2 - Manipulating the DOM

Manipulating the DOM means adding, editing and deleting content on a web page.

In this lesson we'll look at:

-   what the DOM is
-   how we can edit DOM elements

## The DOM

In Programming Foundations we briefly looked at `API`s - Application Programming Interfaces used by programs to communicate with each other. In particular we looked at REST APIs, used to communicate with a server.

The `DOM` is another type of API.

`DOM` stands for `D`ocument `O`bject `M`odel.

It is an interface, an API, provided by browsers to interact with and manipulate web pages.

If you view the source of a web page (right-click -> View Page Source), what is displayed is the content - the HTML, CSS, JavaScript, etc - sent to the browser by the server.

The browser uses the DOM to manipulate this content and display the web page.

Differences in how the DOM (and JavaScript) is implemented by browsers leads to differences in how web pages are displayed.

This was particularly a problem when Microsoft's Internet Explorer (IE) was the dominant browser. Microsoft didn't follow the EcmaScript standard which lead to frontend developers spending a lot of time trying to get pages to render properly in various versions of IE. Today, IE is no longer maintained by Microsoft and fewer companies are willing to spend time on IE fixes (though many places still drive their developers mad by insisting on catering for IE). Differences in how mobile versions of browsers implement the DOM are more likely nowadays to cause issues when trying to render correctly across various devices and browsers.

We can use JavaScript to manipulate the DOM, to add, edit and delete DOM elements and content.

### window and document objects

The `window` object is the parent object in a web page displayed by a browser.

One of the properties of the `window` object is `screen` that holds information about the screen.

Type `window.screen` or just `screen` in a console and press enter to see information about your screen.

Another property of window is `document`. The `document` is the `D` in `DOM`.

On any web page, enter the following in the console: `window document` or just `document`.

`document` contains all the nodes (HTML elements) in the DOM and also all the methods (functions) and properties the browser and developers can use to manipulate those elements.

```js
document.querySelector;
//f querySelector() {  }

document.querySelectorAll;
//ƒ querySelector() { }
```

The video below is an intro to the DOM.

<iframe src="https://player.vimeo.com/video/444052197" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

## DOM selectors

To manipulate the DOM, we first need to select an element on which we can do this manipulation.

A lot of tutorials use `getElementById` to select a node - an HTML element - by its id attribute. This was one of the first ways to select something in the DOM and is still valid. We, however, will be using the newer:

-   `querySelector` - to select one element, such as a single `h1` element on a page.
-   `querySelectorAll` - to select many elements, such as all the `li` tags in a `ul` element.

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

The video below explores selecting and editing DOM elements.

<iframe src="https://player.vimeo.com/video/444301212" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://github.com/NoroffFEU/manipulating-the-dom" target="_blank">Code from the video</a>

---

## Lesson Task

There are practice questions in the master branch of [this repo](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson2).

Attempt the answers before checking them against the answers in the `script.js` file in the [answers branch](https://github.com/NoroffFEU/lesson-task-js1-module1-lesson2/tree/answers) of the repo.

---

[Go to lesson 3](3)

---

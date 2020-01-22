# Lesson 1 - Introductory concepts

## Introduction

This first lesson contains JavaScript language features we will be using throughout the course and need to address in the beginning.

Further lessons will introduce concepts as we write code, providing practical examples and uses of the concepts.

Beginning in a later lesson, we will be building a website and using the [RAWG](https://api.rawg.io/docs/) video game database API for live server calls.

You will be provided with all the HTML and CSS required to build the site so you can concentrate on the JavaScript.

<!-- 
## Style guide
 -->

## VSCode

Some useful keyboard shortcuts:

- `ctrl`/`cmd`-`p` - find a file in your project
- `ctrl`/`cmd`-`d` - making a selection and using this shortcut will select all occurences of the selection in the file

[Code snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_create-your-own-snippets) can be very useful for things like `console.log` that you type out a lot.

> **Mac users:** if you install node to get an extension to work, please ***DO NOT*** install using sudo, it will create permission problems and is problematic to fix.


## ES6

`ECMAScript` (`ES`) is the official specification for JavaScript. It decides what features should be in the language.

`ES6`, or `ES2015`, was released in 2015 and introduced many improvements to the language after a long gap in updates to the specification.

New features are now continuously being added and, at the time of writing, the latest version is known as `ECMAScript 2019`. 

`ES6` is often, slightly confusingly, used to refer to the modern versions of JavaScript.

In the Programming Foundations course we didn't use any modern features of the language, but we will be using them throughout the JavaScript 1 course.

You can check the browser support for a feature (JavaScript and CSS) by using [caniuse.com](https://caniuse.com/)

[YoutTube video: ECMAScript, TC39, and the History of JavaScript](https://www.youtube.com/watch?v=gytOcNFV1dM)


<a id="const-let"></a>

## `const` and `let`

In the Programming Foundations course we used `var` to declare every variable. 

`ES6` introduced the `const` and `let` keywords for declaring variables. 

A key difference between `const` and `let` is that `let` can have its value reassigned, where as `const` cannot.

If we declare a variable using `const` and assign it a value:
```js
const count = 1;
```

we cannot reassign its value - we can't give it a different value.

We can't do this
```js
count = 2;
```

or this 

```js
count = count + 1;
```

Both the above statements try to assign a new value to `count`. This will give us an `Assignment to const variable` error.

<img src="/images/js1/const-reassignment-error.png" alt="const reassignment error" style="max-width:420px">

`count = count + 1` is equivalent to `count++`, and because that's how we change the counter variable in `for loops`, we need to use `let` because we can assign a new value to a variable declared with `let`. 

We can do this

```js
let count = 1;
count = 2;
count = count + 1;
```

so we can use that kind of declaration in loops:

```js
for(let count = 0; count > 10; count++) {

}
```

or

```js
for(let i = 0; i > 10; i++) {

}
```

A another diffrence between both `const` and `let` and `var` is how `scope` and `this` are handled. We will discuss these two concepts further when we reach practical examples of them.

There is unfortunately no standard way to use these two keywords, and some documentation uses `let` for all variables.

We will follow the very common practice of using `const` for most variables and only use `let` when we need to.


## The browser

All references to the "browser" refer to [Chrome](https://www.google.com/chrome/).

#### `console.log` vs `console.dir`

Until now, we have only used `console.log`. 

`console.dir` is similar, but when logging an object it will display a clickable, interactive list of the object's properties, while `console.log` only prints out a string version of the object. This is why we'll sometimes use `dir` instead of `log`.

In the dev tools console, enter the following to see the difference:

> We are going to start using `const` instead of `var` (and `let` when necessary).

```js
const pet = {
    type: "dog"
};

console.log(pet);

console.dir(pet);
```

---

## Strings using backticks `

Previously we've seen that we can create strings using double or single quotes, and that you should pick one and use it consistently (for any Noroff code use double quotes).

There is another way to create strings, with backticks `. On many keyboards the key is in the top left.

Using backticks gives us an easy way to split strings across lines:

```js
const sentences = `First sentence.
                   Second sentence.`;
```

This is a far cleaner way to get new lines in strings than using either double or single quotes.

There is another very useful feature of backticks which we will cover in a later lesson.

## Data types and truthy and falsy values

In Programming Foundations, we looked at five different data types in JavaScipt:

- `string`
- `number`
- `boolean`
- `undefined`
- `null`

We also looked at `objects`, `arrays` and `functions`.

The first five (together with `bigInt` and `symbol` - neither of which we will use in this course) are considered `primitive` types, they are built-in to the language.

All other values are built from objects, including arrays and functions.

> An unhelpful "feature" in JS: If you use the `typeof` operator on an array, it will return `object`. If you use typeof on a function, it will return `function`.

Each value also has a `boolean` value associated with it, known as `truthy` or `falsy`.

The following values are `falsy`:

- 0 (zero)
- false
- "", '' or `` - empty strings
- null
- undefined
- Nan - `N`ot `a` `N`umber

Every other value is `truthy`. 

If we are trying to check if a value exists, if it isn't `null` or `undefined`, for example, we can do this:

```js
if(someVariable) {
    console.log("someVariable exists");
}
```

rather than having to check for both `null` and `undefined` like this:

```js
if(someValue !== null && someValue !== undefined) {
    console.log("someValue exists");
}
```

That applies to all the falsy values, so we can check that a variable's value is not one of the `falsy` values by writing an `if statement` like the one above and below:

```js
if(someVariable) {
    // someVariable exists, do something with it
}
```


## Accessing object properties using brackets

Previously we have accessed object properties using dot `.` notation. 

We can also access them using brackets `[]`, with the key of the property as the value inside the brackets:

```js
const pet = {
    type: "dog"
};

console.log(pet["type"]);
// dog

// this is the same as 
console.log(pet.type);
// dog
```


## Methods - Functions as properties of objects

We've previously seen `objects` with properties having `string`, `number` or `boolean` values.

```js
const dog = {
    name: "Burt",
    age: 7,
    dangerous: false
}

console.log(dog.age)
// 7
```

Objects can also have `functions` as properties:

```js
const dog = {
    name: "Burt",
    age: 7,
    dangerous: false,

    // bark is a property with a function as its value
    bark: function() {
        console.log("Woof!");
    }
}
```

If we log the `bark` property, the function declaration will be logged:

```js
console.log(dog.bark);

// function() {
//    console.log("Woof!");
// }
```

Because the `bark` property is a function, we can call it like any other function:

```js
dog.bark();
// Woof!
```

> We didn't use a console log there, we just called the function and the console log happened inside the function.

These object functions are called `methods`.

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


### document

`document` is the parent object in the `DOM`. Everything in the DOM is a property of `document`.

On any web page, enter the following in the console:

```js
console.dir(document);
// #document (and a clickable list of its properties) is logged
```

`document` contains all the nodes (HTML elements) in the DOM and also all the methods (functions) the browser and developers can use to manipulate those elements.

> Chrome dev tools uses `f` as a shorthand for function

```js
console.log(document.querySelector);
//f querySelector() {  }

console.log(document.querySelectorAll);
//ƒ querySelector() { }
```

We will use the above two methods to select DOM elements in the [next lesson](2).

---

## Acivities

#### Read

[CSS Tricks: What is the DOM](https://css-tricks.com/dom/) 
(You can skip the Ajax and Templating section)

#### Watch

[LinkedIn Learning: JavaScript Essential Training](https://www.linkedin.com/learning/javascript-essential-training-3/)

Watch the following videos:

Section 5. JavaScript and the DOM, Part 1: Changing DOM Elements:

- DOM: The document object model

---
- [Go to lesson 2](2) 
---
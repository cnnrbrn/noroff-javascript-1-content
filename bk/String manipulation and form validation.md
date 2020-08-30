

The example page can be found <a href="https://js1-form-validation.netlify.com/" target="_blank">here</a>.

<iframe src="https://js1-form-validation.netlify.com/" style="height:400px"></iframe>

---

First we will look at two string manipulation methods.

We looked at the `replace()` method in [Lesson 3 of Module 3](../3/3).

We are going to look at two other methods here:

-   `length`
-   `trim`

### length

The `length` property can be used to find the number of characters - the length - of a string.

```js
const greeting = "Hello";
const lengthOfGreeting = greeting.length;
console.log(lengthOfGreeting);
// 5
```

An empty string returns a length of `0`:

```js
const emptyString = "";
console.log(emptyString.length);
// 0
```

Blank spaces are counted as part of the length of the string:

```js
const spaceTest = "a b";
console.log(spaceTest.length);
// 3

const blankSpace = " ";
console.log(blankSpace.length);
// 1
```

A common use for the `length` property is to check the length of the value a user types in to a text input.

Sometimes an input needs to have a minimum or maximum number of characters, or sometimes the input is simply required - it must have at least one character.

Let's select the `firstName` input below and log it's value using a `keyup` event.

Add the following input to an HTML page:

```html
<input type="text" id="firstName" />
```

Let's get the input by its `id`:

```js
const firstName = document.querySelector("#firstName");
```

Now we'll add `keyup` event listener and log the length of the value in the input:

```js
firstName.addEventListener("keyup", logLength);

function logLength(event) {
    const inputValue = event.target.value;
    const valueLength = inputValue.length;
    console.log(valueLength);

    // we could skip the variables and write it this way
    console.log(event.target.value.length);
}
```

If you run the code above the number of characters (the length) of what you type in the input will be logged. If you delete eveything in the input, `0` will be logged.

Let's change the code to log whether or not the input has a value. We can do this by checking if the length is greater than 0.

```js
firstName.addEventListener("keyup", checkLength);

function checkLength(event) {
    const inputValue = event.target.value;
    const valueLength = inputValue.length;

    if (valueLength > 0) {
        console.log("The input has a value");
    } else {
        console.log("The input does not have a value");
    }
}
```

If we wanted to check if a field was required - that it had a length greater than 0 - we could use something like the above code.

There is a problem though. If you typed only a space or spaces into the input, the code above would log that the input had a value, but empty spaces are not useful as user input in the real world.

We can use the `trim` method to remove spaces.

### trim

The `trim` method removes spaces from the beginning and end of a string, but doesn't remove spaces between words.

The string below has a space at the beginning and the end.

```js
const firstName = " Burt ";
```

If we log its value it will return `6`:

```js
console.log(firstName.length);
// 6
```

We can use the `trim` method to remove the spaces:

```js
const trimmedName = firstName.trim();
```

Now the `length` property will return `4`:

```js
console.log(trimmedName.length);
// 4
```

If we use trim on a string with more than one word, the spaces between words don't get removed:

```js
const sentence = "a dog ";
console.log(sentence.length);
// 6

const trimmedSentence = sentence.trim();
console.log(trimmedSentence.length);
// 5
```

If a string has only space in it, trim will ensure the length property returns `0`. This time we'll `chain` the `length` property on to the `trim` method without assigning the trimmed value to a variable first:

```js
const space = " ";
console.log(space.length);
// 1

console.log(space.trim().length);
// 0
```

Let's update the `checkLength` function to use `trim`:

```js
const firstName = document.querySelector("#firstName");

firstName.addEventListener("keyup", checkLength);

function checkLength(event) {
    const inputValue = event.target.value.trim();
    const valueLength = inputValue.length;

    if (valueLength > 0) {
        console.log("The input has a value");
    } else {
        console.log("The input does not have a value");
    }
}
```

Now values with only spaces won't pass the length test.

---

Clone the [repo](https://github.com/javascript-repositories/form-validation) to add the code below.

---

We'll add the code in `js/contact.js`.

First we'll select the form:

```js
const form = document.querySelector("#contactForm");
```

The event we want to listen for is the `submit` event. We'll pass in a function called `validateForm` when the submit event happens.

```js
form.addEventListener("submit", validateForm);
```

Let's write `validateForm` function.

```js
function validateForm(event) {
    console.log("The form was submitted");
}
```

If you add code above and then click the submit button, the console message will briefly appear but because, by default, when a form is submitted the page gets reloaded, the message will disapear as the page refreshes.

After the form is submitted you'll see parameters have been added to the query string:

```js
http://127.0.0.1:5502/contact.html?firstName=&email=
```

This is how forms submit their input values when they don't have a `method` attribute set - they use the default method which is the `GET` method. Using this method all the input names and values get added to the querystring.

If we add a `method` attribute to the form and give it a value of `POST`, the values won't be added to the query string and forms are usually submitted using the `POST` method.

We won't be submitting any values to a server, but need to prevent the browser's default behaviour of reloading the page when a form gets submitted. Otherwise none of the JavaScript we write will run as the page will simply refresh.

We can do that using the `event.preventDefault` method:

```js
function validateForm(event) {
    event.preventDefault();
    console.log("The form was submitted");
}
```

Now when we click submit button the form is not submitted, the page doesn't reload and the message in the console remains there.

Now we can write the validation code.

When the submit button is clicked, we want to check if both `firstName` and `email` have a value. If not, we want to display the error message below the relevant input.

The code to check whether an input has a value will apply to any input that needs this validation, so let's write a function we can reuse:

```js
function checkInputLength(value) {
    // trim the value
    const trimmedValue = value.trim();

    // if the value's length is greater than 0 return true
    if (trimmedValue.length > 0) {
        return true;
    } else {
        return false;
    }
}
```

The function will return `true` if the value passed in has a length greater than 0, otherwise it will return `false`.

Inside the `validateForm` function we'll first select the `firstName` input and the `firstNameError` div and then pass the input's value to the `checkInputLength` function. If the input has value the error message will be hidden, otherwise it will be displayed:

```js
const firstName = document.querySelector("#firstName");
const firstNameError = document.querySelector("#firstNameError");
const firstNameValue = firstName.value;

if (checkInputLength(firstNameValue) === true) {
    firstNameError.style.display = "none";
} else {
    firstNameError.style.display = "block";
}
```

The code in `js/contact.js` so far:

```js
const form = document.querySelector("#contactForm");

form.addEventListener("submit", validateForm);

function validateForm(event) {
    event.preventDefault();
    console.log("The form was submitted");

    const firstName = document.querySelector("#firstName");
    const firstNameError = document.querySelector("#firstNameError");
    const firstNameValue = firstName.value;

    if (checkInputLength(firstNameValue) === true) {
        firstNameError.style.display = "none";
    } else {
        firstNameError.style.display = "block";
    }
}

function checkInputLength(value) {
    // trim the value
    const trimmedValue = value.trim();

    // if the value's length is greater than 0 return true
    if (trimmedValue.length > 0) {
        return true;
    } else {
        return false;
    }
}
```

Test the form and you'll see that validation for the `firstName` field is working.

Because we are setting the error message's display property every time the submit button is clicked, if validation for the input failed and the error message was displayed, the message will be hidden again whenever validation passes.

Let's add the same validation to the `email` input. We can remove the `=== true` in the if statement.

```js
const email = document.querySelector("#email");
const emailError = document.querySelector("#emailError");
const emailValue = email.value;

if (checkInputLength(emailValue)) {
    emailError.style.display = "none";
} else {
    emailError.style.display = "block";
}
```

Now the validation code will check if both the `firstName` and `email` fields contain a value, but the code is not validating where the email address is valid.

Let's create another function to validate the email.

We said in Lesson 3 of Module 3 that `regular expressions` - or `regex` - are used to match patterns. We will use a regular expression in the `validateEmail` function to check if the value of the input matches a certain pattern.

First we create the expression between two forward slashes `/` `/`.

Then the `test` method checks if a value matches a pattern - it returns true or false. We'll return this value.

```js
function validateEmail(email) {
    const regEx = /\S+@\S+\.\S+/;
    const patternMatches = regEx.test(email);
    return patternMatches;
}
```

We could return the `test` method value directly:

```js
function validateEmail(email) {
    const regEx = /\S+@\S+\.\S+/;
    return regEx.test(email);
}
```

Let's add a check using the `validateEmail` below the other code that checks if the email input has a value.

First we need to select a different div to display this particular error:

```js
const invalidEmailError = document.querySelector("#invalidEmailError");
```

Now we can add the `if` statement that will hide or show the error depending on if it passes the `regex` test in the `validateEmail` function:

```js
if (validateEmail(emailValue) === true) {
    invalidEmailError.style.display = "none";
} else {
    invalidEmailError.style.display = "block";
}
```

This is now the email validation code:

```js
const email = document.querySelector("#email");
const emailError = document.querySelector("#emailError");
const invalidEmailError = document.querySelector("#invalidEmailError");

const emailValue = email.value;

if (checkInputLength(emailValue) === true) {
    emailError.style.display = "none";
} else {
    emailError.style.display = "block";
}

if (validateEmail(emailValue) === true) {
    invalidEmailError.style.display = "none";
} else {
    invalidEmailError.style.display = "block";
}
```

---

The code added in this lesson can be found in the <a href="https://github.com/javascript-repositories/form-validation/blob/step-1/js/contact.js" target="_blank">step-1</a> branch of the repo.

---
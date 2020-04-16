# Lesson 2 - Display an array of results after an API call

This is a short lesson on fetching an array of results from an API and creating HTML from the returned data.

In this lesson we will create the page below, a loop through an array of results from calling an elephant API.

The example page can be found <a href="https://api-calls.netlify.com/" target="_blank">here</a>.

<iframe src="https://api-calls.netlify.com/" style="height:400px"></iframe>

In the next lesson we will write the details page.

Clone the [repo](https://github.com/javascript-repositories/javascript-1-api-calls) to follow along.

The first branch is called `step-0`.

---

We will add the code below to the `js/index.js` file.

First we need to add the CORS fix to the URL we want to use:

```js
const elephantUrl = "https://elephant-api.herokuapp.com/elephants";
const corsEnabledUrl = "https://noroffcors.herokuapp.com/" + elephantUrl;
```

We are going to use the `async/await` way of calling an API.

```js
// the function must be marked as async
async function fetchElephants() {
    try {
        // use await when calling fetch
        const response = await fetch(corsEnabledUrl);
        // use await when resolving the returned value, which is a promise
        const elephants = await response.json();
        // pass the array of elephants to the displayElephants function
        displayElephants(elephants);
    } catch (error) {
        console.log(error);
    }
}

// call the fetchElephants function
fetchElephants();
```

Once the API call is complete, we call the `displayElephants` function and passing in the result of the call, which we are storing in the variable called `elephants`.

We need to create the `displayElephants` function.

First thing to do is always to inspect the result of an API call by logging it.

```js
function displayElephants(elephants) {
    console.log(elephants);
}
```

> You always need to inspect the data from an API call to see what you need to retrieve from it. All REST APIs will return JSON, but they will return it differently with different properties.

These are the properties each elephant object has that we can use when creating HTML.

<img src="/images/js1/elephant-api-properties.png" alt="Elephant API properties" style="max-width:800px">

Here is the rest of the code for the `displayElephants` function with comments for each part.

```js
function displayElephants(elephants) {
    console.log(elephants);
    // select the element where we will attach the HTML we create
    const elephantContainer = document.querySelector(".elephant-container");

    // declare a vairable to hold the HTML we will create
    let html = "";

    // loop through each using a for loop
    for (let i = 0; i < elephants.length; i++) {
        //some of the result objects have only id properties, nothing else
        // check if the object has a name property,
        // if it doesn't, skip the rest of the code in this iteration of the loop and go to the next object
        if (!elephants[i].name) {
            // continue will skip the remaining code and return to the top of the loop
            continue;
        }

        // the elephants[i].dod property is the date of death of the elephant, but some elephants don't have a proper value
        // for some the value is -
        console.log(elephants[i].dod);

        // create a default value for dateOfBirth
        // this variable will be used when creating the html, not elephants[i].dod
        let dateOfDeath = "Unkown";

        // if the elephant has a proper date of death value (not -), assign it to the dateOfDeath variable
        if (elephants[i].dod !== "-") {
            dateOfDeath = elephants[i].dod;
        }

        // add the new HTML string to the existing HTML string
        html += `<div>
                    <div class="image" style="background-image: url(${elephants[i].image});"></div>
                    <h3>${elephants[i].name}</h3>
                    <p>Date of birth: ${elephants[i].dob}</p>                    
                    <p>Date of death: ${dateOfDeath}</p>
                    <a href="detail.html?name=${elephants[i].name}">Details</a>
                </div>`;
    }

    // assign the new HTML string to the innerHTML or elephantContainer
    elephantContainer.innerHTML = html;
}
```

> Refer to [Programing Foundations Module 2 Lesson 3](https://interactive-content.now.sh/programming-foundations/2/3) for info on looping through arrays of objects using `for loops`

### Default values for properties

The `dod` property on each elephant object is the elephant's date of death. Sometimes it only has a value of "-". We want to display something better than that for the user.

In the code above we declare a variable called `dateOfDeath` and give it an initial value of "Unkown".

```js
let dateOfDeath = "Unkown";
```

Then we ckeck if the `dod` property is not equal to "-". If it isn't, we assign its value to `dateOfDeath`.

```js
if (elephants[i].dod !== "-") {
    dateOfDeath = elephants[i].dod;
}
```

We then use `dateOfDeath` inside the HTML instead of `elephants[i].dod`.

```js
<p>Date of death: ${dateOfDeath}</p>
```

### Continue

We can use the `continue` keyword to skip executing the code that follows it inside a for loop.

Several of the objects in the array of results don't have properties apart from an id. We don't want to create HTML for those objects.

In the code above we check if the object has a `name` property and if it doesn't we'll skip the rest of the code in the block.

```js
if (!elephants[i].name) {
    // continue will skip the remaining code
    continue;
}
```

This will return execution of the code back to the top of the for loop without calling any code that follows the `continue` keyword.

---

In the HTML we create in the loop, we are adding the `name` property as a paramater to a link to the `detail.html` page.

```html
<a href="detail.html?name=${elephants[i].name}">Details</a>
```

In the next lesson we will retrieve the name parameter from the url and use it in an API call to fetch a single elephant's details.

---

The code added in this lesson can be foudn in the <a href="https://github.com/javascript-repositories/javascript-1-api-calls/blob/step-1/js/index.js" target="_blank">step-1</a> branch of the repo.

---

[Go to lesson 3](3)

---

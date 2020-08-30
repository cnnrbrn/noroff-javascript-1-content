# Lesson 3

In this lesson we will take a look at:

- retrieving parameters from the querystring
- passing variables to other pages in the querystring 

## Retrieving parameters from the querystring

One way to pass variables across pages is the querystring, which is the part of the URL after the `?`.

In this video we will look at how we can retrieve paramater values (essentially variables) from the querystring using code similar to the below:


```js
// get the querystring
const queryString = document.location.search;

// create an object that will allows us to access all the querystring parameters
const params = new URLSearchParams(queryString);

// get the id parameter from the querystring
const id = params.get("id");
```

<iframe src="https://player.vimeo.com/video/453021027" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/453021027/cc9e8cce3f" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/retrieving-parameters-from-querystrings" target="_blank">Code from the video</a>

---

## Passing variables to other pages in the querystring 

In this video we will add a variable to the href value in an `<a>` tag, retrieve it from the querystring on a separate page and then use its value in an API call.

<iframe src="https://player.vimeo.com/video/453080750" width="640" height="400" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

<a href="https://vimeo.com/453080750/328b6f90fd" target="_blank">Direct link</a>

<a href="https://github.com/NoroffFEU/passing-variables-to-other-pages-in-the-querystring" target="_blank">Code from the video</a>



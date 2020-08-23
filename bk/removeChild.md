
### removeChild

We need to remove the loader from the page once the API call has finished.

The container div contains the `Back to games` link as well as the loader. If we set its innerHTML property to an empty string

```js
innerHTML = "";
```

the link would disapper too, not just the loader.

We an use the `removeChild` method to remove only the loader from the DOM.

First we'll select the container and the loader:

```js
const container = document.querySelector(".container");
const loader = document.querySelector(".loader");
```

Now we'll call `removeChild` on `container` and pass in `loader` as the element to remove:

```js
container.removeChild(loader);
```

The loader will now be gone.

Full function code so far:

```js
function createDetails(details) {
    console.dir(details);

    const container = document.querySelector(".container");
    const loader = document.querySelector(".loader");
    container.removeChild(loader);
}
```
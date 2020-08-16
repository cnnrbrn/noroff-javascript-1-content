## forEach

So far we've used `for loops` to loop (iterate) over arrays.

We can also use the `forEach` method. We'll see how it works using the array below.

```js
const cats = ["Blob", "Harold", "Slim"];
```

This is how the code would look using a `for loop`:

```js
for (let i = 0; i < cats.length; i++) {
    console.log(cats[i]);
}
```

This is what it would look like using a `forEach`:

```js
cats.forEach(function (cat) {
    console.log(cat);
});
```

The `forEeach` method takes a callback function as an argument. The function runs on every item in the array.

We could define the function first and then pass it in:

```js
function handleEachCat(cat) {
    console.log(cat);
}

cats.forEach(handleEachCat);
```

The callback function receives each item in the array as an argument. We've called this argument `cat` because the array is called `cats` but it can be called anything:

```js
function handleEachCat(item) {
    console.log(item);
}
```

The item argument is how we get access to each item in the array, and is equivalent to the `cats[i]` part in the `for loop` code.

If you run the `for loop` code and then the `forEach` version, you will see they both log each item in the array.

```js
Blob;
Harold;
Slim;
```

Let's look at an example that uses `forEach` on an array of objects:

```js
const cats = [
    {
        name: "Blob",
        age: 10
    },
    {
        name: "Harold",
        age: 7
    },
    {
        name: "Slim",
        age: 21
    }
];

function handleEachCat(item) {
    console.log(item.name, item.age);
}

cats.forEach(handleEachCat);
```

The above code logs the name and age of each cat item in the array.

Let's rewrite the `makeGenres` function from Module 1, Lesson 4 to use a `forEach`. We'll pass the function directly into the method without declaring it first. `genre` is a good name for the argument.

```js
function makeGenres(genreArray) {
    let genreHTML = "";

    genreArray.forEach(function (genre) {
        genreHTML += `<a class="genre">${genre.name}</a>`;
    });

    return genreHTML;
}
```

You can access the item's index by passing in a second argument to the callback function. Remember, an array's index begins at 0.

```js
function handleEachCat(item, index) {
    console.log("name: " + item.name + " index: " + index);
}
```

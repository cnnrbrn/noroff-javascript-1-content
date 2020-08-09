## Data types and truthy and falsy values

In Programming Foundations, we looked at five different data types in JavaScipt:

-   `string`
-   `number`
-   `boolean`
-   `undefined`
-   `null`

We also looked at `objects`, `arrays` and `functions`.

The first five (together with `bigInt` and `symbol` - neither of which we will use in this course) are considered `primitive` types, they are built-in to the language.

All other values are built from objects, including arrays and functions.

> An unhelpful "feature" in JS: If you use the `typeof` operator on an array, it will return `object`. If you use typeof on a function, it will return `function`.

Each value also has a `boolean` value associated with it, known as `truthy` or `falsy`.

The following values are `falsy`:

-   0 (zero)
-   false
-   "", '' or `` - empty strings
-   null
-   undefined
-   Nan - `N`ot `a` `N`umber

Every other value is `truthy`.

If we are trying to check if a value exists, if it isn't `null` or `undefined`, for example, we can do this:

```js
if (someVariable) {
    console.log("someVariable exists");
}
```

rather than having to check for both `null` and `undefined` like this:

```js
if (someValue !== null && someValue !== undefined) {
    console.log("someValue exists");
}
```

That applies to all the falsy values, so we can check that a variable's value is not one of the `falsy` values by writing an `if statement` like the one above and below:

```js
if (someVariable) {
    // someVariable exists, do something with it
}
```

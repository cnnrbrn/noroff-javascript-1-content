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

-   false
-   0 - the number zero
-   "", '' or `` - empty strings
-   null
-   undefined
-   Nan - `N`ot `a` `N`umber

Every other value is `truthy`.

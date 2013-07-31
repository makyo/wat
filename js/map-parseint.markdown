This came up as a little thought exercise as to just what exactly is going on.

```javascript
console.log( ['10', '10', '10', '10'].map(parseInt) );

// >>> [10, NaN, 2, 3]
```

So what's going on here?

Well, it turns out, two things working together.

1. `map` passes three arguments to the function passed to it.

   **value** - the value of the current item.

   **index** - the index of the current item.

   **array** - the entire array being iterated over.
2. `parseInt` can use two arguments.  It doesn't really *take* any arguments
because it just uses (for the sake of example; it's a native function) the
`arguments` array and uses the first two items.  The second argument to parseInt
is the radix, or base to use when parsing an integer.

This means that parseInt is technically using the index that map is passing it,
and the following is what is going on:

```javascript
console.log( parseInt('10', 0) ); // 0 is falsey, default to base 10

// >>> 10

console.log( parseInt('10', 1) ); // 1 is not a valid radix

// >>> NaN

console.log( parseInt('10', 2) ); // 10 in binary

// >>> 2

console.log( parseInt('10', 2) ); // 10 in ternary

// >>> 3
```

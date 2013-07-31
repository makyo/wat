Something seemed a little different about arrays created through the `new Array`
constructor.

```javascript
var x = new Array(3);
console.log(x, x.length);

// >>> [undefined, undefined, undefined] 3

var y = [undefined, undefined, undefined]
console.log(y, y.length);

// >>> [undefined, undefined, undefined] 3

// Swapping order for drama...
console.log( y.map(function(a) { return 0; }) );

// >>> [0, 0, 0]

console.log( x.map(function(a) { return 0; }) );

// >>> [undefined, undefined, undefined]
```

What's happening is that the `new Array` constructor creates an empty array with
three **undefined** pointers, where as initializing an array with three
undefined elements creates an empty array with three pointers to **undefined**
elements.

[ref](http://stackoverflow.com/questions/5501581/javascript-new-arrayn-and-array-prototype-map-weirdness)

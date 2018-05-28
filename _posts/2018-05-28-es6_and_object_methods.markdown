---
layout: post
title:      "ES6 and Object Methods"
date:       2018-05-28 17:35:52 -0400
permalink:  es6_and_object_methods
---


Variables defined using `const` cannot be modified or redclared. 

However, when `const` is an object, its properties CAN be modified:
```javascript
// declare the constant
const x = {
 key1: "value1"
}

x 
//=> {key1: "value1"}

// assign a new value to the object property
x.key1 = "value2"

// object property changes
x 
//=> {key1: "value2"}
```

If you want to prevent this, you can use `Object.freeze()` and `Object.seal()`

**`Object.freeze()`: Existing properties cannot be modified or removed, and new properties cannot be added.**

```javascript
// declare the constant
const y = {
 key1: "value1"
}

// freeze the object
const frozenY = Object.freeze(y)

frozenY 
//=> {key1: "value1"}

// attempt to assign a new value to the object property
frozenY.key1 = "value2"

// object property doesn't change
frozenY 
//=> {key1: "value1"}

// attempt to assign a new value to the original (frozen object) property
y.key1 = "value2"

// object property doesn't change
y 
//=> {key1: "value1"}

// attempt to add a new property to the original (frozen object)
y.key2 = "value2"

// object property isn't added
y 
//=> {key1: "value1"}
```

**`Object.seal()`: Existing properties can be modified but not removed, and new properties cannot be added.**

```javascript
// declare the constant
const z = {
 key1: "value1"
}

// seal the object
const sealedZ = Object.seal(z)

sealedZ
//=> {key1: "value1"}

// assign a new value to the object property
sealedZ.key1 = "value2"

// object property changes
sealedZ
//=> {key1: "value2"}

// attempt to add a new property to the sealed object
sealedZ.key2 = "value3"

// object property isn't added
sealedZ
//=> {key1: "value2"}
```


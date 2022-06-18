<div id="top" align="center">

<h1><a href="https://github.com/ThePywon/locked-array">locked-array</a></h1>
 
[![npm version](https://img.shields.io/npm/v/@protagonists/locked-array)](https://npmjs.com/package/@protagonists/locked-array)
[![npm downloads](https://img.shields.io/npm/dt/@protagonists/locked-array)](https://npmjs.com/package/@protagonists/locked-array)
[![discord server](https://img.shields.io/discord/937758194736955443?logo=discord&logoColor=white)](https://discord.gg/cwhj3EgqGP)
[![last commit](https://img.shields.io/github/last-commit/ThePywon/locked-array)](https://github.com/ThePywon/locked-array)
 
</div>



# About

An array that can be completely locked from adding/removing elements on demand

---

<br/><br/><br/>

# Table of content

* [**LockedArray**](#lockedarray)

* <details open><summary><a href="#properties"><b>Properties</b></a></summary>
  <p>
  
  * [**`.key`**](#key) &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)
  * [**`.locked`**](#locked) &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)
  * [**`.value`**](#value) &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)
    
  </p>
</details>

* <details open><summary><a href="#methods"><b>Methods</b></a></summary>
  <p>
  
  * [**`.lock`**](#lock)
  * [**`.unlock`**](#unlock)
  * [**`.add`**](#add)
  * [**`.remove`**](#remove)
  * [**`.includes`**](#includes)
  * [**`.find`**](#find)
  * [**`.findOne`**](#findOne)
  * [**`.valueOf`**](#valueof) &nbsp; [![Prototype](https://shields.io/badge/-Prototype-orange)](https://javascript.info/prototype-inheritance)
  * [**`.toString`**](#tostring) &nbsp; [![Prototype](https://shields.io/badge/-Prototype-orange)](https://javascript.info/prototype-inheritance)
    
  </p>
</details>

---

<br/><br/><br/>



# LockedArray

The constructor function for locked arrays!

<br/>

**Syntax:** &nbsp; `new LockedArray()`

> The lack of the `new` keyword may cause unwanted behaviour

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("protagonists/locked-array");
// Create new LockedArray instance
const names = new LockedArray(["John", "Steve", "Carl", "Maria"]);

// Get the array's key
const key = names.key;

// Create a function to add an element to the list using the key
function addName(name) {
  if(typeof name === "string") {
    names.unlock(key);
    names.add(name);
    names.lock();
  }
}

// Log the array's value
console.log(names.value);
// try to add element to the direct value
names.value.push("Meep");
// Log the array's value
console.log(names.value);
// Add an element using the function which utilises the key
addName("Meep");
// Log the array's value
console.log(names.value);
```

**Output:**

```
[ 'John', 'Steve', 'Carl', 'Maria' ]
[ 'John', 'Steve', 'Carl', 'Maria' ]
[ 'John', 'Steve', 'Carl', 'Maria', 'Meep' ]
```

---

<br/><br/><br/>

# Properties

A few readonly properties from the locked array object

<br/>

<a id="key"></a>

## `.key` &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)

A getter that returns the key to the locked array (if unlocked), then locks the array  
If checked while the array is locked, returns `undefined`

<br/>

**Type:** &nbsp; [**Symbol**](https://javascript.info/symbol)

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create new LockedArray instance
const myArr = new LockedArray();

// Log array's lock state
console.log(myArr.locked);

// Get the array's key
const key = myArr.key;

// Log the key
console.log(key);
// Log array's lock state
console.log(myArr.locked);

// Unlock the array with the key
myArr.unlock(key);

// Log array's lock state
console.log(myArr.locked);
```

**Output:**

```
false
Symbol(key)
true
false
```

<br/><br/>

<a id="locked"></a>

## `.locked` &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)

A getter that returns the locked state of the locked array object

<br/>

**Type:** &nbsp; [**Boolean**](https://javascript.info/types#boolean-logical-type)

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create new LockedArray instance
const myArr = new LockedArray();

// Log array's lock state
console.log(myArr.locked);

// Get array's key
const key = myArr.key;
// Log array's lock state
console.log(myArr.locked);

// Unlock the array with the key
myArr.unlock(key);
// Log array's lock state
console.log(myArr.locked);

// Lock the array
myArr.lock();
// Log array's lock state
console.log(myArr.locked);
```

**Output:**

```
false
true
false
true
```

<br/><br/>

<a id="value"></a>

## `.value` &nbsp; ![Read Only](https://shields.io/badge/-Read%20Only-green)

A getter that returns the array's value

<br/>

**Type:** &nbsp; [**Array**](https://javascript.info/array)

<br/>

### **Example**

**Code:**

```js
const LockedArray = require("@protagonists/locked-array");
const myArr = new LockedArray([1, 2, 3, 5, 4]);

console.log(myArr.value);
```

**Output:**

```
[ 1, 2, 3, 5, 4 ]
```

---



<br/><br/><br/>

# Methods

Some methods to interact with the array or find specific elements within it

<br/>

## `.lock`

Locks the array from any further modification

<br/>

**Syntax:** &nbsp; `lock()`

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["Apple", "Orange"]);

// Add "tomato" in the array
fruits.add("Tomato");
// Lock the array
fruits.lock();

// Log the array's value
console.log(fruits.value);
// try to add element to the direct value
fruits.value.push("Banana");
// Log the array's value
console.log(fruits.value);
```

**Output:**

```
["apple", "orange", "tomato"]
["apple", "orange", "tomato"]
```


<br/><br/>


## `.unlock`

Unlocks the array using the corresponding key, allowing it to be modified once again

<br/>

**Syntax:** &nbsp; `unlock(key)`

|**Parameters**|**Types**|
|-|-|
|`key`|[**Symbol**](https://javascript.info/symbol)|

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["apple", "orange"]);

// Add "tomato" in the array
fruits.add("tomato");
// Lock the array and get the key
const key = fruits.key;

// Log the array's value
console.log(fruits.value);

// try to add element to the direct value
fruits.value.push("banana");
// Log the array's value
console.log(fruits.value);

// Unlock the array
fruits.unlock(key);

// Add "banana" to the array
fruits.add("banana");
// Log the array's value
console.log(fruits.value);
```

**Output:**

```
[ 'apple', 'orange', 'tomato' ]
[ 'apple', 'orange', 'tomato' ]
[ 'apple', 'orange', 'tomato', 'banana' ]
```


<br/><br/>


## `.add`

Pushes a new element on the bottom of the array

<br/>

**Syntax:** &nbsp; `add(element)`

|**Parameters**|**Types**|
|-|-|
|`element`|**Any**|

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["apple", "orange"]);

// Log array's value
console.log(fruits.value);

// Add "tomato" into the array
fruits.add("tomato");

// Log array's value
console.log(fruits.value);
```

**Output:**

```
[ 'apple', 'orange' ]
[ 'apple', 'orange', 'tomato']
```


<br/><br/>


## `.remove`

Removes the first instance of an element from the array

<br/>

**Syntax:** &nbsp; `remove(element)`

|**Parameters**|**Types**|
|-|-|
|`element`|**Any**|

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["apple", "orange", "banana"]);

// Log array's value
console.log(fruits.value);

// Remove "banana" from the array
fruits.remove("banana");

// Log array's value
console.log(fruits.value);
```

**Output:**

```
[ 'apple', 'orange', 'banana' ]
[ 'apple', 'orange' ]
```


<br/><br/>


## `.includes`

Checks if the array contains the specified element

<br/>

**Syntax:** &nbsp; `includes(element)`

|**Parameters**|**Types**|
|-|-|
|`element`|**Any**|

<br/>

**Returns:** &nbsp; [**Boolean**](https://javascript.info/types#boolean-logical-type)

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["apple", "orange", "banana"]);

// Check if array has "tomato"
console.log(fruits.includes("tomato"));

// Check if array has "banana"
console.log(fruits.includes("banana"));
```

**Output:**

```
false
true
```


<br/><br/>


## `.find`

Find all elements matching the given requirements

<br/>

**Syntax:** &nbsp; `includes(options)`

|**Parameters**|**Types**|
|-|-|
|`options`|[**Object**](https://javascript.info/object)|

<br/>

**Returns:** &nbsp; **Any**

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const workers = new LockedArray([{
  name: "John",
  age: 37
}, {
  name: "Steve",
  age: 34
}, {
  name: "Carl",
  age: 37
}, {
  name: "Maria",
  age: 38
}]);

// Log any element matching the name "Steve"
console.log(workers.find({ name: "Steve" }));
// Log any element matching the age 37
console.log(workers.find({ age: 37 }));
```

**Output:**

```
[ { name: 'Steve', age: 34 } ]
[ { name: 'John', age: 37 }, { name: 'Carl', age: 37 } ]
```


<br/><br/>


## `.findOne`

Find the first element matching the given requirements

<br/>

**Syntax:** &nbsp; `includes(options)`

|**Parameters**|**Types**|
|-|-|
|`options`|[**Object**](https://javascript.info/object)|

<br/>

**Returns:** &nbsp; **Any**

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const workers = new LockedArray([{
  name: "John",
  age: 37
}, {
  name: "Steve",
  age: 34
}, {
  name: "Carl",
  age: 37
}, {
  name: "Maria",
  age: 38
}]);

// Log the first element matching the name "Steve"
console.log(workers.findOne({ name: "Steve" }));
// Log the first element matching the age 37
console.log(workers.findOne({ age: 37 }));
```

**Output:**

```
{ name: 'Steve', age: 34 }
{ name: 'John', age: 37 }
```


<br/><br/>


<a id="valueof"></a>

## `.valueOf` &nbsp; [![Prototype](https://shields.io/badge/-Prototype-orange)](https://javascript.info/prototype-inheritance)

This method returns the array's value

<br/>

**Syntax:** &nbsp; `valueOf()`

<br/>

**Returns:** &nbsp; [**Array**](https://javascript.info/array)

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create new LockedArray instance
const myArr = new LockedArray([1, 2, 3, 5, 4]);

// Log the array's toString() result
console.log(myArr.valueOf());
```

**Output:**

```
[ 1, 2, 3, 5, 4 ]
```


<br/><br/>


<a id="tostring"></a>

## `.toString` &nbsp; [![Prototype](https://shields.io/badge/-Prototype-orange)](https://javascript.info/prototype-inheritance)

This method returns a stringified version of the locked array object

<br/>

**Syntax:** &nbsp; `toString()`

<br/>

**Returns:** &nbsp; [**String**](https://javascript.info/string)

<br/>

### **Example**

**Code:**

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create new LockedArray instance
const myArr = new LockedArray();

// Log the array's toString() result
console.log(myArr.toString());
```

**Output:**

```
[object LockedArray]
```

---



<br/><br/><br/><br/><br/>

<h1 align="center">This is the bottom, there is nothing more.<br/>
Go <a href="#top">back up?</a></h1>

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

* [**How to use?**](#how-to-use)

* [**LockedArray**](https://github.com/ThePywon/locked-array/blob/main/documentation/LockedArray.md) &nbsp; ![Exported](https://img.shields.io/badge/-Exported-cyan)

---

<br/><br/><br/>



# How to use?

## Description

This is a simple array package that can prevent users from modifying the array itself  
Elements within it can still be modified and accessed as normal

## Import

### Terminal

> ```sh
> npm install @protagonists/locked-array
> ```

### Node.js

> ```js
> const LockedArray = require("@protagonists/locked-array");
> ```

---



<br/>

## Example

### Code:

```js
// Imports
const LockedArray = require("@protagonists/locked-array");
// Create LockedArray instance
const fruits = new LockedArray(["apple", "orange"]);

// Add "tomato" in the array
fruits.add("tomato");
// Lock the array
fruits.lock();

// Log the array's value
console.log(fruits.value);
// try to add element to the direct value
fruits.value.push("banana");
// Log the array's value
console.log(fruits.value);
```

<br/>

### Output:

```
[ 'apple', 'orange', 'tomato' ]
[ 'apple', 'orange', 'tomato' ]
```

<br/><br/><br/><br/><br/>

<h1 align="center">This is the bottom, there is nothing more.<br/>
Go <a href="#top">back up?</a></h1>

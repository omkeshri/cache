# Overview

Node Js is a JavaScript runtime built on Chrome's V8 JavaScript Engine.

> `globalThis` keyword can be used to access the global object in both browser and node.<br>
> __In browser:__ `this`, `global`, `self`, `frame`.. can also be used.<br>
> __In NodeJs:__ `global` can also be used.

## require

`require` is a built-in function used to load modules, JSON, or local files. It's part of the CommonJS module system. When you use require(), Node.js loads the specified module and makes its exported functions, objects, or variables available in the current file.

```js
const express = require('express');
```

## Module Type

In Node.js, the `type` field in a package.json file determines how the JavaScript code is interpreted — whether it uses CommonJS or ES modules. The two primary module systems are:
1. __CommonJS (CJS)__ - The default system used by Node.js (`require` and `module.exports`) (no type)
2. __ES Modules (ESM)__ - The standard module system for JavaScript (`import` and `export`) (type: "module")

```js
// file1.js

// CJS
var x = "Hello World"

function calculateSum(a, b){
    const s = a + b;
    console.log(s);
}

module.exports = {
    x : x, // or just x
    calculateSum : calculateSum // or just calculateSum
}

// ESM
var x = "Hello World"

export function calculateSum(a, b){
    const s = a + b;
    console.log(s);
}

// file2.js

// CJS
const { x, calculateSum } = require("./file1.js");
calculateSum(3, 4);

// or

const obj = require("./sum.js")
obj.calculateSum(3, 4)
console.log(obj.x)

// ESM
import { calculateSum } from "./file1.js";
calculateSum(3, 4);
```

> `module.exports` is an empty object.


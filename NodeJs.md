# Overview

Node Js is a JavaScript runtime built on Chrome's V8 JavaScript Engine.

> `globalThis` keyword can be used to access the global object in both browser and node.<br>
> __In Browser:__ `this`, `global`, `self`, `frame`.. can also be used.<br>
> __In NodeJs:__ `global` can also be used.

---

## require

`require` is a built-in function used to load modules, JSON, or local files. It's part of the CommonJS module system. When you use require(), Node.js loads the specified module and makes its exported functions, objects, or variables available in the current file.

```js
const express = require('express');
```

---

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

```
    CJS(Common JS Module)               vs               ESM(Ecma Script Module)
1.  module.exports and require()                         import export
2. By default used in node js                            By default used in React, Angular
3. Older way                                             Newer way
4. Synchronous                                           Asynchronous
5. Non Strict Mode                                       Strict Mode
```

> `module.exports` is an empty object.

> Strict Mode doesn't allow errors to be ignored. For example, assigning a = 10 without declaring it using var, let, or const will throw an error in Strict Mode, whereas it would be allowed in non-strict mode, making a a global variable.

---

## Immediately Invoked Function Expression (IIFE)

```js
function() {
    // Code
}) ();
```
> When we use `require("/path")`, the entire module's code is enclosed within an Immediately Invoked Function Expression (IIFE).

---

## V8 Engine

### Types of Languages

```
Interpreted                        vs                Compiled
1. Line by Line Execution                            First Compilation then Execution (High Level Code -> Machine Code)
2. Fast Initial Execution                            Initially heavy but executed fast
3. Interpretter                                      Compiler
```

> Code -> Parsing -> Compilation + Interpretation -> Execution

The V8 Engine processes code in two steps. First, it performs tokenization (or lexical analysis), converting the code into tokens. Then, in the second step, it conducts syntax analysis (or parsing) to transform these tokens into an Abstract Syntax Tree (AST).

> Code that is repeatedly executed (eg:- function) is known as hot code.

```
// JUST IN TIME COMPILATION
      -----  
     | AST |
      -----  
        ↓
                               Hot Code           -----------------
                           --------------->      |Turbofan Compiler|
 --------------------         Optimization        -----------------
|Ignition Interpreter|
 --------------------                                      ↓
                            Deoptimization        ----------------------
                           <---------------      |Optimized Machine Code| // If there is any changes in the code it will deoptimize.
        ↓                                         ----------------------
    ---------                                      
   |Byte Code|
    ---------                                              
        ↓                                                  ↓
                               ---------                             
                              |Execution|
                               ---------
```

Garbage Collection is also part of the process.
- Orinoco
- Oil Pan
- Scavenger
- MCompact

---

## libuv Library

- libuv is a C library originally developed for Node.js to provide support for asynchronous I/O(non-blocking IO), handling things like files, network connections, and timers.
- It offers an event loop, asynchronous file and socket operations, timers, child processes, and other core I/O features essential for Node.js.
- Since it's in C, it provides a bridge that lets Node.js, written in JavaScript, manage low-level system interactions more efficiently.

  

### JavaScript Overview

**JavaScript** is a synchronous, single-threaded, and high-level language.

The shortest possible JavaScript program can consist of no code at all. Even an empty JavaScript file automatically has a global execution context, which can be accessed using the `window` or `this` keyword.

#### Execution Context:
When JavaScript code runs, an execution context is created, which consists of memory and code components.

- **Memory Creation:** Before code execution starts, memory is allocated in a key-value pair format, assigning memory to each variable and function.
  - Variables are initially stored with the value `"undefined"`, while functions are stored entirely in memory.
  
- **Code Execution:** As the code runs line by line, variable values are updated, and functions are executed as they are called. Each execution context has a stack (LIFO):
  - Function contexts (for each invoked function)
  - The global execution context.

#### Hoisting:
In JavaScript, variables or functions can be used before they are declared because memory is allocated for them during the initial phase of code execution.

#### Scope:
In JavaScript, every execution context has access to its own memory as well as the memory of its parent context, known as the **lexical environment**. The global execution context has no parent lexical environment.

---

### Types of Errors:
- **Reference Error**
- **Syntax Error**
- **Type Error**

#### Temporal Dead Zone (TDZ):
It refers to the period between when a variable is hoisted (allocated memory) and when it is initialized. During this period, the variable cannot be accessed, and attempting to use it results in a `ReferenceError`.

- Both `let` and `const` are hoisted (not in the global or local lexical environment but in the script) but remain in the **Temporal Dead Zone (TDZ)** until their initialization.
- Both `let` and `const` cannot be redeclared. If redeclared, a syntax error will be thrown.
- With `let`, a variable can be initialized later after its declaration, while `const` must be initialized at the time of declaration. If not, a `TypeError` will occur.

---

#### Block:
A block is a pair of curly braces `{}` that groups multiple statements together. Blocks are essential in control structures like loops, if statements, and function definitions.

> When a variable declared with `var` is redeclared inside a block, it changes the global value (known as **shadowing**). However, this does not happen with `let` and `const`, as they are hoisted into a different memory space specific to the block.

---

### Closures:
A **closure** is a function that "remembers" and has access to its lexical scope, even when the function is executed outside that scope. In other words, a closure allows a function to access variables from an outer function after the outer function has returned.

- A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).
- In JavaScript, closures are created every time a function is created, at function creation time.

#### Uses/Advantages of Closures:
- Data Hiding and Encapsulation
- Module Design Pattern
- Currying
- Functions like `once`
- Memoization
- Maintaining state in asynchronous operations
- `setTimeout` callbacks
- Iterators

#### Disadvantages:
- Overconsumption of memory
- Not garbage collected (JavaScript freezes and removes unused variable memory, but not in this case)
- May freeze the browser if not handled properly

---

### Loop Example (Issue with `var`):
The following loop won't work as intended because `var` is function-scoped, causing each iteration to share the same value of `i`, which will be `6` after the loop finishes:

```js
for (var i = 1; i <= 5; ++i) {
  setTimeout(function () {
    console.log(i);
  }, i * 1000);
}
```

To fix this, you can either use let, which is block-scoped, or create a function closure to capture the current value of i at each iteration.
```js
for (var i = 1; i<=5; ++i{
  setTimeOut(function () {
    console.log(i);
  }, i * 1000);
}

for (var i = 1; i<=5; ++i{
  function close(x){
    setTimeOut(function () {
      console.log(x);
    }, x * 1000);
  }
  close(i);
}
```

---

### Function

The difference in Function Statement and Function Expression is in hoisting.<br>
a(arguement);<br>
b(); Not possible since JS will treat it as a variable and assign undefined to it during memory creation.

#### Function Statement/Function Declaration:
```js
function a(parameter){
    console.log("a called")
  }
```

#### Function Expression
  ```js
  var b = function (){
    console.log("b called");
  }
```

#### Anonymous Function 
Function without a name<br>
Should be used in Function Expression not directly or will throw error
  ```js
function (){
    console.log("Anonymous Function");
}
```

#### Named Function Expression 
  ```js
  var b = function xyz(){     // Cannot access xyz outside
    console.log("b called");
  }
```

#### First Class Function/First Class Citizen:
Functions that can be treated like any other variable. This means that a function can be assigned to a variable, passed as an argument to other functions, and returned from other functions. This concept is key to functional programming.

##### 1. Assigned to Variables
 ```js
const greet = function() {
    console.log("Hello!");
};
```

##### 2. Passed as Arguments
 ```js
function executeFunction(func) {
    func(); // Calls the passed function
}

executeFunction(greet); // Outputs: Hello!

```

##### 3. Returned from Functions
 ```js
function createCounter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // Outputs: 1
console.log(counter()); // Outputs: 2

```

##### 4. Stored in Data Structures
 ```js
const functionArray = [greet, counter];
functionArray[0](); // Outputs: Hello!

```

##### 5. Anonymous Functions
 ```js
setTimeout(function() {
    console.log("Executed after 1 second");
}, 1000);

```

JavaScript is a synchronus, single-threaded language.

Execution Context: When JavaScript code runs, an execution context is created, which consists of memory and code components.

Memory Creation: Before the code execution starts, memory is allocated in a key-value pair format, assigning memory to each variable and function.
                 - Variables are initially stored with a value of "undefined", while functions are stored entirely in memory.

Code Execution: As the code runs line by line, variable values are updated, and functions are executed as they are called. Each execution context has a stack(LIFO):
                - Function contexts (for each invoked function)
                - The global execution context


Hoisting: In JavaScript, variables or functions can be used before they are declared because memory is allocated for them during the initial phase of code execution.

The shortest possible JavaScript program can consist of no code at all. Even an empty JavaScript file automatically has a global execution context,which can be accessed using the window or this keyword.

Scope: In JavaScript, every execution context has access to its own memory as well as the memory of its parent context. This is known as the lexical environment. The global execution context has no parent lexical environment.

Types of error:
  - Reference Error
  - Syntax Error
  - Type Error

Temporal Dead Zone (TDZ) = It refers to the period between when a variable is hoisted (allocated memory) and when it is initialized. During this period, the variable cannot be accessed, and attempting to use it results in a ReferenceError.

Both let and const are hoisted(not in gloabal or local lexical enviornment but script) but remain in the Temporal Dead Zone (TDZ) until their initialization.

Both let and const cannot be declared again, if declared it will throw a syntax error.

With let, a variable can be initialized at a later point after its declaration, while const must be initialized at the time of declaration, if not it will throw a type error.

Block: It is a pair of curly braces {} that groups multiple statements together. A block is typically used to structure code into sections, define the scope of variables, and organize logic. Blocks are essential in control structures like loops, if statements, and function definitions.

When a variable declared with var is redeclared inside a block, it changes the global value (a concept known as shadowing). However, this does not happen with let and const, as they are hoisted into a different memory space specific to the block in which they are declared.

Closure: It is a function that "remembers" and has access to its lexical scope, even when the function is executed outside that scope. In other words, a closure allows a function to access variables from an outer function after the outer function has returned.
        - A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical             environment). In other words, a closure gives a function access to its outer scope. In JavaScript, closures are created every            time a function is created, at function creation time.
        - Uses:
              - Module Design Pattern
              - Currying
              - Functions like once
              - Memoize
              - Maintaining state in async world
              - SetTimeouts
              - Iterators etc.


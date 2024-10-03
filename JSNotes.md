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

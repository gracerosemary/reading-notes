# The Call Stack

## [Call stack](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)  

- a mechanism to keep track of its place in a script
- calls multiple functions (functions being run and functions called within those functions)
- functions called are added to the call stack by the interpreter, which then starts carrying out the function
- called functions are added to the call stack further up and run when calls are reached
- once current function is finished, it's removed from the stack and resumes execution where it left off
- stack overflow error - occurs when stack takes up more space than assigned

```jsx
function greeting() {
   // [1] Some codes here
   sayHi();
   // [2] Some codes here
}
function sayHi() {
   return "Hi!";
}

// Invoke the `greeting` function
greeting();

// [3] Some codes here
```

1. `greeting()` is added to the call stack
    
    Call stack list: 
    - greeting
2. functions within `greeting()` are executed
3. `sayHi()` is added to the call stack
    
    Call stack list: 
    - sayHi
    - greeting
4. functions within `sayHi()` are executed
5. return execution to the line that invoked `sayHi()` and continue with the rest of the `greeting()`function execution
6. delete `sayHi()` function from call stack list
    
    Call stack list:
    - greeting
7. if everything inside `greeting()` function has been executed, then return to its invoking line to continue executing the rest of the code
8. delete `greeting()` function from call stack list
    
    Call stack list:
    - empty

> In summary, then, we start with an empty Call Stack. Whenever we invoke a function, it is automatically added to the Call Stack. Once the function has executed all of its code, it is automatically removed from the Call Stack. Ultimately, the Stack is empty again.

## [The JavaScript Call Stack - What It Is and Why It's Necessary](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)  

> The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.

- call stack is primarily used for function invocation (call)
- call stack is synchronous → function execution is done top to bottom, one at a time
- call stack is a data structure that uses LIFO to temporarily store and manage function invocation (call)
    - LIFO: last in, first out
    - last function getting pushed to the stack is the first to return

    ![call stack storage](https://cdn-media-1.freecodecamp.org/images/QgR2uIk7tW0YNz0Xm8g0jAPeRFI0e4sCejsv)  

    ### Temporarily Store

    function invoked (called) → function (&parameters) & variables are pushed into the call stack → forms a stack frame (memory location in the stack) → function returns → pops out of stack and memory is cleared

    ### Manage function invocation (call)

    - call stack records the position of each stack frame
    - knows what function should be executed next (order)
    - removes function after execution
    - synchronous → needs to follow an order

    ### Stack Overflow

    Occurs due to recursive functions (function that calls itself) with no exit point. Hosting environments have a max stack call it can hold before throwing a stack error. 

     - "Uncaught RangeError: Maximum call size exceeded"

    > In summary
    The key takeaways from the call stack are:
    1. It is single-threaded. Meaning it can only do one thing at a time.
    2. Code execution is synchronous.
    3. A function invocation creates a stack frame that occupies a temporary memory.
    4. It works as a LIFO — Last In, First Out data structure.

    ## [JavaScript error messages && debugging](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)  

    <img src="https://miro.medium.com/max/1000/1*nKJJY1hD3QmbyCNtaafANA.jpeg" alt="cool trees" width="200"/> 

    → [Click here for more photography by Yannick Pulver 😲](https://unsplash.com/@yanu)  

    ### Types of error messages

    - Reference errors:
        - when variables are not declared

            ```jsx
            console.log(foo) // Uncaught ReferenceError: foo is not defined
            ```

        - temporal dead zone (tdz)
            - using `const` and `let` → time spent between hoisting and being declared causes reference error

            ```jsx
            foo = 'Hello' // Uncaught ReferenceError: foo is not defined
            let foo
            ```

        - error is simply fixed by declaring the variable before any declaration

            ```jsx
            let foo;
            foo = 'Hello'
            ```

    - Syntax errors:
        - something can't be parsed in terms of syntax
            - trying to parse an invalid object using JSON.parse

            ```jsx
            JSON.parse( {'foo': 'bar'} ) // Uncaught SyntaxError: Unexpected token o in JSON at position 1

            // fix by making the object a JSON
            JSON.parse('{"foo":"bar"}')
            ```

    - Range errors:
        - giving objects invalid lengths

        ```jsx
        var foo= []
        foo.length = foo.length -1 // Uncaught RangeError: Invalid array length

        // arrays cannot have negative lengths
        ```

    - Type errors:
        - types are incompatible (trying to access a property in an undefined variable)

        ```jsx
        var foo = {}
        foo.bar // undefined
        foo.bar.baz // Uncaught TypeError: Cannot read property 'baz' of undefined
        ```

### Debugging

- `console.log()`is your ride or die 🖤
- make a breakpoint using a debugger statement on the corresponding code line
- conditional breakpoints → right-click a previous breakpoint → program stops at that point only if a condition is met

### Call stack

- available in the chrome developer tools [sources] tab
- use names for functions so that it's easier to debug referencing the call stack
- `console.trace()` is used to see the stack trace at any point in your code

### Handling errors

- light blue error → anything after that error will not be executed
- catch the errors to default back somewhere (ex: 404 page)
- try…catch

### You're a cool tool

🔧 [quokka](https://quokkajs.com/)  

🔨 [eslint](http://eslint.org/)  

🔩 [TypeScript](https://www.typescriptlang.org/)  

## [MDN Web Docs - JS Error Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors)  
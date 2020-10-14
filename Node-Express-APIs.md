# Reading: An Introduction to Node.js on [sitepoint.com](http://sitepoint.com/)

> Node.js is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

> Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

### Node Is Built on Google Chrome’s V8 JavaScript Engine

- V8 engine was designed with performance in mind and is responsible for compiling JS directly to native machine code that the computer can execute
- Node takes the V8 engine and enhances it with features such as file system API, HTTP library, and a number of operating system-related utility methods
- Node.js is a program that can be used to execute JS on computers → it's a JS runtime

### NPM - the JS Package Manager

- Comes bundled with Node and is used to install a package

### Working with the package.json File

- The `node_modules` folder is where npm saves any dependent libraries
    - Shouldn't be checked in to version control and can be recreated at any time by running `npm install` from within the project's root.

### What Is Node.js Used For?

Used to automate the process of developing a modern JS application by installing (via npm) and running (via Node). 

- Biggest use case → running JS on the server

### Site Point Articles:

- [A Beginner’s Guide to Webpack](https://www.sitepoint.com/webpack-beginner-guide/)
- [Up and Running with ESLint — the Pluggable JavaScript Linter](https://www.sitepoint.com/up-and-running-with-eslint-the-pluggable-javascript-linter/)
- [An Introduction to Gulp.js](https://www.sitepoint.com/introduction-gulp-js/)
- [Unit Test Your JavaScript Using Mocha and Chai](https://www.sitepoint.com/unit-test-javascript-mocha-chai/)

### The Node.js Execution Model

- Node.js is single-threaded and event-driven → everything that happens in Node is in reaction to an event
- Node's execution model causes the server very little overhead and is capable of handling a large number of simultaneous connections
- Traditional approach to scaling a Node app is to clone it and have the cloned instances shared the workload
- Also has a built-in module to help implement a cloning strategy on a single sever

![node.js execution model](https://uploads.sitepoint.com/wp-content/uploads/2012/10/1516152673node_event_loop.png)

### Suitable apps

- Apps that require real-time interaction or collaboration (ex. chat sites)
- Building APIs that handle a lot of requests that are I/O driven
- Sites involving data streaming

### Advantages of Node.js

- Speed and scalability
- 1 language use (easily share code between server / client)
- Speaks JSON
- Automation of repetitive or error prone tasks on the PC
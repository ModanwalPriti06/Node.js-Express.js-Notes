# Node.js - Notes

# CORS (Cross-Origin Resource Sharing)
- CORS errors occur when a web application running on one domain (origin) tries to fetch resources (API, fonts, scripts) from another domain without proper permissions.
### Solutions to Prevent CORS Issues
1. Enable CORS on the Server (Best Approach)
2. Modify Headers in the Backend
3. Use a Proxy (Frontend Side Fix)
4. Enable CORS in Browser (Temporary Fix for Testing)

### Best Practice
- ✅ Modify the backend to send proper CORS headers (recommended).
- ✅ Use a proxy if backend changes are not possible.
- ✅ Do not disable CORS security in production.

# What is NodeJs?

- Node.js is an open-source, cross-platform JavaScript runtime environment that allows developers to run JavaScript outside the browser, mainly on servers.
- NodeJs use V8 and V8 is JS engine build by google that run javascript in browser.
- Engine mean: Engine take js code and node use and its compile js code in machine code.
- V8 written in C++ language
- ✅ Built on Chrome’s V8 engine – Fast execution of JavaScript.
- ✅ Single-threaded, event-driven, and non-blocking – Handles multiple requests efficiently.
- ✅ Uses an asynchronous I/O model – Perfect for real-time applications like chat apps, APIs, and streaming services.
<img width="780" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/1eb1f606-7e41-4680-85bf-1604b939a18c" />

###  Why Use Node.js?
-  Scalable & lightweight – Ideal for microservices and APIs.
-  Fast performance – Uses the V8 engine for high-speed execution.
-  Non-blocking I/O – Handles thousands of concurrent connections.
-  Full-stack JavaScript – Use JavaScript on both frontend & backend.

### difference between Browser and Nodejs run time environment:
- Browser can access DOM operation but nodejs can't.
- Runs JavaScript in the browser for frontend applications. Nodejs Runs JavaScript on the server for backend applications.
- Browser : DOM, BOM, Web APIs (e.g., document, window, fetch). Nodejs: Built-in Module (http, os fs etc)
- BrowserL ❌ No direct access to files. Nodejs: ✅ Full access using the fs module.

### Window Vs Global Object
- The javascript global object for the browser is window and for the nodejs is global
- The window object contain the method and property available only inthe browser environment.

# Node.js Architecture (Single-threaded, Event Loop, Non-blocking I/O)

## Event loop
- The event loop in JavaScript is a mechanism that handles asynchronous operations. JavaScript is single-threaded, meaning it executes code sequentially in a single call stack.
- Everything in Javascript happened in execution context.
```
console.log("Start");
setTimeout(() => console.log("setTimeout"), 0);
setImmediate(() => console.log("setImmediate"));
process.nextTick(() => console.log("nextTick"));
console.log("End");   
```
output:
```
Start
nextTick
setImmediate
setTimeout
End
```
### process.nextTick() in Node.js
- process.nextTick() is a Node.js method that schedules a callback function to be executed immediately after the current operation completes, before the Event Loop continues to the next phase.
- process.nextTick() executes after the synchronous code, but before the Event Loop moves to the next phase.

### execution context
- A big box which divide in 2 category
1. Memory Component ( Variable environment) = all variable and function are store in key value pair.
2. Code Component (Thread of Execution) = Just like whole code executed in thread run **one line at the time** (means one time can run one line only) that's why js is synchronous single threaded code component. 

### How it works:
Check up whatsapp image - uploaded
- Call Stack: JavaScript executes synchronous code line by line, pushing and popping function calls from the stack. Every time bottom of the stack have Execution context, means whenever js program is run this callstack populate this global execution context (GEC).
- Call stack maintain the order of execution of execution context.
- Web APIs: Asynchronous tasks like setTimeout, fetch, or event listeners are handled by Web APIs.
- Callback Queue & Microtask Queue: Once asynchronous tasks are completed, their callbacks are placed in the queue.
- - Microtasks (Promises, process.nextTick in Node.js) are prioritized over macrotasks (setTimeout, setInterval).
-  Event Loop: It constantly checks if the call stack is empty and pushes queued callbacks for execution.

## Single-threaded
- A single-threaded system means that it uses only one thread to execute tasks at a time. A thread is the smallest unit of execution in a process, and in a single-threaded model, tasks are executed sequentially on a single main thread.
  
## Non-blocking I/O
- 

# Types of Modules in Node.js

| **Type** | **Description** | **Example** | 
| ------------ | ---------------| ------------ |
| Built-in Modules|	Pre-installed Node.js modules. |	fs, http, path, crypto |
| Local Modules	| Custom modules created in the project.	| require("./myModule") |
| Third-party Modules |	Installed using npm. | express, mongoose, cors |

# Difference Between CommonJS (require()) and ESM (import)

| **Feature** | **CommonJS (require)** | **ES Modules (import)** | 
| ------------ | ---------------| ------------ |
|  Default in Node.js | 	✅ Yes	| ❌ No (Needs "type": "module")| 
| Execution| 	Synchronous| 	Asynchronous| 
| Can Load Dynamically?| 	❌ No| 	✅ Yes (Using import())| 
| Usage	| Used in older projects	| Recommended for modern projects| 

# Dynamic Module Import (Lazy Loading)
- ES Modules allow lazy loading using import().

#### Summary of Module above:
- ✔ Built-in Modules → Use require("module").
- ✔ Custom Modules → Use require("./file") (CommonJS) or import (ESM).
- ✔ Third-Party Modules → Install via npm install module-name.
- ✔ Use import() for lazy loading in ES Modules.


# Non-Blocking I/O Vs Blocking I/O:
- Non-blocking means working with multiple request without blocking the thread for a single request.
  - Faster & efficient – Uses callbacks, promises, or async/await to handle responses later.
- Blocking - Executes synchronously: The process waits until an I/O operation (file read, DB query) completes.
   - Slower performance – One operation blocks others until it finishes.

# Concept of Libuv
- Libuv is an open-source libarary built-in C, It has a strong focus on asynchronous and I/O. This give node access tothe underlying computer OS, filesystem and networking.
- ode.js uses libuv to manage a thread pool for handling heavy tasks like file system operations, cryptography, and networking.
- Libuv implement two extrenely important feature of node.js
  - Event Loop
  - Thread Pool

# How Node JS Work 
<img width="400" height="600" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/fcd6160a-29d6-4a8a-b8e8-0fb522923bd5" />

## Thread Pool 
- A thread pool is a collection of pre-initialized worker threads that can be reused to perform multiple tasks instead of creating new threads every time.
- The default thread pool size in Node.js is 4 (configurable via UV_THREADPOOL_SIZE).
- We can change thread pool size - process.ev.UV_THREADPOOL_SIZE = 7;
  
### How it Works?
- A task is assigned to the thread pool.
- An available thread picks up the task and executes it.
- Once the task is complete, the thread is returned to the pool for reuse.

# Pooling



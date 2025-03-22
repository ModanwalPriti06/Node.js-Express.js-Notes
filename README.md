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
- Javascript runtime environment
- Run javascript not only browser even run anywhere.
- NodeJs use V8 and V8 is JS engine build by google that run javascript in browser.
- Engine mean: Engine take js code and node use and its compile js code in machine code.
- V8 written in C++ language.
<img width="780" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/1eb1f606-7e41-4680-85bf-1604b939a18c" />

# Event loop
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

# 

# Index
## Core Node.js Concepts
- 🔹 Node.js Modules (CommonJS vs. ES Modules)
- 🔹 Built-in Modules (fs, path, http, crypto, events, os, etc.)
- 🔹 Global Objects (__dirname, __filename, process, etc.)
- 🔹 Asynchronous Programming (Callbacks, Promises, Async/Await)
- 🔹 The Event Loop and Event-Driven Architecture
- 🔹 Streams & Buffers (Readable, Writable, Duplex, Transform Streams)
- 🔹 Working with File System (fs module)
- 🔹 Multer
- 🔹 Express Js
- Timer Module - setTimeout/ setInterval

---

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

### npm (Node Package Manager)
- It's used to manage the dependency for your node project.

### node_module
- node module folder contain all the dependencies of the node project.

### what is the role of package.json file in node project
- It keeps track of everything your project needs and is. Describes your project + manages its dependencies, scripts, metadata, and more.
- Defines project metadata
- Manages dependencies

## Dependency and Dev Dependecy
### dependency:
- These are the packages that are required for your application to run.
- They are the core libraries and tools that your project needs to function correctly in a production environment.
- When are they installed? When you run npm install
- Example: express, mongoose, axios etc.

### dev-dependency
- These are the packages that are required for development purposes only, such as testing, building, linting, and other tasks that aren't necessary for the application to run in production.
- These packages are typically used during the development phase and are not needed when the app is running in production.
- These dependencies are installed if you run npm install --save-dev or when you install the dependencies in a development environment.
```
"devDependencies": {
  "eslint": "^8.0.0",
  "nodemon": "^2.0.0",
  "jest": "^29.0.0"
}
```

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
- You can use globalThis in both environments — it's a unified global object:
  ```
  globalThis.message = "Hello World!";
  console.log(globalThis.message); // Works in both browser & Node.js
  ```
  
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
<img width="400" height="600" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/b4777e64-6aee-41be-adab-688ba2b67a5f"/>

- Call Stack: JavaScript executes synchronous code line by line, pushing and popping function calls from the stack. Every time bottom of the stack have Execution context, means whenever js program is run this callstack populate this global execution context (GEC).
- Call stack maintain the order of execution of execution context.
- Web APIs: Asynchronous tasks like setTimeout, fetch, or event listeners are handled by Web APIs.
- Callback Queue & Microtask Queue: Once asynchronous tasks are completed, their callbacks are placed in the queue.
-  Microtasks (Promises, process.nextTick in Node.js) are prioritized over macrotasks (setTimeout, setInterval).
-  Event Loop: It constantly checks if the call stack is empty and pushes queued callbacks for execution.

## Single-threaded
- A single-threaded system means that it uses only one thread to execute tasks at a time. A thread is the smallest unit of execution in a process, and in a single-threaded model, tasks are executed sequentially on a single main thread.

# Module in Node JS
- Module - When divide code small-2 part that is called modular coding.
- A module in Node.js is a reusable block of code (functions, objects, variables, etc.) that can be exported from one file and imported into another.
- Clean and maintainable code
- Reusability
- Easy debugging and testing
  
# Types of Modules in Node.js : Built-in , Local, Third-Party

| **Type** | **Description** | **Example** | 
| ------------ | ---------------| ------------ |
| Built-in Modules|	Pre-installed Node.js modules. |	fs, http, path, crypto, os, url |
| Local Modules/ User-defined Modules | Custom modules created in the project.	| require("./myModule") |
| Third-party Modules |	Installed using npm. | express, mongoose, cors , lodash |

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
- We can change thread pool size - process.ev.UV_THREADPOOL_SIZE = 7 (based on CPU core);
  
### How it Works?
- A task is assigned to the thread pool.
- An available thread picks up the task and executes it.
- Once the task is complete, the thread is returned to the pool for reuse.
  
# Pooling
<img width="400" height="600" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/617ae81a-f668-460b-a4c7-737d35542840" />

- Short Pooling: In the short pooling when client req server then server wait for res for some time and then return response either data or empty payload.
- Long Pooling: In Long pooling when client req to server then server return res only when data is there if data is not there then your req is open untill you are not getting response. After response he will again req and open that one for next response.
- **Example** can say - Group of channel in whatsapp when One user change dp u also get notification from server that time you are not req but still got response. 
- Web shocket: Bi-directional relationship b/w the client and server. When Client req then server response (Whatsapp Chat)

## Proxy
- A proxy acts as an intermediary between a client and a server.
- In Networking: A proxy server is a system or router that acts as a gateway between you and the internet. It’s used for:
  - Hiding your IP address
  - Improving security
  - Controlling internet usage (like in schools or offices).
  - Caching frequently accessed websites for speed.

<img width="400" height="400" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/fc4dd5b3-d188-43aa-a1a1-af9457c13ad8" />
<img  width="500" height="400" alt="Screenshot 2025-04-07 at 10 13 18 PM" src="https://github.com/user-attachments/assets/7f8888ef-0eda-4dbd-98e2-308dab08a139" />

- An isolated client uses a forward proxy.

<img  width="500" height="400" alt="Screenshot 2025-04-07 at 10 13 18 PM" src="https://github.com/user-attachments/assets/bfe5f100-3aa6-492a-b166-e7a9ec3e254e" />

- An isolated client uses a forward proxy.

#  Working with File System (fs module)
- The fs module in Node.js allows you to interact with the file system — like reading, writing, updating, deleting files and directories.
- Read File
  ```
  const fs = require('fs');
  fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
  });
  ```
- Write File
```
  fs.writeFile('file.txt', 'Hello, World!', (err) => {
    if (err) throw err;
    console.log('File written');
  });
```
- Append File
```
  fs.appendFile('file.txt', '\nNew Line', (err) => {
    if (err) throw err;
  });
```
-  Delete File
```
  fs.unlink('file.txt', (err) => {
    if (err) throw err;
    console.log('File deleted');
  });
```
- Create Folder
```
fs.mkdir('newFolder', (err) => {
  if (err) throw err;
});
```
- Check if File Exists
```
 fs.existsSync('file.txt'); // returns true or false
```
#### 🧠 Bonus: 
- Use fs.promises for promise-based operations (with async/await)
- Use path module to handle file paths safely
  
# Buffer and Stream
- A Buffer is a temporary storage in memory used to hold binary data (like files, images, videos, etc.) when you’re dealing with raw data. Buffer and array have some similarities, but the difference is that array can be any type, and it can be resizable. Buffers only deal with binary data, and it can not be resizable. 
- A Stream is a sequence of data chunks being transferred over time (bit-by-bit), rather than loading everything into memory at once. Stream efficient processing of large volumes of data, especially in situations where the data size is too large to fit into memory all at once.
  
## Why Streams?
- Efficient: Don’t need to load entire file into memory.
- Great for large files: e.g., video streaming, file downloads/uploads.
- Piyush garg example: 
  ```
  app.get('/download', (req, res) => {
  const filePath = 'path/to/largefile.pdf';
  const readStream = fs.createReadStream(filePathm, "utf-8");
  stream.on('data', (chunk) => res.write(chunk));
  stream.on('end', () => res.end());
  });
  ```
  - Normal Example
```
    const fs = require('fs');
    
    // Create a readable stream from an input file
    const readStream = fs.createReadStream('input.txt');
    
    // Create a writable stream to an output file
    const writeStream = fs.createWriteStream('output.txt');
    
    // Pipe the read stream into the write stream
    readStream.pipe(writeStream);
    
    // Log when it's done
    readStream.on('end', () => {
      console.log('File copied successfully using streams!');
    });
    
    // Error handling
    readStream.on('error', (err) => {
      console.error('Read error:', err);
    });
    writeStream.on('error', (err) => {
      console.error('Write error:', err);
    });
```
- pipe(): The .pipe() method connects a readable stream to a writable stream. It automatically handles backpressure — so it won’t overload the destination.

#### Real-Life Example: Sending large files to client (download API)
```
app.get('/download', (req, res) => {
  const filePath = 'path/to/largefile.pdf';
  const fileName = 'downloadedfile.pdf';

  res.setHeader('Content-Disposition', `attachment; filename="${fileName}"`);

  const readStream = fs.createReadStream(filePath);
  readStream.pipe(res);
});
```

## 4 Types of Streams:
1. Readable – e.g., fs.createReadStream()
2. Writable – e.g., fs.createWriteStream()
3. Duplex – both readable and writable (e.g., TCP sockets)
4. Transform – a special duplex stream for modifying data (e.g., gzip)
```
 reader.pipe(writer); // sends data chunk by chunk
```
# Make any file zip
- So creating any file zip - we have to read file then convert into zip then have to write that is process. but read and again convert in zip taking twise mb in memory so reducing the memory we can use stream only have to create zip file and have to send write with help of pipe() function
- Solution : Stream Read --> Zipper ---> fs Write Stream 
- Example:
  ```
  fs.createReadStream(filePath).pipe(
  zlib,createGzip().pipe(                //zlib is library create file in zip
    fs.createWriteStream('./sample.zip'))
    )
  ```
  
## 💡 In Real Life:
- Buffer is like downloading the whole movie before watching.
- Stream is like watching a movie while it's still downloading.

# Multer
- In multer use to upload file and that file you can store in memory or disk.
  
### For Disk Storage
- The disk storage engine gives you full control on storing files to disk.
- install multer - npm i multer
```
const multer  = require('multer')
// const upload = multer({ dest: '../uploads' })  // whatever file uploading keep in uploads folder

// diskstorage
const storage = multer.diskStorage({
  destination: function (req, file, cb) {
    return cb(null, './uploads');
  },
  filename: function (req, file, cb) {
    return cb(null, `${Date.now()}-${file.originalname}`);
  }  
})

const upload = multer({ storage: storage })
```
In API -  for single file
```
router.post('/uploadFile', authTokenHandler, upload.single('notebookFile'), async (req, res) => {
```
In API -  for multiple file
```
router.post('/uploadFile', authTokenHandler, upload.array('notebookFile'), async (req, res) => {
```
### For Memory Storage
- The memory storage engine stores the files in memory as Buffer objects. It doesn't have any options.
```
const storage = multer.memoryStorage()
const upload = multer({ storage: storage })
```
  ---
  ---
  ---
  
 # Express JS

### What is Express jS?
- Express.js is a minimal and flexible Node.js web application framework that helps you build web servers and APIs quickly and efficiently.
- Hosting of Node.js projects

### Why Use Express?
- Routing - Simplifies creating routes (GET, POST, etc.)
- Easily handle request and response objects.
- Middleware- Supports middleware for functionality like logging, authentication, and error handling.
- Works great with MongoDB, PostgreSQL, and other databases.
- Error Handling
- RESTful API
  
```
  const express = require('express');
  const app = express();
  
  app.get('/', (req, res) => {
    res.send('Hello from Express!');
  });
  
  app.listen(3000, () => {
    console.log('Server running on http://localhost:3000');
  });
```
# Middleware
- Middleware is a function that has access to the request (req), response (res), and the next middleware in the request-response cycle.
- next() - This function is used to execute the other midddleware function succeeding the current middleware.

## Type of Middleware

1. Applications-level Middleware (app.use)
2. Router level Middleware (router.use)
3. Built-in level Middleware (express.static, express.json, express.unlencoded)
4. Error handling Middleware ( app.use(err, req, res, next) )
5. Third-party Middleware ( bodyparser, cookie parser ) 

## Application-level Middleware: 
  
- Application-level middleware in Express is middleware that is bound to your entire app instance using app.use() or a specific HTTP method like app.get() or app.post().
```
const express = require('express');
const app = express();

// Application-level middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});

app.get('/', (req, res) => {
  res.send('Home Page');
});

app.listen(3000, () => console.log('Server started'));

```
#### Common Use case 
- Logging
- Authentication
- Body parsing (express.json())
- CORS handling
- Custom headers or response formatting
  
## Router level Middleware
- Router-level middleware is just like application-level middleware, but it is bound to an Express Router instance instead of the whole app.
- It helps keep your code modular and organized, especially in large apps.

#### Common use cases
- Authentication & Authorization
- Role-based Access Control
- Request Validation

```
const express = require('express');
const app = express();
const router = express.Router();

// Router-level middleware
router.use((req, res, next) => {
  console.log('Router-level middleware');
  next();
});

// Route in router
router.get('/user', (req, res) => {
  res.send('User route');
});

// Mount router to app
app.use('/api', router);

app.listen(3000, () => console.log('Server running'));

```
## Built-in Middleware
1. express.static(): Serves static files like HTML, CSS, JS, images, etc.
2. express.json():
 - Parses incoming requests with JSON payloads.
 - Used in APIs that send/receive JSON.
```
// convert
{
  "name": "John"  = {name: 'john}
}
```
3. express.urlencoded()
  - Parses URL-encoded data from forms (like <form> submissions).
```
const express = require('express');
const app = express();

app.use(express.json()); // JSON payload
app.use(express.urlencoded({ extended: true })); // form data //  extended: true means it can handle nested objects too.
app.use(express.static('public')); // serve static files

app.post('/data', (req, res) => {
  console.log(req.body);
  res.send('Data received!');
});

app.listen(3000, () => console.log('Server running...'));
```
## Error Handling Middleware:
- Express js is capable of handling any sort of errors when occured bcz it has the tendency of default error -handlings and defined error handling.
- A special kind of middleware in Express that catches errors during the request-response cycle
  ```
  (err, req, res, next)
  -------------------------------------------------------
  const express = require('express');
  const app = express();
  
  // Regular middleware
  app.get('/', (req, res) => {
    throw new Error('Something went wrong!');
  });
  
  // Error handling middleware
  app.use((err, req, res, next) => {
    console.error(err.stack); // Log the error
    res.status(500).send('Something broke!');
  });
  
  app.listen(3000, () => console.log('Server running'));
  ------------------------------------------------------------
  ```
## Third-Party Middleware
- Third-party middleware is a middleware function provided by an external library/package that you install via npm. It adds additional functionality to your app like logging, security, CORS, file uploads, and more.
   
## How to use
- npm install <package-name>
- npm install cors
```
const middleware = require('<package-name>');
app.use(middleware());
```
```
  const cors = require('cors');
  app.use(cors()); // allow all origins by default
```
- npm install multer
```
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded!');
});
```
---- 
# Routing
- Routing refers to how an application responds to client requests to a particular endpoint (URL path) and HTTP method (GET, POST, etc.).
- Routing = URL + HTTP method + handler function
  
| **Method** | **Use Case** |
| ------ | ----------| 
| GET |	Read / Fetch data |
| POST |	Create / Submit data |
| PUT |	Update existing data |
| DELETE | Remove data |

## Export and Import Module
- In Node.js (and JavaScript), export is used to make variables/functions accessible to other files, and import is used to bring them in.

### 1. CommonJS (default in Node.js)
 Use module.exports and require()
 ```
  module.exports = add;
```
```
const add = require('./math');
```

### 2. ES Modules (ESM)
Use export / export default and import

- Named Export
```
export const add = (a, b) => a + b;
export const sub = (a, b) => a - b;
```
- Named Import
```
import { add, sub } from './math.js';
```
- Default Export
```
export default function greet(name) {
  return `Hello, ${name}`;
}
```
- Default Named
```
import greet from './greet.js';
```

##  What is REPL in Node.js?
- REPL stands for:
🔁 Read
📥 Eval
📤 Print
🛑 Loop
- It is a command-line tool that lets you interactively write and run JavaScript code directly in the terminal.

# Timers Module
- The Timers module in NodeJS contains various functions that allow us to execute a block of code or a function after a set period. The Timers module is global, we do not need to use require() to import it.

### setTimeout Vs setInterval 

#### setTimeout: 
- The setTimeout() function is used to execute a function once after a specified delay (in milliseconds).
- Syntax: 
```
setTimeout(callback, delay, [arg1, arg2, ...]);
```
#### setImmediate() method
- The setImmediate() function is used to execute a callback function immediately after the current event loop cycle, i.e., after the I/O events in the Node.js event loop have been processed. It is similar to setTimeout() with a delay of 0 milliseconds, but it differs in terms of when the function is executed.
- Syntax
```
setImmediate(callback, [arg1, arg2, ...]);
```
#### setInterval() method
- The setInterval() function is used to execute a function repeatedly, with a fixed time delay between each call.
```
  setInterval(callback, delay, [arg1, arg2, ...]);
```
### What are the three methods to avoid callback hell?
- The three methods to avoid callback hell are:

1. Using async/await()
2. Using promises
3. Using generators

### What is a .body-parser in NodeJS?
- Body-parser is the NodeJS body-parsing middleware. It is responsible for parsing the incoming request bodies in a middleware before you handle it. It is an NPM module that processes data sent in HTTP requests.

###  What is a cluster in NodeJS?
- Node.js runs your app using a single thread by default (just one CPU core).
- But modern computers have multiple cores, right?
- ➡️ Cluster lets you run multiple instances of your Node.js app using all CPU cores to handle more traffic and improve performance.

### Why use Cluster?
1. Handles more users/requests
2. Takes full advantage of multi-core CPUs
3. Improves performance of heavy apps

### Explain some of the cluster methods in NodeJS
1. Fork(): It creates a new child process from the master. The isMaster returns true if the current process is master or else false.
2. isWorker: It returns true if the current process is a worker or else false.
3. process: It returns the child process which is global.
4. send(): It sends a message from worker to master or vice versa.
5. kill(): It is used to kill the current worker.

### How to manage sessions in NodeJS?
Session management can be done in NodeJS by using the express-session module. It helps in saving the data in the key-value form. In this module, the session data is not saved in the cookie itself, just the session ID.

### Explain the NodeJS Redis module.
- Redis is an Open Source store for storing data structures. It is used in multiple ways. It is used as a database, cache, and message broker. It can store data structures such as strings, hashes, sets, sorted sets, bitmaps, indexes, and streams. Redis is very useful for NodeJS developers as it reduces the cache size which makes the application more efficient. However, it is very easy to integrate Redis with NodeJS applications.

### What is web socket?
- Web Socket is a protocol that provides full-duplex (multiway) communication i.e. allows communication in both directions simultaneously. Web Socket is a modern web technology in which there is a continuous connection between the user’s browser (client) and the server. In this type of communication, between the web server and the web browser, both of them can send messages to each other at any point in time.

### MVC Architecture
- MVC stands for Model View Controller. The Model-View-Controller (MVC) framework is a way of organizing code for web applications. It separates the application into three parts: the Model, the View, and the Controller. 
Example:
```
// Controller
app.get('/user/:id', (req, res) => {
  User.findById(req.params.id)       // → Model
    .then(user => res.render('user', { user })); // → View
});
```
1. Model: User (MongoDB schema)
2. View: HTML/EJS template
3. Controller: app.get() handler

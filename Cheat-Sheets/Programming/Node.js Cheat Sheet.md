# 🟩 Node.js Cheat Sheet

A concise, practical reference for Node.js developers — covering commands, modules, and best practices for backend development.

---

## 📘 Overview

**Node.js** is a JavaScript runtime built on Chrome’s V8 engine.  
It allows you to run JS code outside the browser, ideal for building APIs, servers, and CLI tools.

---

## ⚙️ Installation & Setup

```bash
# Check Node.js and npm versions
node -v
npm -v

# Initialize a new Node project
npm init -y

# Install and uninstall packages
npm install <package-name>
npm uninstall <package-name>

# Install a package globally
npm install -g <package-name>
````

---

## 📁 Project Structure Example

```
my-app/
├── package.json
├── index.js
├── /src
│   ├── app.js
│   └── utils.js
└── /node_modules
```

---

## 📦 package.json Essentials

```json
{
  "name": "my-app",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^3.0.0"
  }
}
```

### Common npm commands

```bash
npm run start     # Run start script
npm run dev       # Run custom script
npm install       # Install dependencies
npm update        # Update dependencies
npm audit fix     # Fix vulnerabilities
```

---

## 🧩 Core Modules

| Module   | Description            | Example                            |
| -------- | ---------------------- | ---------------------------------- |
| `fs`     | File System operations | `fs.readFileSync('file.txt')`      |
| `path`   | File path utilities    | `path.join(__dirname, 'file.txt')` |
| `os`     | System information     | `os.platform()`                    |
| `http`   | Create HTTP server     | `http.createServer(...)`           |
| `url`    | URL parsing            | `new URL(req.url, base)`           |
| `events` | Custom event handling  | `emitter.on('data', ...)`          |
| `crypto` | Encryption and hashing | `crypto.createHash('sha256')`      |

---

## 🌐 Basic HTTP Server

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, Node.js!');
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

---

## 🚀 Express.js Example

```js
const express = require('express');
const app = express();

app.use(express.json());

app.get('/', (req, res) => res.send('Hello, Express!'));

app.post('/data', (req, res) => {
  console.log(req.body);
  res.status(201).send('Data received');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

---

## 🗂️ File System (fs)

```js
const fs = require('fs');

// Read file synchronously
const data = fs.readFileSync('text.txt', 'utf8');

// Write file synchronously
fs.writeFileSync('output.txt', 'Hello Node!');

// Async read
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

---

## 🔄 Modules & Exports

**utils.js**

```js
function add(a, b) { return a + b; }
module.exports = { add };
```

**app.js**

```js
const { add } = require('./utils');
console.log(add(2, 3)); // 5
```

---

## ⚡ ES Modules (Modern Syntax)

Enable in `package.json`:

```json
"type": "module"
```

Then import:

```js
import fs from 'fs';
import express from 'express';
```

---

## 🧠 Environment Variables

**.env**

```
PORT=3000
DB_URL=mongodb://localhost:27017/mydb
```

**Usage**

```js
require('dotenv').config();
console.log(process.env.PORT);
```

---

## 🪵 Console & Debugging

```js
console.log('Info message');
console.error('Error message');
console.table([{ name: 'Alice' }, { name: 'Bob' }]);
console.time('timer');
console.timeEnd('timer');
```

---

## 🧰 Useful npm Packages

| Package       | Purpose                 |
| ------------- | ----------------------- |
| **express**   | Web framework           |
| **dotenv**    | Environment variables   |
| **nodemon**   | Auto-restart on save    |
| **axios**     | HTTP client             |
| **chalk**     | Colorful console output |
| **commander** | Build CLI tools         |
| **cors**      | Enable CORS for APIs    |
| **mongoose**  | MongoDB ODM             |
| **jest**      | Testing framework       |

---

## 🧪 Simple CLI Script Example

```js
#!/usr/bin/env node
console.log('Custom CLI running!');
```

Make executable:

```bash
chmod +x cli.js
./cli.js
```

---

## 🧹 Common Node Commands Recap

```bash
node file.js             # Run a file
node --inspect app.js    # Debug mode
npm init -y              # Create package.json
npm install <pkg>        # Install dependency
npm install -g <pkg>     # Install globally
npm outdated             # Check for updates
npm audit fix            # Fix vulnerabilities
```

---

## 🧾 Best Practices

✅ Use `const` and `let` (avoid `var`)
✅ Always handle errors (`try/catch`, `async/await`)
✅ Avoid blocking (prefer async APIs)
✅ Store secrets in `.env`
✅ Keep dependencies up to date
✅ Use linters (ESLint) and formatters (Prettier)

---

## 📚 References

* [Node.js Official Docs](https://nodejs.org/en/docs)
* [npm Docs](https://docs.npmjs.com/)
* [Express Docs](https://expressjs.com/)

---

# 🟩 Express.js Cheat Sheet

A fast, practical reference for building APIs, middleware, servers, and routing using the Express.js framework.

---

## 📘 Overview

**Express.js** is a minimalist and flexible Node.js framework used for building web servers and REST APIs.  
It provides routing, middleware, utilities, and easy integration with databases.

Install Express:

```bash
npm install express
````

---

## 🏁 Basic Express Server

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello Express.js!');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

---

## 📦 Middleware Essentials

Enable JSON parsing:

```js
app.use(express.json());
```

Logging middleware example:

```js
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```

Serve static files:

```js
app.use(express.static('public'));
```

---

## 🌐 Routing

### Basic Routes

```js
app.get('/users', (req, res) => res.send('GET users'));
app.post('/users', (req, res) => res.send('POST users'));
app.put('/users/:id', (req, res) => res.send('PUT user'));
app.delete('/users/:id', (req, res) => res.send('DELETE user'));
```

### Route Parameters

```js
app.get('/book/:id', (req, res) => {
  res.send(`Book ID: ${req.params.id}`);
});
```

### Query Parameters

```js
app.get('/search', (req, res) => {
  res.send(req.query); // ?q=apple&page=2
});
```

### Router Instance

```js
const router = express.Router();

router.get('/', (req, res) => res.send('List items'));
router.post('/', (req, res) => res.send('Create item'));

app.use('/items', router);
```

---

## 📤 Sending Responses

```js
res.send('Hello');
res.json({ message: 'OK' });
res.status(201).json({ created: true });
res.download('file.txt');
res.sendFile(path.join(__dirname, 'index.html'));
```

---

## 🧠 Request Data Access

```js
req.params;  // URL params
req.query;   // Query string
req.body;    // JSON body
req.headers; // Request headers
```

---

## 🧩 Middleware Types

| Middleware Type   | Purpose                       |
| ----------------- | ----------------------------- |
| Application-level | `app.use()`                   |
| Router-level      | `router.use()`                |
| Built-in          | `express.json()`              |
| Error-handling    | `(err, req, res, next) => {}` |
| Third-party       | `cors`, `morgan`, etc.        |

---

## ⚠️ Error Handling

Basic error handler:

```js
app.use((err, req, res, next) => {
  console.error(err.message);
  res.status(500).json({ error: 'Server error' });
});
```

Throw an error:

```js
app.get('/', (req, res) => {
  throw new Error('Something went wrong');
});
```

Async error example:

```js
app.get('/async', async (req, res, next) => {
  try {
    const data = await fetchData();
    res.send(data);
  } catch (err) {
    next(err);
  }
});
```

---

## 🔐 CORS Setup

```js
const cors = require('cors');
app.use(cors());
```

Or custom config:

```js
app.use(cors({
  origin: 'http://localhost:3000',
  methods: 'GET,POST'
}));
```

---

## 🗄️ Working With Databases

### MongoDB (Mongoose example)

```js
const mongoose = require('mongoose');

mongoose.connect(process.env.DB_URL)
  .then(() => console.log('MongoDB connected'))
  .catch(err => console.error(err));
```

User model:

```js
const User = mongoose.model('User', {
  name: String,
  email: String
});
```

Route example:

```js
app.get('/users', async (req, res) => {
  const users = await User.find();
  res.json(users);
});
```

---

## 🔑 Environment Variables

```bash
npm install dotenv
```

```js
require('dotenv').config();
console.log(process.env.PORT);
```

---

## 🧪 Testing With Supertest

Install:

```bash
npm install --save-dev supertest jest
```

Test example:

```js
const request = require('supertest');
const app = require('./app');

test('GET /', async () => {
  const res = await request(app).get('/');
  expect(res.statusCode).toBe(200);
});
```

---

## 🧰 Useful Packages

| Package               | Purpose                   |
| --------------------- | ------------------------- |
| **cors**              | CORS support              |
| **morgan**            | HTTP logging              |
| **dotenv**            | Environment variables     |
| **helmet**            | Security headers          |
| **cookie-parser**     | Parse cookies             |
| **multer**            | File uploads              |
| **compression**       | Gzip response compression |
| **express-validator** | Validation middleware     |

---

## 🧹 Common Express Patterns

### Controller Pattern

```
/controllers
   userController.js
/routes
   userRoutes.js
```

**Controller**

```js
exports.getUsers = (req, res) => { res.send('Users'); };
```

**Route**

```js
const express = require('express');
const { getUsers } = require('../controllers/userController');
const router = express.Router();

router.get('/', getUsers);

module.exports = router;
```

**App**

```js
app.use('/users', require('./routes/userRoutes'));
```

---

## ✨ Best Practices

✅ Use async/await
✅ Centralize error handling
✅ Validate all data (`express-validator`)
✅ Use `.env` for secrets
✅ Minimize global middleware
✅ Organize routes into modules
✅ Sanitize inputs to prevent attacks
✅ Log meaningful information

# 🌐 API Foundations & REST Essentials Cheat Sheet

A concise, practical reference covering API fundamentals, request structure, JSON, server-side requests with Axios, authentication methods, and REST API concepts.

The file includes:
✔ Introduction to APIs
✔ Structuring API Requests
✔ What is JSON
✔ Server-side API Requests (Axios)
✔ API Authentication
✔ REST APIs

---

# 001 — Introduction to APIs

## 🔍 What Is an API?
**API (Application Programming Interface)** is a set of rules that allows one piece of software to communicate with another.

APIs allow:
- A client (browser/app/server) to **request** data.
- A server to **respond** with data (usually JSON).

## 🧩 Real-World Examples
- Weather apps fetching temperature from a weather service.
- Login with Google/Facebook → uses OAuth APIs.
- E-commerce websites fetching product data.

## 🔗 Key API Concepts
| Term | Meaning |
|------|---------|
| **Endpoint** | A specific URL for accessing API data. |
| **Client** | The system making the request. |
| **Server** | The system responding with data. |
| **Request** | The client asking for data/action. |
| **Response** | The server sending data back. |

---

# 002 — Structuring API Requests

APIs commonly use the **HTTP protocol**.

## 📤 HTTP Methods (CRUD Mapping)
| Method | Description | CRUD |
|--------|-------------|------|
| **GET** | Fetch data | Read |
| **POST** | Send new data | Create |
| **PUT** | Replace existing data | Update |
| **PATCH** | Update part of existing data | Update |
| **DELETE** | Remove data | Delete |

## 📦 API Request Structure
Each request has 3 main parts:

### **1. URL (Endpoint)**
```

[https://api.example.com/users](https://api.example.com/users)

```

### **2. Headers**
```

Content-Type: application/json
Authorization: Bearer <token>

````

### **3. Body** (only for POST/PUT/PATCH)
```json
{
  "name": "John",
  "email": "john@example.com"
}
````

## 🏗️ Example Request (POST)

```
POST /api/users
Content-Type: application/json

{
  "name": "Sarah",
  "age": 25
}
```

---

# 003 — What is JSON?

**JSON (JavaScript Object Notation)** is the most common format for API data.

## ✔ Why JSON?

* Lightweight
* Human-readable
* Works well with JavaScript (object-like syntax)
* Language-independent

## 📄 Basic JSON Example

```json
{
  "id": 1,
  "name": "Alice",
  "hobbies": ["reading", "coding"],
  "address": {
    "city": "Tehran",
    "zip": "12345"
  }
}
```

## JSON Rules

✔ Keys must be in **double quotes**
✔ No trailing commas
✔ Supports:

* Object `{ }`
* Array `[ ]`
* String
* Number
* Boolean
* Null

---

# 004 — Making Server-Side API Requests With Axios

Axios is a popular HTTP client for Node.js and browsers.

Install:

```bash
npm install axios
```

## 📥 GET Request

```js
const axios = require('axios');

const getUsers = async () => {
  const res = await axios.get('https://api.example.com/users');
  console.log(res.data);
};
```

## 📤 POST Request

```js
const createUser = async () => {
  const res = await axios.post('https://api.example.com/users', {
    name: "Ali",
    age: 30
  });
  console.log(res.data);
};
```

## 🏷️ Passing Headers

```js
axios.get('https://api.example.com/data', {
  headers: {
    Authorization: "Bearer YOUR_TOKEN"
  }
});
```

## ❗ Error Handling

```js
try {
  const res = await axios.get(url);
} catch (err) {
  console.error(err.response?.data || err.message);
}
```

---

# 005 — API Authentication

APIs often require authentication before granting access.

## 🔐 Common Authentication Methods

### 1. **API Keys**

* Simple token used in headers or query params.

```js
axios.get(url, {
  headers: { 'x-api-key': '123abc' }
});
```

### 2. **Bearer Token**

Used in OAuth, JWT, etc.

```js
axios.get(url, {
  headers: { Authorization: `Bearer ${token}` }
});
```

### 3. **Basic Auth**

Base64 encoded username:password

```js
axios.get(url, {
  auth: {
    username: 'user',
    password: 'pass'
  }
});
```

### 4. **OAuth 2.0**

Used by:

* Google
* Facebook
* GitHub
* Spotify

Tokens expire & refresh routines required.

### 5. **Cookies / Session Auth**

Used in web apps (server-side authentication).

---

# 006 — REST APIs

## 🌐 What is REST?

**REST (Representational State Transfer)** is an architectural style used for building APIs.

A REST API follows these rules:

* Stateless
* Client-Server separation
* Cacheable responses
* Uses HTTP methods properly
* Resource-based URLs

---

## 📚 REST URL Design (Resources)

✔ Use nouns, not verbs
✔ Use plural for collections

| Bad           | Good     |
| ------------- | -------- |
| /getUsers     | /users   |
| /createUser   | /users   |
| /deleteUser/1 | /users/1 |

---

## 🔄 REST Endpoints (Example: Users)

| Method     | Endpoint   | Action        |
| ---------- | ---------- | ------------- |
| **GET**    | /users     | Get all users |
| **GET**    | /users/:id | Get one user  |
| **POST**   | /users     | Create user   |
| **PUT**    | /users/:id | Replace user  |
| **PATCH**  | /users/:id | Update user   |
| **DELETE** | /users/:id | Delete user   |

---

## 📤 REST Responses (JSON)

### Success Example

```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "Sara"
  }
}
```

### Error Example

```json
{
  "success": false,
  "error": "User not found"
}
```

# 🌐 API Foundations & REST Essentials Cheat Sheet

A concise, practical reference covering API fundamentals, request structure, JSON, server-side requests with Axios, authentication methods, and REST API concepts.

The file includes:
✔ Introduction to APIs
✔ Structuring API Requests
✔ What is JSON
✔ Server-side API Requests (Axios)
✔ API Authentication
✔ REST APIs

---

# 001 — Introduction to APIs

## 🔍 What Is an API?
**API (Application Programming Interface)** is a set of rules that allows one piece of software to communicate with another.

APIs allow:
- A client (browser/app/server) to **request** data.
- A server to **respond** with data (usually JSON).

## 🧩 Real-World Examples
- Weather apps fetching temperature from a weather service.
- Login with Google/Facebook → uses OAuth APIs.
- E-commerce websites fetching product data.

## 🔗 Key API Concepts
| Term | Meaning |
|------|---------|
| **Endpoint** | A specific URL for accessing API data. |
| **Client** | The system making the request. |
| **Server** | The system responding with data. |
| **Request** | The client asking for data/action. |
| **Response** | The server sending data back. |

---

# 002 — Structuring API Requests

APIs commonly use the **HTTP protocol**.

## 📤 HTTP Methods (CRUD Mapping)
| Method | Description | CRUD |
|--------|-------------|------|
| **GET** | Fetch data | Read |
| **POST** | Send new data | Create |
| **PUT** | Replace existing data | Update |
| **PATCH** | Update part of existing data | Update |
| **DELETE** | Remove data | Delete |

## 📦 API Request Structure
Each request has 3 main parts:

### **1. URL (Endpoint)**
```

[https://api.example.com/users](https://api.example.com/users)

```

### **2. Headers**
```

Content-Type: application/json
Authorization: Bearer <token>

````

### **3. Body** (only for POST/PUT/PATCH)
```json
{
  "name": "John",
  "email": "john@example.com"
}
````

## 🏗️ Example Request (POST)

```
POST /api/users
Content-Type: application/json

{
  "name": "Sarah",
  "age": 25
}
```

---

# 003 — What is JSON?

**JSON (JavaScript Object Notation)** is the most common format for API data.

## ✔ Why JSON?

* Lightweight
* Human-readable
* Works well with JavaScript (object-like syntax)
* Language-independent

## 📄 Basic JSON Example

```json
{
  "id": 1,
  "name": "Alice",
  "hobbies": ["reading", "coding"],
  "address": {
    "city": "Tehran",
    "zip": "12345"
  }
}
```

## JSON Rules

✔ Keys must be in **double quotes**
✔ No trailing commas
✔ Supports:

* Object `{ }`
* Array `[ ]`
* String
* Number
* Boolean
* Null

---

# 004 — Making Server-Side API Requests With Axios

Axios is a popular HTTP client for Node.js and browsers.

Install:

```bash
npm install axios
```

## 📥 GET Request

```js
const axios = require('axios');

const getUsers = async () => {
  const res = await axios.get('https://api.example.com/users');
  console.log(res.data);
};
```

## 📤 POST Request

```js
const createUser = async () => {
  const res = await axios.post('https://api.example.com/users', {
    name: "Ali",
    age: 30
  });
  console.log(res.data);
};
```

## 🏷️ Passing Headers

```js
axios.get('https://api.example.com/data', {
  headers: {
    Authorization: "Bearer YOUR_TOKEN"
  }
});
```

## ❗ Error Handling

```js
try {
  const res = await axios.get(url);
} catch (err) {
  console.error(err.response?.data || err.message);
}
```

---

# 005 — API Authentication

APIs often require authentication before granting access.

## 🔐 Common Authentication Methods

### 1. **API Keys**

* Simple token used in headers or query params.

```js
axios.get(url, {
  headers: { 'x-api-key': '123abc' }
});
```

### 2. **Bearer Token**

Used in OAuth, JWT, etc.

```js
axios.get(url, {
  headers: { Authorization: `Bearer ${token}` }
});
```

### 3. **Basic Auth**

Base64 encoded username:password

```js
axios.get(url, {
  auth: {
    username: 'user',
    password: 'pass'
  }
});
```

### 4. **OAuth 2.0**

Used by:

* Google
* Facebook
* GitHub
* Spotify

Tokens expire & refresh routines required.

### 5. **Cookies / Session Auth**

Used in web apps (server-side authentication).

---

# 006 — REST APIs

## 🌐 What is REST?

**REST (Representational State Transfer)** is an architectural style used for building APIs.

A REST API follows these rules:

* Stateless
* Client-Server separation
* Cacheable responses
* Uses HTTP methods properly
* Resource-based URLs

---

## 📚 REST URL Design (Resources)

✔ Use nouns, not verbs
✔ Use plural for collections

| Bad           | Good     |
| ------------- | -------- |
| /getUsers     | /users   |
| /createUser   | /users   |
| /deleteUser/1 | /users/1 |

---

## 🔄 REST Endpoints (Example: Users)

| Method     | Endpoint   | Action        |
| ---------- | ---------- | ------------- |
| **GET**    | /users     | Get all users |
| **GET**    | /users/:id | Get one user  |
| **POST**   | /users     | Create user   |
| **PUT**    | /users/:id | Replace user  |
| **PATCH**  | /users/:id | Update user   |
| **DELETE** | /users/:id | Delete user   |

---

## 📤 REST Responses (JSON)

### Success Example

```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "Sara"
  }
}
```

### Error Example

```json
{
  "success": false,
  "error": "User not found"
}
```

### form example

* formaction 
The formaction attribute specifies where to send the form-data when a form is submitted. This attribute overrides the form's action attribute.

The formaction attribute is only used for inputs/buttons with type="submit".

```html
<form id="myForm" method="post">
      <label for="idInput">Id:</label>
      <input type="text" id="idInput" name="id">

      <label for="secretInput">Secret:</label>
      <input type="text" id="secretInput" name="secret">

      <label for="scoreInput">Score:</label>
      <input type="number" id="scoreInput" name="score">

      <label for="submit">Route:</label>
      <input id="get" type="submit" value="GET" formaction="/get-secret">
      <input id="post" type="submit" value="POST" formaction="/post-secret">
      <input id="put" type="submit" value="PUT" formaction="/put-secret">
      <input id="patch" type="submit" value="PATCH" formaction="/patch-secret">
      <input id="delete" type="submit" value="DELETE" formaction="/delete-secret">
    </form>
```

---

# 🧠 Quick Summary

### APIs allow software to talk to each other

### Requests use methods, headers, and (optionally) bodies

### JSON is the standard data format

### Axios is used to send HTTP requests from Node.js

### Authentication uses keys, tokens, or sessions

### REST defines clean, resource-based APIs


# 🟩 EJS Cheat Sheet

A fast, practical reference for **Embedded JavaScript (EJS)** — a templating language used to generate HTML markup with plain JavaScript.

---

## 📘 Overview

**EJS** lets you embed JavaScript directly inside HTML using special tags.  
Commonly used with Express.js for building dynamic server-rendered pages.

Install:

```bash
npm install ejs
````

Set up with Express:

```js
app.set('view engine', 'ejs');
```

Render a template:

```js
app.get('/', (req, res) => {
  res.render('index', { title: 'Home Page' });
});
```

---

## 🏷️ EJS Tag Types

| Tag      | Purpose                   |
| -------- | ------------------------- |
| `<%= %>` | Output **escaped** value  |
| `<%- %>` | Output **unescaped** HTML |
| `<% %>`  | Run JS **without output** |
| `<%# %>` | Comment (ignored)         |
| `<%%`    | Prints `<%` character     |

---

## ✨ Output Examples

### Escaped Output

```ejs
<%= user.name %>
```

### Unescaped (render raw HTML)

```ejs
<%- htmlContent %>
```

### No Output (logic only)

```ejs
<% if (loggedIn) { %>
  <p>Welcome back!</p>
<% } %>
```

---

## 🔁 Loops

### For Loop

```ejs
<ul>
  <% for (let i = 0; i < users.length; i++) { %>
    <li><%= users[i].name %></li>
  <% } %>
</ul>
```

### ForEach Loop

```ejs
<% users.forEach(user => { %>
  <p><%= user.name %></p>
<% }) %>
```

---

## 🔀 Conditionals

```ejs
<% if (age >= 18) { %>
  <p>Adult</p>
<% } else { %>
  <p>Minor</p>
<% } %>
```

---

## 📦 Include Partials

Render reusable components (header, footer, nav, etc.)

```ejs
<%- include('partials/header') %>
<h1><%= title %></h1>
<%- include('partials/footer') %>
```

Include with variables:

```ejs
<%- include('partials/card', { product: item }) %>
```

---

## 🧱 Layout Structure (Common Pattern)

```
views/
├── partials/
│   ├── header.ejs
│   ├── footer.ejs
├── pages/
│   ├── home.ejs
│   ├── about.ejs
└── layout.ejs
```

---

## 🧩 Using Variables

Passing data from Express:

```js
res.render('profile', {
  name: 'John',
  hobbies: ['coding', 'gaming']
});
```

Access in template:

```ejs
<h1><%= name %></h1>

<ul>
  <% hobbies.forEach(hobby => { %>
    <li><%= hobby %></li>
  <% }) %>
</ul>
```

---

## 📜 Template Comments

```ejs
<%# This comment will not appear in HTML %>
```

---

## 🧮 JavaScript in EJS

```ejs
<%
  const fullName = user.first + " " + user.last;
%>

<p><%= fullName %></p>
```

Ternary expressions:

```ejs
<p>Status: <%= active ? 'Active' : 'Inactive' %></p>
```

---

## 🗂️ Working With Arrays & Objects

### Array:

```ejs
<% items.forEach(item => { %>
  <li><%= item %></li>
<% }) %>
```

### Object:

```ejs
<p><%= product.name %> - $<%= product.price %></p>
```

---

## 🧱 Forms Example

```ejs
<form action="/submit" method="POST">
  <input type="text" name="username" />
  <button>Submit</button>
</form>
```

---

## 🖼️ Inline Styles & Script Tags

```ejs
<style>
  h1 { color: blue; }
</style>

<script>
  console.log("EJS loaded");
</script>
```

---

## 🧬 Escaping Characters

To literally print `<%`:

```ejs
<%%
This prints '<%' in output
```

---

## 🧰 Useful Tips

✔ Use `<%- %>` carefully (avoid XSS)
✔ Group templates in folders
✔ Use partials to avoid repetition
✔ Pass only required data to views
✔ Keep logic simple (avoid heavy calculations)

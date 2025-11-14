# 🟩 Express + EJS Project Structure (Boilerplate)

A clean, scalable boilerplate for building Express.js applications with EJS templating, partials, layouts, routing, and organized controllers.

---

## 📁 Project Structure

```

my-app/
├── package.json
├── server.js
├── /public
│   ├── css/
│   ├── js/
│   └── images/
├── /views
│   ├── /partials
│   │   ├── header.ejs
│   │   └── footer.ejs
│   ├── /pages
│   │   ├── home.ejs
│   │   └── about.ejs
│   ├── layout.ejs
│   └── 404.ejs
├── /routes
│   ├── index.js
│   └── about.js
└── /controllers
├── homeController.js
└── aboutController.js

````

---

## 📦 package.json (Example)

```json
{
  "name": "express-ejs-app",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "dev": "nodemon server.js",
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "ejs": "^3.1.9"
  },
  "devDependencies": {
    "nodemon": "^3.0.0"
  }
}
````

---

## 🖥️ server.js (Main App Entry)

```js
const express = require('express');
const app = express();
const path = require('path');

// View engine
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// Public folder
app.use(express.static(path.join(__dirname, 'public')));
app.use(express.urlencoded({ extended: true }));

// Routes
app.use('/', require('./routes/index'));
app.use('/about', require('./routes/about'));

// 404 Page
app.use((req, res) => {
  res.status(404).render('404', { title: 'Page Not Found' });
});

// Start server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

---

## 🧩 Views

### 📄 layout.ejs (Main Layout Template)

```ejs
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title><%= title %></title>
  <link rel="stylesheet" href="/css/style.css" />
</head>
<body>

  <%- include('partials/header') %>

  <main>
    <%- body %>
  </main>

  <%- include('partials/footer') %>

</body>
</html>
```

---

### 🧩 Partial: header.ejs

```ejs
<header>
  <nav>
    <a href="/">Home</a>
    <a href="/about">About</a>
  </nav>
</header>
```

---

### 🧩 Partial: footer.ejs

```ejs
<footer>
  <p>© <%= new Date().getFullYear() %> My Website</p>
</footer>
```

---

### 🏠 Page: home.ejs

```ejs
<%- include('../layout', { title: 'Home Page', body: `
  <h1>Welcome to the Home Page</h1>
  <p>This is an Express + EJS boilerplate project.</p>
` }) %>
```

---

### ℹ️ Page: about.ejs

```ejs
<%- include('../layout', { title: 'About Page', body: `
  <h1>About Us</h1>
  <p>We build great Express.js applications.</p>
` }) %>
```

---

### ❌ 404.ejs

```ejs
<%- include('layout', { title: '404 - Not Found', body: `
  <h1>404</h1>
  <p>The page you're looking for does not exist.</p>
` }) %>
```

---

## 🛣️ Routes

### 📄 routes/index.js

```js
const express = require('express');
const router = express.Router();
const { homePage } = require('../controllers/homeController');

router.get('/', homePage);

module.exports = router;
```

---

### 📄 routes/about.js

```js
const express = require('express');
const router = express.Router();
const { aboutPage } = require('../controllers/aboutController');

router.get('/', aboutPage);

module.exports = router;
```

---

## 🎮 Controllers

### 📄 controllers/homeController.js

```js
exports.homePage = (req, res) => {
  res.render('pages/home', { title: 'Home' });
};
```

---

### 📄 controllers/aboutController.js

```js
exports.aboutPage = (req, res) => {
  res.render('pages/about', { title: 'About' });
};
```

---

## 🎨 Public Assets

Example CSS file:

### 📄 public/css/style.css

```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

nav a {
  margin-right: 1rem;
}
```

---

## 🧠 Notes & Best Practices

✔ Use **layout.ejs** to avoid repetition
✔ Group pages inside `views/pages/`
✔ Use controllers for cleaner logic separation
✔ Serve static files from `/public`
✔ Use partials for header, footer, nav
✔ Always render full pages using layout → partials → content
✔ Keep routes simple and readable

---

## 🚀 Startup

```bash
npm install
npm run dev
```

Visit:
👉 [http://localhost:3000](http://localhost:3000)
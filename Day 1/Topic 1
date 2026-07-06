# 🚀 Server Configuration

## 📌 Objective

In this section, we will configure the backend server for the Grocery Store MERN application. This includes creating the project structure, initializing a Node.js project, installing the required dependencies, creating the first Express server, and configuring Nodemon for automatic server restarts during development.

---

## 📋 Prerequisites

Before getting started, install the following:

- Node.js
- npm (Node Package Manager)

Verify the installation:

```bash
node -v
npm -v
```

If both commands display version numbers, your environment is ready.

---

## 📁 Project Structure

Create a main project folder named **Grocery-Store**.

Inside it, create two subfolders:

```text
Grocery-Store/
├── backend/
└── frontend/
```

### Folder Description

- **backend/** – Contains the server-side code, APIs, and database logic.
- **frontend/** – Contains the React application.

---

## 📂 Navigate to the Backend Folder

Open the terminal and move into the backend directory.

```bash
cd backend
```

---

## 📦 Initialize the Node.js Project

Run the following command:

```bash
npm init -y
```

### What happens?

- A `package.json` file is created.
- A `package-lock.json` file is created.
- Your Node.js project is initialized.

The folder structure becomes:

```text
backend/
├── package.json
└── package-lock.json
```

---

## 📥 Install Required Packages

Install the required dependencies:

```bash
npm install express mongoose nodemon cors jsonwebtoken
```

### Installed Packages

| Package | Purpose |
|----------|---------|
| Express | Creates the backend server and APIs |
| Mongoose | Connects Node.js with MongoDB |
| Nodemon | Automatically restarts the server during development |
| CORS | Enables communication between frontend and backend |
| jsonwebtoken (JWT) | Used for authentication and authorization |

After installation, the folder structure becomes:

```text
backend/
├── node_modules/
├── package.json
└── package-lock.json
```

The `package.json` file is automatically updated with all installed package versions.

---

## 📄 Create the Server File

Inside the `backend` folder, create a new file:

```text
server.js
```

This file acts as the entry point of the backend application.

---

## 📌 Import Express

### Using ES Modules

```javascript
import express from "express";
```

> Use this syntax when `"type": "module"` is added to `package.json`.

### Using CommonJS (Preferred in this Project)

```javascript
const express = require("express");
```

---

## 🖥️ Create the Express Server

Add the following code to `server.js`.

```javascript
const express = require("express");

const app = express();

const PORT = 8000;

app.listen(PORT, () => {
    console.log(`Server running at ${PORT}`);
});
```

### Explanation

- `require("express")` imports the Express framework.
- `express()` creates an Express application.
- `PORT` stores the port number.
- `app.listen()` starts the server.
- `console.log()` displays a message when the server starts successfully.

---

## ▶️ Run the Server

Execute the following command:

```bash
node server.js
```

### Output

```text
Server running at 8000
```

The backend server is now running successfully.

---

## ⚠️ Problem

Whenever changes are made to `server.js`, the server must be stopped and started again using:

```bash
node server.js
```

This is inefficient during development.

---

## 🔄 Configure Nodemon

Open `package.json` and update the `"scripts"` section:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "nodemon server.js"
}
```

---

## ▶️ Start the Server with Nodemon

Run:

```bash
npm start
```

### Output

```text
[nodemon] starting `node server.js`
Server running at 8000
```

Now, every time you save `server.js`, Nodemon automatically restarts the server.

---

## 📂 Final Backend Structure

```text
backend/
├── node_modules/
├── package-lock.json
├── package.json
└── server.js
```

---

## 📚 Concepts Learned

- Node.js project initialization
- Purpose of `package.json`
- Purpose of `package-lock.json`
- Installing npm packages
- Understanding the `node_modules` folder
- Creating an Express server
- Difference between CommonJS and ES Modules
- Running a Node.js application
- Configuring Nodemon
- Using npm scripts

---

## ✅ Summary

In this section, the backend environment for the Grocery Store MERN application was successfully configured. A Node.js project was initialized, the required dependencies were installed, an Express server was created, and Nodemon was configured to automatically restart the server whenever changes are made during development.

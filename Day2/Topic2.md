# 🍃 MongoDB Database Connection

## 📌 Objective

The objective of this section is to connect the Express backend application to a MongoDB database using **MongoDB Atlas**, **Mongoose**, and **Environment Variables (.env)**. This approach keeps sensitive information, such as the database connection string, secure and makes the application easier to maintain.

---

# 📋 Prerequisites

Before connecting the database, ensure you have:

* Node.js installed
* npm installed
* Express server configured
* A MongoDB Atlas account

---

# ☁️ Step 1: Create a MongoDB Atlas Account

1. Visit the MongoDB Atlas website.
2. Sign in using your Google account.
3. Create a new MongoDB Atlas account if you don't already have one.

---

# 📁 Step 2: Create a New Project

After logging in:

* Click **Projects**.
* Select **View All Projects**.
* Click **Create Project**.
* Enter a project name.
* Click **Create**.

---

# 🗄️ Step 3: Create a Database Cluster

Inside the newly created project:

1. Click **Build a Database**.
2. Choose the **Free (M0)** cluster.
3. Select your preferred cloud provider and region.
4. Click **Create Cluster**.

---

# 👤 Step 4: Create a Database User

Navigate to **Database Access**.

Create a new database user by providing:

* Username
* Password

Save these credentials, as they will be required while connecting the application.

---

# 🔗 Step 5: Obtain the Connection String

1. Open your cluster.
2. Click **Connect**.
3. Select **Drivers**.
4. Choose **Node.js** as the driver.
5. Copy the generated connection string.

Example:

```text
mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/
```

Replace:

* `<username>` with your database username.
* `<password>` with your database password.

---

# 🔐 Step 6: Create an Environment File

Inside the **backend** folder, create a new file named:

```text
.env
```

Store the connection string as an environment variable.

```env
MONGO_URL=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/
```

## Why use a `.env` file?

* Keeps sensitive information secure.
* Prevents database credentials from being hardcoded.
* Makes configuration easier across different environments.

---

# 📦 Step 7: Install Required Packages

Install **dotenv** if it is not already installed.

```bash
npm install dotenv
```

The package will automatically be added to the dependencies listed in `package.json`.

---

# 📥 Step 8: Import Required Modules

Open `server.js` and import the required modules.

```javascript
const express = require("express");
const dotenv = require("dotenv");
const mongoose = require("mongoose");
```

Load the environment variables.

```javascript
dotenv.config();
```

---

# ✅ Step 9: Verify the Environment Variable

Before connecting to MongoDB, verify that the connection string is being loaded correctly.

```javascript
console.log("Checking MongoDB URL:", process.env.MONGO_URL);
```

### Expected Output

```text
Checking MongoDB URL: mongodb+srv://...
```

If the URL is displayed, the `.env` file has been configured successfully.

---

# 🔗 Step 10: Connect to MongoDB

Use Mongoose to establish the database connection.

```javascript
mongoose
  .connect(process.env.MONGO_URL)
  .then(() => {
    console.log("Database connected successfully.");
  })
  .catch((error) => {
    console.log(error.message);
  });
```

### Explanation

* `mongoose.connect()` establishes a connection with MongoDB Atlas.
* `.then()` executes when the connection is successful.
* `.catch()` handles any connection errors.

---

# ▶️ Run the Server

Start the backend server.

```bash
npm start
```

### Expected Output

```text
Server running at 8000
Database connected successfully.
```

---

# ⚠️ Common Errors and Solutions

## 1️⃣ IP Whitelist Error

### Cause

MongoDB Atlas blocks connections from unknown IP addresses.

### Solution

1. Open your MongoDB Atlas project.
2. Navigate to **Network Access**.
3. Click **Add IP Address**.
4. Choose **Add Current IP Address** or manually enter:

```text
0.0.0.0/0
```

5. Save the changes.
6. Wait a few minutes for the configuration to update.

> **Note:** Allowing `0.0.0.0/0` permits connections from any IP address. This is convenient during development but should be restricted in production.

---

## 2️⃣ `querySrv ECONNREFUSED` Error

### Cause

This error usually occurs because the system cannot resolve MongoDB Atlas DNS records.

### Solution

Update your preferred DNS servers.

For example:

* Primary DNS: `1.1.1.1`
* Secondary DNS: `8.8.8.8`

You can also configure DNS programmatically before establishing the database connection.

```javascript
const dns = require("dns");

dns.setServers(["1.1.1.1", "8.8.8.8"]);
```

Place this code before calling `mongoose.connect()`.

---

# 📂 Backend Structure

```text
backend/
├── node_modules/
├── .env
├── package.json
├── package-lock.json
└── server.js
```

---

# 📚 Concepts Learned

* MongoDB Atlas
* Cloud Database
* Database Cluster
* Database User
* Connection String
* Environment Variables
* `.env` file
* `dotenv`
* `process.env`
* Mongoose
* Database Connectivity
* Promise Handling using `.then()` and `.catch()`
* Common MongoDB Connection Errors

---
## 📄 Complete `server.js` File

```javascript
const express = require("express");
const mongoose = require("mongoose");
const dotenv = require("dotenv");
const dns = require("dns");

// Load environment variables
dotenv.config();

// Set DNS servers (Useful if querySrv ECONNREFUSED occurs)
dns.setServers(["1.1.1.1", "8.8.8.8"]);

const app = express();

const PORT = 8000;

// Connect to MongoDB
mongoose
  .connect(process.env.MONGO_URL)
  .then(() => {
    console.log("✅ Database connected successfully.");
  })
  .catch((error) => {
    console.log("❌ Database Connection Failed");
    console.log(error.message);
  });

// Start Express Server
app.listen(PORT, () => {
  console.log(`🚀 Server running at http://localhost:${PORT}`);
});
```

---

## 📄 Complete `.env` File

```env
MONGO_URL=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/
```

> **Note:** Never commit your actual `.env` file to GitHub. Replace your username and password with placeholders before pushing the repository.

---

## 📂 Final Backend Structure

```text
backend/
├── node_modules/
├── .env
├── package.json
├── package-lock.json
└── server.js
```

# ✅ Summary

In this section, the backend application was successfully connected to a MongoDB Atlas database using **Mongoose**. Sensitive credentials were stored securely in a `.env` file, environment variables were loaded using **dotenv**, and the database connection was established using `mongoose.connect()`. Finally, common connection issues such as IP whitelist restrictions and DNS resolution errors were identified and resolved, resulting in a successful connection between the Express server and MongoDB.


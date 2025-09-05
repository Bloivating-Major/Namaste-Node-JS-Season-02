# 📝 Homework — Episode 6: Database, Schema & Models

---

## 1. 🌐 Connect to MongoDB Cluster

- Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and create a free cluster.
- Get your connection string (e.g., `mongodb+srv://<username>:<password>@cluster0.mongodb.net/devtinder?retryWrites=true&w=majority`).

---

## 2. 📦 Install Mongoose Library

```sh
npm install mongoose
```

---

## 3. 🔗 Connect Your Application to the Database

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 06 Database, Schema & Models\src\db.js
const mongoose = require('mongoose');

const connectDB = async () => {
  try {
    await mongoose.connect('your-mongodb-connection-string');
    console.log('MongoDB connected!');
  } catch (err) {
    console.error('DB connection error:', err);
    process.exit(1);
  }
};

module.exports = connectDB;
```

---

## 4. 🚦 Call connectDB Before Starting Server

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 06 Database, Schema & Models\src\app.js
const express = require('express');
const connectDB = require('./db');
const app = express();

app.use(express.json());

connectDB().then(() => {
  app.listen(7777, () => {
    console.log('Server running on port 7777');
  });
});
```

---

## 5. 📁 Models Folder — `user.js`

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 06 Database, Schema & Models\src\models\user.js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  firstName: String,
  lastName: String,
  email: { type: String, unique: true },
  password: String,
  age: Number,
  gender: String
});

const User = mongoose.model('User', userSchema);

module.exports = User;
```

---

## 6. 🚀 Create POST `/signup` API

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 06 Database, Schema & Models\src\app.js
const User = require('./models/user');

app.post('/signup', async (req, res) => {
  try {
    const user = new User(req.body);
    await user.save();
    res.status(201).send({ message: 'User created!', user });
  } catch (err) {
    res.status(400).send({ error: err.message });
  }
});
```

---

## 7. 🧪 Push Documents Using Postman

- Open Postman.
- Send a `POST` request to `http://localhost:7777/signup` with JSON body:
  ```json
  {
    "firstName": "Sam",
    "lastName": "Bhav",
    "email": "sam@example.com",
    "password": "securepass",
    "age": 25,
    "gender": "male"
  }
  ```

---

## 8. ⚠️ Error Handling with Try-Catch

- Already implemented in the `/signup` API above.
- Ensures errors are caught and a proper response is sent.

---

🎉 Homework complete! You’ve connected MongoDB, created a schema/model, built an API, and tested it with
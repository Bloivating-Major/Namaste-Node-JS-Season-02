# 📝 Homework — Episode 8: Data Sanitization & Schema Validation

---

## 1. 📚 Explore SchemaType Options

- Use Mongoose schema options like `required`, `unique`, `lowercase`, `min`, `minLength`, `trim`, and `default`.

---

## 2. 🧬 Improved User Schema Example

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 08 Data Sanitization & Schema Validation\src\models\user.js
const mongoose = require('mongoose');
const validator = require('validator');

const userSchema = new mongoose.Schema({
  firstName: {
    type: String,
    required: true,
    trim: true,
    minLength: 2
  },
  lastName: {
    type: String,
    required: true,
    trim: true,
    minLength: 2
  },
  email: {
    type: String,
    required: true,
    unique: true,
    lowercase: true,
    trim: true,
    validate: [validator.isEmail, 'Invalid email']
  },
  password: {
    type: String,
    required: true,
    minLength: 8,
    validate: [validator.isStrongPassword, 'Password not strong enough']
  },
  age: {
    type: Number,
    min: 18,
    max: 100,
    default: 18
  },
  gender: {
    type: String,
    required: true,
    trim: true,
    validate: {
      validator: function (v) {
        return ['male', 'female', 'other'].includes(v.toLowerCase());
      },
      message: props => `${props.value} is not a valid gender`
    }
  },
  photoURL: {
    type: String,
    trim: true,
    validate: [validator.isURL, 'Invalid URL']
  }
}, { timestamps: true });
```

---

## 3. 🕒 Add Timestamps

- `{ timestamps: true }` in schema options automatically adds `createdAt` and `updatedAt` fields.

---

## 4. 🛡️ API Level Validation (Signup & Patch)

```javascript
// filepath: c:\Users\Sambhav\Desktop\Projects\Namaste Node Js Season 2\Episode 08 Data Sanitization & Schema Validation\src\app.js
const express = require('express');
const User = require('./models/user');
const validator = require('validator');
const app = express();

app.use(express.json());

// Signup API with validation
app.post('/signup', async (req, res) => {
  const { firstName, lastName, email, password, age, gender, photoURL } = req.body;

  // API-level validation
  if (!firstName || firstName.length < 2) return res.status(400).send('First name required and must be at least 2 chars');
  if (!lastName || lastName.length < 2) return res.status(400).send('Last name required and must be at least 2 chars');
  if (!email || !validator.isEmail(email)) return res.status(400).send('Valid email required');
  if (!password || !validator.isStrongPassword(password)) return res.status(400).send('Password not strong enough');
  if (!gender || !['male', 'female', 'other'].includes(gender.toLowerCase())) return res.status(400).send('Invalid gender');
  if (photoURL && !validator.isURL(photoURL)) return res.status(400).send('Invalid photo URL');
  if (age && (age < 18 || age > 100)) return res.status(400).send('Age must be between 18 and 100');

  try {
    const user = new User(req.body);
    await user.save();
    res.status(201).send('User registered');
  } catch (error) {
    res.status(400).send(error.message);
  }
});

// Patch API with validation
app.patch('/user/:id', async (req, res) => {
  const { firstName, lastName, email, password, age, gender, photoURL } = req.body;

  // API-level validation (only for fields present)
  if (firstName && firstName.length < 2) return res.status(400).send('First name must be at least 2 chars');
  if (lastName && lastName.length < 2) return res.status(400).send('Last name must be at least 2 chars');
  if (email && !validator.isEmail(email)) return res.status(400).send('Valid email required');
  if (password && !validator.isStrongPassword(password)) return res.status(400).send('Password not strong enough');
  if (gender && !['male', 'female', 'other'].includes(gender.toLowerCase())) return res.status(400).send('Invalid gender');
  if (photoURL && !validator.isURL(photoURL)) return res.status(400).send('Invalid photo URL');
  if (age && (age < 18 || age > 100)) return res.status(400).send('Age must be between 18 and 100');

  try {
    const user = await User.findByIdAndUpdate(req.params.id, req.body, { new: true, runValidators: true });
    if (!user) return res.status(404).send('User not found');
    res.status(200).json(user);
  } catch (error) {
    res.status(400).send(error.message);
  }
});
```

---

## 5. 🧹 Data Sanitizing

- Use `trim`, `lowercase`, and validation functions in both schema and API level to sanitize incoming data.

---

## 6. 📦 Install Validator

```sh
npm install validator
```

---

## 7. 🔍 Explore Validator Library Functions

- Use `validator.isEmail(email)`, `validator.isStrongPassword(password)`, `validator.isURL(photoURL)` for validation in APIs and schema.

---

🎉 Homework complete! You’ve explored schema options, improved validation, sanitized data, and secured your APIs. Keep practicing and refining your skills!
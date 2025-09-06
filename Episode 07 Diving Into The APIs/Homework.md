# 📝 Homework — Episode 7: Diving Into The APIs

---

## 1. 🟦 JS Object vs JSON (Difference)

- **JS Object**: Key-value pairs, can contain functions, undefined, and other JS types.
- **JSON**: String format, only supports data types (string, number, boolean, array, object, null), no functions or undefined.

---

## 2. 🛡️ Add the express.json Middleware

```javascript
app.use(express.json());
```
- This middleware parses incoming JSON requests and makes the data available in `req.body`.

---

## 3. 📝 Make Signup API Dynamic

- Accept user data from the request body and create a new user in the database.

```javascript
app.post('/signup', async (req, res) => {
    const user = new User(req.body);
    try {
        await user.save();
        res.status(201).send('User registered');
    } catch (error) {
        res.status(400).send('Error registering user');
    }
});
```

---

## 4. 🔍 User.findOne with Duplicate Email IDs

- `User.findOne({ email })` returns the **first matching document** found in the database.
- If multiple users have the same email (should be unique!), only the first one is returned.

---

## 5. 📧 API - Get User by Email

```javascript
app.get('/user', async (req, res) => {
    const email = req.body.email;
    try {
        const user = await User.findOne({ email });
        // Or use find to get all users with that email:
        // const user = await User.find({ email });
        if (!user || user.length === 0) {
            return res.status(404).send('User not found');
        }
        res.status(200).json(user);
    } catch (error) {
        res.status(404).send('User not found');
    }
});
```

---

## 6. 📰 API - Feed API - GET /feed

```javascript
app.get('/feed', async (req, res) => {
    try {
        const users = await User.find();
        res.status(200).json(users);
    } catch (err) {
        res.status(404).send('Something went wrong');
    }
});
```

---

## 7. 🆔 API - Get User by ID

- You can add a route like:
```javascript
app.get('/user/:id', async (req, res) => {
    try {
        const user = await User.findById(req.params.id);
        if (!user) return res.status(404).send('User not found');
        res.status(200).json(user);
    } catch (error) {
        res.status(404).send('User not found');
    }
});
```

---

## 8. 🗑️ Create a Delete User API

```javascript
app.delete('/user', async (req, res) => {
    const userId = req.body.userId;
    try {
        const user = await User.findByIdAndDelete(userId);
        if (!user) {
            return res.status(404).send('User not found');
        }
        res.status(200).send('User deleted');
    } catch (error) {
        res.status(500).send('Error deleting user');
    }
});
```

---

## 9. 🔄 Difference Between PATCH and PUT

- **PUT**: Replaces the entire document.
- **PATCH**: Updates only the specified fields.

---

## 10. 🛠️ API - Update a User

```javascript
app.patch('/user', async (req, res) => {
    const userId = req.body.userId;
    const data = req.body;
    try {
        const user = await User.findByIdAndUpdate(userId, data);
        if (!user) {
            return res.status(404).send('User not found');
        }
        res.status(200).send('User updated');
    } catch (error) {
        res.status(500).send('Error updating user');
    }
});
```

---

## 11. 📚 Explore the Mongoose Documentation for Model Methods

- Useful methods: `find`, `findOne`, `findById`, `findByIdAndUpdate`, `findByIdAndDelete`, `save`, etc.
- [Mongoose Model Docs](https://mongoosejs.com/docs/models.html)

---

## 12. ⚙️ Options in Model.findOneAndUpdate

- `new`: Returns the updated document.
- `upsert`: Creates a new document if none matches.
- `runValidators`: Runs schema validation.
- More options: [findOneAndUpdate Options](https://mongoosejs.com/docs/api/model.html#Model.findOneAndUpdate)

---

## 13. 📧 API - Update the User with Email ID

- You can add a route like:
```javascript
app.patch('/user/email', async (req, res) => {
    const email = req.body.email;
    const data = req.body;
    try {
        const user = await User.findOneAndUpdate({ email }, data, { new: true });
        if (!user) {
            return res.status(404).send('User not found');
        }
        res.status(200).json(user);
    } catch (error) {
        res.status(500).send('Error updating user');
    }
});
```

---

## 💡 Summary

- You learned the difference between JS objects and JSON.
- Added `express.json` middleware for parsing JSON requests.
- Built dynamic and robust user APIs: signup, get by email/ID, feed, delete, and update.
- Explored Mongoose model methods and update options.
- Practiced error handling and response management.

---

🎉 Homework complete! You’ve mastered CRUD APIs and
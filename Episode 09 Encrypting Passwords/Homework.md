# 📝 Homework — Episode 9: Encrypting Passwords

---

## 1. ✅ Validate Data in Signup API

- Use a helper function or inline checks to ensure all required fields are present and valid before proceeding.

```javascript
function validateSignupData({ firstName, lastName, email, password }) {
  if (!firstName || !lastName || !email || !password) return false;
  // Add more checks as needed (e.g., email format, password strength)
  return true;
}
```

---

## 2. 📦 Install bcrypt Package

```sh
npm install bcrypt
```

---

## 3. 🔒 Create Password Hash Using bcrypt.hash & Save User with Encrypted Password

```javascript
const bcrypt = require('bcrypt');

app.post('/signup', async (req, res) => {
  const { firstName, lastName, email, password } = req.body;
  if (!validateSignupData(req.body)) return res.status(400).send('Invalid signup data');

  try {
    const hashedPassword = await bcrypt.hash(password, 10);
    const user = new User({ firstName, lastName, email, password: hashedPassword });
    await user.save();
    res.status(201).send('User registered');
  } catch (error) {
    res.status(400).send('Error registering user');
  }
});
```

---

## 4. 🛡️ Create Login API

```javascript
app.post('/login', async (req, res) => {
  const { email, password } = req.body;
  if (!email || !password) return res.status(400).send('Email and password required');

  try {
    const user = await User.findOne({ email });
    if (!user) return res.status(401).send('Invalid email or password');

    const isMatch = await bcrypt.compare(password, user.password);
    if (!isMatch) return res.status(401).send('Invalid email or password');

    // Never return password in response!
    const { password: _, ...userData } = user.toObject();
    res.status(200).json({ message: 'Login successful', user: userData });
  } catch (error) {
    res.status(500).send('Error logging in');
  }
});
```

---

## 5. 🚨 Compare Passwords and Throw Errors if Email or Password is Invalid

- Already handled in the login API above using `bcrypt.compare` and proper error responses.

---

🎉 Homework complete! You now have secure signup and login flows with password encryption and validation.
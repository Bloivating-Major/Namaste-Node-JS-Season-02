# Episode 9: **Encrypting Passwords** 🔒

> "Passwords are secrets—protect them like treasure."  
> — Inspired by Namaste Node.js S2

---

## 🌟 **What Did I Learn Today?**

- Passwords are highly sensitive and must never be stored in plain text.
- The safe flow for user signup:
  1. **Validate Data in API:**  
     Use a helper function to check all required fields and data formats.
  2. **Encrypt Password Using Bcrypt:**  
     Hash the password before saving it to the database.
  3. **Save User in DB:**  
     Store the user with the encrypted password.

- This approach ensures passwords are never exposed, even if the database is compromised.

---

## 🛡️ **Login API Flow**

1. Receive `email` and `password` from the request body.
2. Check if both fields are provided—if not, throw an error.
3. Find the user by email in the database.
4. If user not found, throw an error.
5. If user found, compare the provided password with the hashed password using `bcrypt.compare`.
6. If passwords do not match, throw an error.
7. If passwords match, send a success response with user details (excluding the password).

---

## 💡 **Best Practices**

- **Always validate input data** using helper functions.
- **Never store plain text passwords**—always hash them with a strong algorithm like bcrypt.
- **Never return passwords** in API responses.
- **Handle errors gracefully** and send clear messages to the client.

---

Let’s keep our users safe and our authentication secure! 🛡️🚀
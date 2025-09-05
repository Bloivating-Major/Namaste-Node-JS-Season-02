# Episode 6: **Database, Schema & Models** 🗄️

> "A solid database foundation powers every great app."  
> — Inspired by Namaste Node.js S2

---

## 🌟 **What Did I Learn Today?**

- Connected MongoDB to my Node.js app using **Mongoose**.
- Designed a **User Schema** and created a **User Model** for the database.
- Built a **signup API** to add new users to the database.
- Tested the API using **Postman**.
- Implemented **error handling** with `try-catch` blocks.
- Practiced using **async/await** for asynchronous operations.

---

## 🔗 **Database Connection**

- Used Mongoose to connect to a local MongoDB instance (`devtinder` database).
- Ensured the server only starts after a successful database connection.

---

## 🧬 **User Schema & Model**

- Defined a schema for user data:  
  - `firstName`, `lastName`, `email`, `password`, `age`, `gender`
- Created a Mongoose model to interact with the `users` collection.

---

## 🚀 **Signup API**

- Built a `POST /signup` endpoint to register new users.
- Used async/await for database operations.
- Handled errors gracefully and sent appropriate responses.

---

## 🧪 **Testing**

- Verified the signup API using Postman to ensure users are added to the database.

---

## 💡 **Key Takeaways**

- Always handle database connections and errors properly.
- Use schemas and models to structure and validate data.
- Async/await makes asynchronous code cleaner and easier to manage.
- Postman is a great tool for testing APIs.

---

## 🏋️‍♂️ **Homework & Practice**

[Homework](./Homework.md)

Let’s keep building robust backends!
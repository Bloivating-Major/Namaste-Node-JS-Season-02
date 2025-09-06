# Episode 7: **Diving Into The APIs** 🌊

> "APIs are the bridges between your app and the world."  
> — Inspired by Namaste Node.js S2

---

## 🌟 **What Did I Learn Today?**

- Explored the difference between JS Objects and JSON.
- Used `express.json()` middleware to parse incoming JSON requests.
- Built dynamic APIs for user signup, fetching users, updating, and deleting users.
- Practiced CRUD operations using Mongoose with MongoDB.
- Handled errors gracefully in all API endpoints.

---

## 🛠️ **APIs Implemented**

### 1. **User Signup**
- `POST /signup`  
  Registers a new user using data from the request body.

### 2. **Get All Users (Feed)**
- `GET /feed`  
  Fetches all users from the database.

### 3. **Get User by Email**
- `GET /user`  
  Finds a user by email provided in the request body.

### 4. **Get User by ID**
- `GET /user/:id`  
  Finds a user by their unique ID.

### 5. **Delete User by ID**
- `DELETE /user`  
  Deletes a user using the user ID from the request body.

### 6. **Update User by ID**
- `PATCH /user`  
  Updates user details using the user ID and new data from the request body.

### 7. **Update User by Email**
- `PATCH /user/email`  
  Updates user details using the email and new data from the request body.

---

## 💡 **Key Concepts**

- **JS Object vs JSON:**  
  JS Objects can have functions and undefined; JSON is a string format for data exchange.

- **express.json Middleware:**  
  Parses incoming JSON requests and makes data available in `req.body`.

- **CRUD Operations:**  
  Create, Read, Update, Delete users using Mongoose methods.

- **Error Handling:**  
  Used try-catch blocks to manage errors and send appropriate responses.

- **Mongoose Model Methods:**  
  Utilized `find`, `findOne`, `findById`, `findByIdAndUpdate`, `findByIdAndDelete`, and `save`.

---

## 📚 **Resources**

- [Mongoose Model Docs](https://mongoosejs.com/docs/models.html)
- [Express.js Documentation](https://expressjs.com/)

---

Let’s keep building powerful APIs and connecting our apps to the world!
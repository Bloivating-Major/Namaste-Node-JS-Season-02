# 📝 Homework — Episode 5: Middlewares & Route Handlers

---

## 1. 🔄 Multiple Route Handlers — Play with the Code

```javascript
app.use('/user', rh1, rh2, rh3, rh4, rh5);
// Each handler (rh1, rh2, ...) can be a middleware or route handler function.
```

Example:
```javascript
const rh1 = (req, res, next) => { console.log('rh1'); next(); };
const rh2 = (req, res, next) => { console.log('rh2'); next(); };
const rh3 = (req, res, next) => { console.log('rh3'); next(); };
const rh4 = (req, res, next) => { console.log('rh4'); next(); };
const rh5 = (req, res) => { res.send('All handlers executed!'); };

app.use('/user', rh1, rh2, rh3, rh4, rh5);
```

---

## 2. ➡️ `next()`

- `next()` passes control to the next middleware or route handler.
- If you call `next()` after sending a response, Express will throw an error.

Example:
```javascript
app.get('/test', (req, res, next) => {
  res.send('Hello!');
  next(); // This will cause an error because response is already sent.
});
```

---

## 3. ⚠️ `next` Function and Errors with `res.send()`

- If you call `next(err)`, Express will skip all remaining non-error middlewares and go to error-handling middleware.

Example:
```javascript
app.get('/error', (req, res, next) => {
  next(new Error('Something went wrong!'));
});

app.use((err, req, res, next) => {
  res.status(500).send({ error: err.message });
});
```

---

## 4. 🧩 `app.use('/user', rh1, rh2, rh3, rh4, rh5);`

- This chains multiple middlewares for the `/user` route.
- Each handler can process the request and pass it along using `next()`.

---

## 5. ❓ What is Middleware? Why Do We Need Them?

- **Middleware** is a function that has access to `req`, `res`, and `next`.
- Used for logging, authentication, parsing, error handling, etc.
- They help modularize and reuse logic across routes.

---

## 6. ⚙️ How Express Handles Requests Behind the Scenes

- Express maintains a stack of middlewares and route handlers.
- When a request comes in, it passes through each middleware in order.
- Each middleware can end the cycle (send response) or pass control (`next()`).

---

## 7. 🔀 `app.use` vs `app.all`

- `app.use`: Matches all HTTP methods and paths (optionally with a prefix).
- `app.all`: Matches all HTTP methods for a specific path.

Example:
```javascript
app.use('/user', middleware); // All methods, all paths starting with /user
app.all('/user', handler);    // All methods, only /user path
```

---

## 8. 🔒 Dummy Auth Middleware for Admin

```javascript
const adminAuth = (req, res, next) => {
  if (req.headers['x-admin'] === 'true') {
    next();
  } else {
    res.status(403).send('Forbidden: Admins only');
  }
};

app.use('/admin', adminAuth, (req, res) => {
  res.send('Welcome, Admin!');
});
```

---

## 9. 👤 Dummy Auth Middleware for User Except `/user/login`

```javascript
const userAuth = (req, res, next) => {
  if (req.path === '/login') return next();
  if (req.headers['x-user'] === 'true') {
    next();
  } else {
    res.status(401).send('Unauthorized: Users only');
  }
};

app.use('/user', userAuth);
app.post('/user/login', (req, res) => {
  res.send('Login route, no auth required');
});
```

---

## 10. 🛑 Error Handling Middleware Using Wildcard Route (`app.use`)

```javascript
app.use((err, req, res, next) => {
  res.status(500).send({ error: err.message || 'Unknown error' });
});
```

---

🎉 Homework complete! You now understand middlewares, route handlers, and error handling in Express.
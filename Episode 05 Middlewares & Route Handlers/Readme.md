# Episode 5: **Middlewares & Route Handlers** 🛡️

> "Middleware is the heart of Express. It decides how your requests flow."  
> — Inspired by Namaste Node.js S2

---

## 🌐 **How Requests Flow in Express**

- When a request reaches your Express server, it passes through a chain of **middlewares** and **route handlers**.
- If you **don’t handle the request** (i.e., don’t send a response), the request will hang and eventually time out.
- If you **send a response** (e.g., using `res.send()`), the request is considered complete and no further middleware or handler will run for that request.

---

## 🔄 **The Role of `next()`**

- Calling `next()` passes control to the **next middleware or route handler** in the stack.
- If you call `next()` and then `res.send()`, Express will throw an error because the response has already been sent.  
  - The next middleware executes, and when it returns, Express tries to send another response, causing an error.
- **Best Practice:** Only call `next()` if you haven’t sent a response yet.

---

## 🚦 **Skipping Middlewares with `next('route')`**

- Using `next('route')` tells Express to **skip all remaining middlewares and handlers** for the current route and move directly to the next matching route handler.
- This is useful for conditional logic, such as authentication or permission checks.

---

## 🛑 **Error Handlers**

- Error-handling middleware in Express has four arguments: `(err, req, res, next)`.
- If an error occurs, you can pass it to the error handler using `next(err)`.
- Error handlers allow you to send custom error responses and log issues.

---

## 💡 **Key Takeaways**

- Middleware functions can either end the request-response cycle or pass control using `next()`.
- Never call `next()` after sending a response.
- Use `next('route')` to skip to the next route handler, bypassing remaining middlewares.
- Implement error handlers to gracefully manage errors in your application.

---

## 🏋️‍♂️ **Homework & Practice**

[Homework](./Homework.md)

Let’s keep mastering Express and building smarter APIs!
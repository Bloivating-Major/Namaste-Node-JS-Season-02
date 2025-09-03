# Episode 4: **Routing and Request Handlers** 🛣️

> "The right route leads to the right results."  
> — Inspired by Namaste Node.js S2

---

## 🚫 **Best Practices**

- **Never push your `node_modules` folder** to the repository.
- Create a `.gitignore` file to ignore `node_modules` and other unnecessary files.
- Always push `package.json` and `package-lock.json` — they help others install the exact dependencies.

---

## 🌐 **Routing in Express**

- **Why were routes not working?**  
  The `use` function acts as a wildcard. If used at the default route, it matches all routes.

---

## 🔥 **HTTP Methods**

- By default, hitting any URL sends a **GET** request.
- Use **Postman** to test your APIs.

### **Common Methods**
- **GET**: Handles only GET requests.
- **POST**: Handles only POST requests.
- **USE**: Handles all types of requests.

---

## 🧩 **Advanced Routing Techniques**

- `+` : `/ab+c` matches `/ac`, `/abc`, `/abbc`, `/abbbc`
- `?` : `/ab?c` matches `/abc`, `/ac`
- `*` : `/ab*c` matches `/ac`, `/abc`, `/abbc`, `/abbbc`
- `()` : `/a(bc)?d` matches `/ad`, `/abcd`
- You can use **regex** in your routes, e.g., `/.*fly$/` matches `/butterfly`, `/dragonfly`

---

## 🔍 **Request Data**

- `req.query` — Read query parameters from the URL.
- `req.params` — Read dynamic route parameters.

---

## 💡 **Key Takeaways**

- Order of routes matters!
- Use Postman for API testing and collections.
- Master GET, POST, PATCH, DELETE methods.
- Explore advanced routing and regex.
- Learn to read query params and dynamic routes.

---

## 📝 **Homework**

See [Homework.md](./Homework.md) for solutions and practical steps!

---

Let’s keep routing and exploring! 🚦
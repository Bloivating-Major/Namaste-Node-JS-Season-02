# Episode 8: **Data Sanitization & Schema Validation** 🧼

> "Clean data is the foundation of secure and reliable applications."  
> — Inspired by Namaste Node.js S2

---

## 🌟 **What Did I Learn Today?**

- Explored Mongoose schema options for robust data validation (`required`, `unique`, `minLength`, `trim`, `lowercase`, `default`, etc.).
- Used the **validator** library for advanced validation (email, password strength, URLs).
- Implemented API-level validation and data sanitization in signup and update routes.
- Added automatic timestamps to user documents for tracking creation and updates.
- Practiced error handling and sending meaningful responses.

---

## 🛡️ **Best Practices**

- **Validate at Both Levels:**  
  Use schema validation for structure and API-level validation for custom logic.
- **Sanitize Inputs:**  
  Always trim, lowercase, and validate incoming data before saving to the database.
- **Use Helper Functions:**  
  Create reusable helper functions for validation and sanitization to keep code DRY and maintainable.
- **Error Handling:**  
  Send clear error messages and use try-catch blocks in async routes.
- **Keep Schemas Strict:**  
  Define all fields with proper types and constraints to prevent bad data.

---

## 📝 **Homework Highlights**

- Improved the User schema with advanced options and custom validators.
- Added `{ timestamps: true }` to track `createdAt` and `updatedAt`.
- Used the **validator** library for email, password, and URL checks.
- Implemented API-level validation in `/signup` and `/user/:id` routes.
- Sanitized data using `trim`, `lowercase`, and validation functions.
- Installed and explored the validator library for robust checks.

---

## 💡 **Key Concepts**

- **Schema Validation:**  
  Ensures only valid data is stored in MongoDB.
- **Data Sanitization:**  
  Prevents injection attacks and keeps data consistent.
- **API-Level Checks:**  
  Protects endpoints from invalid or malicious requests.
- **Helper Functions:**  
  Centralize validation logic for reuse and clarity.

---

## 📚 **Resources**

- [Mongoose Schema Validation](https://mongoosejs.com/docs/validation.html)
- [Validator.js Documentation](https://github.com/validatorjs/validator.js)
- [Express.js Error Handling](https://expressjs.com/en/guide/error-handling.html)

---

Let’s keep our APIs clean, safe, and reliable! 🚀
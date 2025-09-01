# Episode 2: **Features, HLD, LLD & Planning**

> "A well-planned project is half built."  
> — Inspired by Namaste Node.js S2

---

## 🌟 **What Did I Learn Today?**

Today, I explored the importance of requirements gathering, feature definition, and the art of planning before writing any code. I learned how High-Level Design (HLD) and Low-Level Design (LLD) set the foundation for successful projects.

---

## 📝 **Feature List**

- Create an Account
- Login
- Update Profile
- Feed Page (Explore)
- Send Connection Request
- View Matches
- See Incoming Requests
- Update Profile (again, because it’s important!)

---

## 🗺️ **Project Planning**

**Microservices Approach:**

1. **Frontend Service:**  
   _Tech Stack:_ React, Redux, Tailwind

2. **Backend Service:**  
   _Tech Stack:_ Node.js, Express, MongoDB

> **Note:** If your planning is perfect, writing code becomes easy!

---

## 🏗️ **Low-Level Design (LLD)**

### **Database Design**

**User Collection**
- firstName
- lastName
- email
- password
- age
- gender

**Connection Collection**
- fromUserId
- toUserId
- status _(pending, accepted, rejected, ignored)_

---

### **API Design (REST)**

- `POST /signup`
- `POST /login`
- `GET /profile`
- `POST /profile`
- `PATCH /profile`
- `DELETE /profile`
- `POST /sendRequest`
- `POST /reviewRequest`
- `GET /request`
- `GET /connections`

---

## 💡 **Key Takeaways**

- Gather and analyze requirements before starting.
- Define features clearly.
- Plan your architecture (HLD & LLD) for smooth development.
- Good planning makes coding effortless!

---

Let’s keep building and designing smart! 🚀
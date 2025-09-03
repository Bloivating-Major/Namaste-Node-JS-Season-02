# 📝 Homework — Episode 4: Routing and Request Handlers

## 1. 🗂️ Initialize Git
```sh
git init
```

## 2. 📄 Add `.gitignore`
- Create a `.gitignore` file and add:
  ```
  node_modules/
  ```

## 3. 🌐 Create Remote Repo & Push Code
- On GitHub, create a new repository.
- Link and push your code:
  ```sh
  git remote add origin <your-repo-url>
  git add .
  git commit -m "Initial commit"
  git push -u origin main
  ```

## 4. 🛣️ Play with Routes & Extensions
- Create routes using `/test`, `/hello`, `/ab+c`, `/ab?c`, `/ab*c`, `/a(bc)?d`, and regex like `/.*fly$/`.

## 5. ⚡ Order of Routes
- Place specific routes before wildcard or generic routes to ensure correct matching.

## 6. 🧪 Install Postman & Test Routes
- Download [Postman](https://www.postman.com/downloads/).
- Create a collection and test all your routes.

## 7. 🔄 Handle GET, POST, PATCH, DELETE
- Example in Express:
  ````javascript
  app.get('/item', (req, res) => res.send('GET item'));
  app.post('/item', (req, res) => res.send('POST item'));
  app.patch('/item', (req, res) => res.send('PATCH item'));
  app.delete('/item', (req, res) => res.send('DELETE item'));

## 8. 🧩 Explore Routing Symbols & Regex
Try routes with ?, +, *, (), and regex.

// modify these according to readme

## 9. 🔍 Read Query Params
Example: /search?name=Sam
```javascript
app.get('/search', (req, res) => {
  res.send(req.query);
});
```

## 10. 🛤️ Read Dynamic Routes
Example: /user/:id
```javascript
app.get('/user/:id', (req, res) => {
  res.send(req.params);
});
```
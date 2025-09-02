# 📝 Homework — Episode 3: Creating our Express Server

## 🗂️ 1. Create a Repository  
- Initialize a new Git repository for your project:  
  ```
  git init
  ```

## 🏁 2. Initialize the Repository  
- Add your files and make your first commit:  
  ```
  git add .
  git commit -m "Initial commit"
  ```

## 📦 3. Understand `node_modules`, `package.json`, and `package-lock.json`  
- **node_modules**: Stores all installed dependencies.  
- **package.json**: Contains project metadata and lists dependencies.  
- **package-lock.json**: Locks the exact versions of installed dependencies for consistency.

## 🚀 4. Install Express  
- Add Express to your project:  
  ```
  npm install express
  ```

## 🖥️ 5. Create a Server  
- In `src/app.js`, set up a basic Express server.

## 🎧 6. Listen on Port 7777  
- Make your server listen on port `7777`:
  ````javascript
  app.listen(7777, () => {
    console.log('Server running on port 7777');
  });


## 🔄 7. Write Request Handlers for /test and /hello

```javascript
app.get('/test', (req, res) => res.send('Test route working!'));

app.get('/hello', (req, res) => res.send('Hello from Express!'));
```

## 🔥 8. Install Nodemon and Update Scripts

- Install Nodemon as a development dependency:
  ```
  npm install --save-dev nodemon
  ```

- Update the `scripts` section in `package.json`:
  ```json
  "scripts": {
    "start": "node src/app.js",
    "dev": "nodemon src/app.js"
  }
  ```

## 🔄 9. Learn the Use of the -g Flag for Global Package Installs

- The `-g` flag installs packages globally, making them accessible from anywhere.
- Example:
  ```
  npm install -g nodemon
  ```

## 🔄 10. Understand the Difference Between Caret (^) and Tilde (~) in package.json

- **Caret (^)**: Allows minor version updates. For example, `^1.2.3` can update to `1.2.x` but not `1.3.0`.
- **Tilde (~)**: Allows patch version updates. For example, `~1.2.3` can update to `1.2.4` but not `1.3.0`.
# Email-Verification

# Project Name

## 📌 Prerequisites

Make sure you have the following installed on your system:

- [XAMPP](https://www.apachefriends.org/index.html)
- [Git](https://git-scm.com/)
- A web browser (Chrome, Firefox, Edge, etc.)
- A Firebase project (for email authentication)

---

## 🚀 Setting Up the Website Using XAMPP

### 1️⃣ Clone the Repository

Open a terminal or command prompt and run:

```sh
cd C:/xampp/htdocs/
git clone https://github.com/Fable07/Email-Verification.git
cd your-repository
```

### 2️⃣ Start XAMPP

1. Open **XAMPP Control Panel**.
2. Start **Apache** and **MySQL**.

### 3️⃣ Configure the Database (if needed)

1. Open **phpMyAdmin** by visiting `http://localhost/phpmyadmin/`.
2. Create a new database (e.g., `my_database`).
3. Import the database from `database/my_database.sql` (if provided).

### 4️⃣ Run the Website

1. Open a browser and visit:
   ```
   http://localhost/your-repository
   ```
2. The website should now be running!

---

## 🔥 Setting Up Firebase for Email Verification

### 1️⃣ Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Click **Create a project** and follow the setup steps.
3. Go to **Authentication > Sign-in Method**.
4. Enable **Email/Password Sign-in**.

### 2️⃣ Add Firebase to the Website

1. In Firebase Console, go to **Project settings > General**.
2. Click **Add app > Web** and register the app.
3. Copy the Firebase configuration and update `firebase-config.js` in your project:
   ```js
   const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_PROJECT_ID.appspot.com",
       messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
       appId: "YOUR_APP_ID"
   };
   firebase.initializeApp(firebaseConfig);
   ```

### 3️⃣ Implement Email Verification

1. Use Firebase's authentication functions in `auth.js`:
   ```js
   firebase.auth().createUserWithEmailAndPassword(email, password)
       .then((userCredential) => {
           userCredential.user.sendEmailVerification()
               .then(() => {
                   alert("Verification email sent!");
               });
       })
       .catch((error) => {
           console.error("Error: ", error.message);
       });
   ```
2. Ensure the user verifies their email before logging in:
   ```js
   firebase.auth().onAuthStateChanged((user) => {
       if (user) {
           if (!user.emailVerified) {
               alert("Please verify your email before logging in.");
           }
       }
   });
   ```

### 4️⃣ Test Firebase Authentication

1. Try signing up with an email and password.
2. Check your inbox for a **verification email**.
3. Click the verification link and log in again.

---

## 🎯 Final Steps

- Ensure your website and Firebase integration work correctly.
- If deploying online, configure Firebase Authentication accordingly.


# 🧠 Course Management Backend App (Express + MongoDB + JWT)

This project is part of my backend learning journey with **Node.js**, **Express.js**, and **MongoDB**. It’s a complete RESTful API for a course-selling platform that implements **JWT-based authentication**, **role-based access control**, and full **CRUD operations** for admins and users.

I'm building this to practice and understand key concepts in backend development, while also making it easy for others to follow or reuse.

---

## 🚀 Features

- Admin & User authentication using JWT
- Persistent data storage with MongoDB
- Role-based route access
- Course creation, listing, and purchase flow
- Secure route protection via token headers

---

## 🔐 Authentication

All protected routes require JWT to be passed in the headers:

```
Authorization: Bearer <your-token>
```

---

## 📦 Tech Stack

- **Backend:** Node.js, Express.js
- **Database:** MongoDB (via Mongoose)
- **Authentication:** JWT (jsonwebtoken package)

---

## 📌 API Endpoints

### 👑 Admin Routes

| Method | Endpoint           | Description                     |
|--------|--------------------|---------------------------------|
| POST   | `/admin/signup`    | Creates a new admin             |
| POST   | `/admin/signin`    | Logs in an admin and returns JWT |
| POST   | `/admin/courses`   | Creates a new course            |
| GET    | `/admin/courses`   | Lists all courses created       |

**Sample Request/Response:**

```http
POST /admin/signup
Body: {"username": "admin", "password": "pass"}
Response: {"message": "Admin created successfully"}
```

```http
GET /admin/courses
Headers: {"Authorization": "Bearer <token>"}
Response: {
  "courses": [
    {
      "id": 1,
      "title": "course title",
      "description": "course description",
      "price": 100,
      "imageLink": "https://linktoimage.com",
      "published": true
    }
  ]
}
```

---

### 🙋 User Routes

| Method | Endpoint                    | Description                           |
|--------|-----------------------------|---------------------------------------|
| POST   | `/users/signup`             | Creates a new user                    |
| POST   | `/users/signin`             | Logs in a user and returns JWT       |
| GET    | `/users/courses`            | Lists all available courses          |
| POST   | `/users/courses/:courseId`  | Purchases a course                   |
| GET    | `/users/purchasedCourses`   | Lists purchased courses by the user |

**Sample Request/Response:**

```http
POST /users/signin
Body: {"username": "user", "password": "pass"}
Response: {"token": "your-token"}
```

```http
GET /users/purchasedCourses
Headers: {"Authorization": "Bearer <token>"}
Response: {
  "purchasedCourses": [
    {
      "id": 1,
      "title": "course title",
      "description": "course description",
      "price": 100,
      "imageLink": "https://linktoimage.com",
      "published": true
    }
  ]
}
```

---

## 🛠️ Setup & Run Locally

1. **Clone the repository**

```bash
git clone https://github.com/Tejas-Jogdand/Backend-Tasks-ExpressJs.git
cd Course-Management-System
```

2. **Install dependencies**

```bash
npm install
```

3. **Configure MongoDB**

Update your MongoDB URI in the `.env` file:

```env
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/courses
JWT_SECRET=your_jwt_secret
```

4. **Start the server**

```bash
node index.js
```

Server will be running at `http://localhost:3000`

---

## 📬 Feedback

This project is part of my personal learning repo, but if you find it helpful or want to contribute, feel free to open issues or submit pull requests!

---

## 📄 License

This project is licensed under the MIT License.

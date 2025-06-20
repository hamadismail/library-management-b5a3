# 📚 Library Management API

A full-featured RESTful API for managing a library system, built with **Express**, **TypeScript**, and **MongoDB (Mongoose)**.

## 🚀 Live Links

- 📦 **Backend GitHub Repo:** [GitHub Repo URL](https://github.com/hamadismail/library-management-b5a3)
- 🌐 **Live Server :** [Live API URL](https://library-management-server-kohl.vercel.app/)

---

## 📖 Project Overview

This Library Management System provides endpoints to:

- Manage book records (Create, Read, Update, Delete)
- Borrow books with business rules
- Retrieve borrow summaries using MongoDB aggregation

The API ensures **schema validation**, **business logic enforcement**, **middleware usage**, and **proper error handling**.

---

## 📦 Tech Stack

- **Node.js**
- **Express.js**
- **TypeScript**
- **MongoDB** with **Mongoose**
- **Postman** (for API testing)

---

## 📁 Features

- ✅ **Create, Read, Update, Delete** operations on books
- ✅ **Borrow a Book** with quantity checks and automatic availability updates
- ✅ **Aggregation Pipeline** to show total borrowed quantities
- ✅ **Schema validations** using Mongoose
- ✅ **Custom static method** for availability control
- ✅ **Mongoose middleware** (`post` findOneAndUpdate hook)
- ✅ **Filter, sort, and paginate books**
- ✅ **Consistent error responses**

---

## 🔧 Setup Instructions

1. **Clone the repository:**

```bash
git clone https://github.com/hamadismail/library-management-b5a3
cd library-management-b5a3
```

2. **Install dependencies:**

```bash
npm install
```

3. **Set up environment variables:**

```bash
PORT=5000
DATABASE_URL=mongodb://localhost:27017/libraryDB
```

4. **Run the server:**

```bash
npm run dev
```

## 🔁 API Endpoints

### 1. 📘 Create Book

#### POST `/api/books`

```bash
Request:
{
  "title": "The Theory of Everything",
  "author": "Stephen Hawking",
  "genre": "SCIENCE",
  "isbn": "9780553380163",
  "description": "An overview of cosmology and black holes.",
  "copies": 5,
  "available": true
}
```

### 2. 📚 Get All Books

#### GET `/api/books?filter=FANTASY&sortBy=createdAt&sort=desc&limit=5`

Supports:

- `filter` by genre
- `sortBy`, `sort` (asc/desc)
- `limit` (default: 10)

### 3. 📖 Get Book by ID

#### GET `/api/books/:bookId`

### 4. ✏️ Update Book

#### PUT `/api/books/:bookId`

```bash
{
  "copies": 50
}
```

### 5. 🗑️ Delete Book

#### DELETE `/api/books/:bookId`

### 6. 📦 Borrow a Book

#### POST `/api/borrow`

Business Rules:

- Check if book exists and has enough copies
- Deduct quantity
- If copies = 0, mark available as false using a static method

```bash
Request:
{
  "book": "64ab3f9e2a4b5c6d7e8f9012",
  "quantity": 2,
  "dueDate": "2025-07-18T00:00:00.000Z"
}
```

### 7. 📊 Borrow Summary (Aggregation)

#### GET `/api/borrow`

```bash
[
  {
    "book": {
      "title": "The Theory of Everything",
      "isbn": "9780553380163"
    },
    "totalQuantity": 5
  },
  ...
]
```

## ❌ Error Response Format

All error responses follow a consistent structure:

```bash
{
  "message": "Validation failed",
  "success": false,
  "error": {
    "name": "ValidationError",
    "errors": {
      "copies": {
        "message": "Copies must be a positive number"
      }
    }
  }
}
```

## 🧠 Bonus Features

- 📌 Mongoose `pre('save')` middleware to log borrow events
- 📌 Static method to update book availability
- 📌 Strict validation on all input fields
- 📌 Modular and maintainable file structure
- 📌 Well-structured code using TypeScript

## 📽️ Demo Video

[Watch Explanation](https://drive.google.com/file/d/1FrUAy1sT18SeOutnPCM-Fd53TkJhIs_2/view?usp=sharing)

---

## 👨‍💻 Author

- Hamad Ismail
- 📧 hamad.ismail.gub@gmail.com

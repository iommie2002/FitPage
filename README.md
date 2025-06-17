
# 📦 Product Ratings & Reviews Web Application

A full-stack web application built using **React**, **Node.js (Express)**, and **MySQL** that allows users to submit product reviews and star ratings. Users can add optional photos and see aggregated product ratings with reviews.

---

## 🚀 Features

- 📄 List of static products
- ⭐ Users can give **ratings**, **reviews**, or both
- 🖼️ Option to upload image URLs with reviews
- 🧠 Prevents multiple reviews per user/product
- 🏷️ (Bonus) Tag extraction from reviews *(optional feature placeholder)*
- 🧮 Displays average ratings per product
- ✅ Input validation on frontend
- 🔗 RESTful API integration

---

## 🖥️ Tech Stack

| Layer      | Technology           |
|------------|----------------------|
| Frontend   | React, HTML, CSS     |
| Backend    | Node.js, Express.js  |
| Database   | MySQL                |
| Tools      | Axios, gh-pages, Postman (for testing) |

---

## 📁 Project Structure

```
ratings-reviews-app/
│
├── backend/ or root/
│   ├── db.js                  # MySQL database connection config
│   ├── routes/
│   │   └── reviews.js         # API endpoints for reviews & products
│   ├── index.js               # Express app initialization
│
├── frontend/ or root/
│   ├── public/                # Static files
│   ├── src/
│   │   ├── App.js             # Main React component (lists products)
│   │   ├── components/
│   │   │   └── ProductCard.js # Individual product + review form
│   │   └── App.css            # Styling for app
│   ├── package.json           # Scripts & dependencies
│
├── README.md                  # Project documentation
└── .gitignore
```

---

## 🔧 How to Run the Project Locally

### ✅ Prerequisites

- Node.js and npm installed
- MySQL installed and running
- Git (optional)

---

### 📦 Backend Setup

1. Navigate to the project root or `backend/` directory:

```bash
cd ratings-reviews-app
```

2. Install dependencies:

```bash
npm install
```

3. Configure database connection in `db.js`:

```js
const db = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'yourpassword',
  database: 'product_reviews'
});
```

4. Ensure the MySQL database is created and contains:

```sql
CREATE DATABASE IF NOT EXISTS product_reviews;

CREATE TABLE products (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255)
);

CREATE TABLE reviews (
  id INT PRIMARY KEY AUTO_INCREMENT,
  product_id INT,
  user VARCHAR(100),
  rating INT,
  review TEXT,
  photo_url TEXT,
  UNIQUE KEY unique_user_review (product_id, user)
);
```

5. Start the backend server:

```bash
node index.js
# or
npm start
```

The backend will run on:  
`http://localhost:3001`

---

### 🎨 Frontend Setup

1. Navigate to the `frontend/` or root folder where your React app exists:

```bash
cd ratings-reviews-app
```

2. Install React dependencies:

```bash
npm install
```

3. Start the React development server:

```bash
npm start
```

The frontend will run on:  
`http://localhost:3000`

---

### 🔗 Backend API Endpoints

| Method | Route                     | Description                         |
|--------|---------------------------|-------------------------------------|
| GET    | `/products`               | Get list of all products            |
| GET    | `/reviews/:productId`     | Get reviews for a specific product  |
| POST   | `/review`                 | Submit a new review                 |

---

## 📌 Important Notes

- Users can only review a product once (validated by username).
- Ratings can be optional — user can submit only a review, or only a rating.
- Image field accepts a **URL string** (not actual image upload).
- Products are statically loaded from database.
- This project is designed for **local testing** and **demo use**.

---

## 🧪 API Testing via Postman

You can test your endpoints manually using [Postman](https://www.postman.com/).

- **POST** to `/review` with JSON body:
```json
{
  "product_id": 1,
  "user": "Alice",
  "rating": 5,
  "review": "Fantastic product!",
  "photo_url": "https://example.com/image.jpg"
}
```
---

## 🌐 Future Improvements

- User authentication (JWT)
- Tag analysis from reviews (NLP-based)
- Actual image upload (Multer/S3)
- Responsive UI improvements
- Admin dashboard

---

## 🧑‍💻 Author

**Omkar Awari**  
📧 omkar.awari@mitaoe.ac.in  
🔗 [LinkedIn](https://www.linkedin.com/in/omkar-awari-9396a223a/)

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

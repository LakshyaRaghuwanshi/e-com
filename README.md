# E-Commerce Backend Application

An end-to-end **E-Commerce Backend Application** built using **Spring Boot**, designed for managing products, users, carts, and orders. This project demonstrates core backend engineering skills, including RESTful API design, JWT authentication, database management with PostgreSQL, and deployment on AWS.

---

## 🚀 Tech Stack
- **Backend**: Java, Spring Boot (MVC, JPA, Security)
- **Database**: PostgreSQL
- **Authentication**: JWT (JSON Web Tokens)
- **Build Tool**: Maven
- **Deployment**: AWS Elastic Beanstalk, AWS RDS
- **Version Control**: Git & GitHub

---

## 📦 Features Implemented
- ✅ User Registration & Login (with JWT Authentication)
- ✅ Product Management (Add, Update, Delete, View Products)
- ✅ Cart Management (Add to Cart, View Cart, Remove Items)
- ✅ Order Placement & Tracking
- ✅ Secure APIs with role-based access control
- ✅ AWS Deployment (Elastic Beanstalk + RDS, instance later removed to avoid billing)

---

## 🛠️ Setup & Run Locally

### 1. Clone the Repository
```bash
git clone https://github.com/LakshyaRaghuwanshi/e-com.git
cd e-com
```

### 2. Configure Database
- Install PostgreSQL and create a database (e.g., `ecommerce_db`).
- Update your `src/main/resources/application.properties` file:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce_db
spring.datasource.username=your_db_username
spring.datasource.password=your_db_password
spring.jpa.hibernate.ddl-auto=update  # Auto creates tables
```

### 3. Build and Run the Application
```bash
mvn clean install
mvn spring-boot:run
```
The backend will start at `http://localhost:8080`.

---

## 🔐 API Authentication
- Use `/api/auth/register` to create users.
- Use `/api/auth/login` to receive JWT tokens.
- Pass the token in the header for secured APIs:
```http
Authorization: Bearer <your_jwt_token>
```

---

## 🗄️ Database Setup
- **Tables** are auto-generated via **JPA/Hibernate** upon first run.
- Entities include: Users, Products, Cart Items, Orders.

### Optional: Manual Schema (PostgreSQL)
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role VARCHAR(50) NOT NULL
);

CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    stock_quantity INT NOT NULL
);

CREATE TABLE cart_items (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id),
    product_id INT REFERENCES products(id),
    quantity INT NOT NULL
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id),
    total_price DECIMAL(10,2) NOT NULL,
    status VARCHAR(50) DEFAULT 'PLACED',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🌐 Deployment
This project was successfully deployed on **AWS Elastic Beanstalk** with **PostgreSQL RDS** integration.

- ✅ Elastic Beanstalk environment setup
- ✅ RDS instance for PostgreSQL
- ✅ IAM role & environment variable management

**Note:** The live instance has been temporarily removed to avoid AWS billing.

---

## 📸 Screenshots (Optional - Recommended)
- Product listing
- Signup/Login
- Add to Cart
- Order Placement

---

## 📄 Author
- **Lakshya Raghuwanshi**  
  [GitHub](https://github.com/LakshyaRaghuwanshi)

---

## 📢 Notes
- For demonstration purposes, **JWT secret keys** and sensitive info should be managed using environment variables (follow best practices in production).


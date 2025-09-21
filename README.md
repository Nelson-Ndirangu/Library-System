---

# 📚 Library Management System – Database Schema

This project contains the **database schema** for a **Library Management System**.
The schema manages books, members, librarians, and borrowing transactions.

---

## 🏗️ Entity-Relationship Overview

The schema consists of four main entities:

### 1. **Book**

Stores details about books available in the library.

| Column            | Type        | Description                                                                    |
| ----------------- | ----------- | ------------------------------------------------------------------------------ |
| `book_id`         | INT (PK)    | Unique identifier for each book.                                               |
| `member_id`       | INT (FK)    | References the member who currently borrowed the book (nullable if available). |
| `title`           | VARCHAR(70) | Title of the book.                                                             |
| `ISBN`            | VARCHAR(45) | ISBN number of the book.                                                       |
| `author`          | VARCHAR(60) | Author of the book.                                                            |
| `publisher`       | VARCHAR(45) | Publisher name.                                                                |
| `copiesAvailable` | INT         | Number of available copies.                                                    |

---

### 2. **Member**

Stores details about library members.

| Column           | Type        | Description                        |
| ---------------- | ----------- | ---------------------------------- |
| `member_id`      | INT (PK)    | Unique identifier for each member. |
| `name`           | VARCHAR(45) | Full name of the member.           |
| `email`          | VARCHAR(45) | Email address.                     |
| `phoneNumber`    | VARCHAR(45) | Contact number.                    |
| `membershipDate` | VARCHAR(45) | Date of membership registration.   |

---

### 3. **Librarian**

Stores details of library staff managing transactions.

| Column          | Type        | Description                           |
| --------------- | ----------- | ------------------------------------- |
| `librarian_id`  | INT (PK)    | Unique identifier for each librarian. |
| `staffId`       | INT         | Internal staff ID.                    |
| `librarianName` | VARCHAR(45) | Full name of the librarian.           |
| `phoneNumber`   | VARCHAR(45) | Contact number.                       |
| `dutyDate`      | DATETIME    | Date/time when librarian is on duty.  |

---

### 4. **BorrowTransaction**

Tracks borrow/return operations between members and librarians.

| Column           | Type        | Description                                           |
| ---------------- | ----------- | ----------------------------------------------------- |
| `Transaction_Id` | INT (PK)    | Unique identifier for each transaction.               |
| `member_id`      | INT (FK)    | References the member borrowing the book.             |
| `book_id`        | VARCHAR(45) | References the borrowed book.                         |
| `librarian_id`   | INT (FK)    | References the librarian officiating the transaction. |
| `borrowDate`     | DATETIME    | Date the book was borrowed.                           |
| `dueDate`        | DATE        | Expected return date.                                 |
| `returnDate`     | DATE        | Actual return date (nullable until returned).         |

---

## 🔗 Relationships

* **Member ↔ Book**: A member can borrow multiple books.
* **Member ↔ BorrowTransaction**: Each transaction belongs to a specific member.
* **Book ↔ BorrowTransaction**: Each transaction involves one book.
* **Librarian ↔ BorrowTransaction**: Each transaction is officiated by exactly one librarian.

---

## 🚀 Usage

* Import the schema into **MySQL Workbench** or run the SQL script in a MySQL server.
* Extend the schema by adding **categories, reservations, or fines** if needed.

---

## 📄 Notes

* Dates are stored as `DATE`/`DATETIME` for tracking transactions and duties.
* `member_id` in **Book** is optional; it indicates which member currently has the book checked out.
* Ensure **foreign keys** are enforced for data consistency.

---

Would you like me to also **generate the SQL CREATE TABLE statements** for this exact schema so you can run it directly in MySQL?

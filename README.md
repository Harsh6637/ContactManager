# Contact List Manager

## 📌 Table of Contents
- [🚀 Introduction](#-introduction)
- [🛠️ Technologies Used](#️-technologies-used)
- [📋 Prerequisites](#-prerequisites)
- [🔧 Setup Instructions](#-setup-instructions)
- [🔗 Backend and Frontend Communication](#-backend-and-frontend-communication)
- [🌟 Features & API Endpoints](#-features--api-endpoints)
- [🧪 Tests Implemented](#-tests-implemented)
- [🔍 Solution Highlights and Trade-offs](#-solution-highlights-and-trade-offs)
- [💡 Future Improvements](#-future-improvements)
- [📖 Conclusion](#-conclusion)

---

## 🚀 Introduction
Contact List Manager is a web application designed to streamline contact list management. It enables users to seamlessly add, search, view, and delete contacts, ensuring data validation and typo-tolerant search functionality. Built with modern web technologies, it adheres to clean coding principles and offers a modular architecture for scalability and maintainability.

## 🛠️ Technologies Used
- **Backend:** Ruby on Rails - Provides a robust RESTful API for contact management.
- **Frontend:** React.js - Offers a dynamic, responsive, and user-friendly interface.
- **Database:** SQLite (in-memory) - A lightweight and efficient database for temporary data storage.

### 📌 Testing Frameworks:
- **Backend:** Default Rails testing framework for comprehensive testing of models, controllers, and endpoints.
- **Frontend:** Jest and React Testing Library for unit, component, and integration tests.

---

## 📋 Prerequisites
Before setting up the project, ensure you have the following tools installed on your system:

- **Node.js (v16 or later):** [Download Node.js](https://nodejs.org/)
- **Ruby (latest stable version):** [Download Ruby](https://www.ruby-lang.org/en/downloads/)
- **Rails:** Install Ruby on Rails using the steps below:
  ```sh
  ruby -v  # Verify Ruby installation
  gem install bundler
  gem install rails
  rails -v  # Verify Rails installation
  ```
- **SQLite:** [SQLite Installation Guide](https://www.sqlite.org/download.html)
- **Git:** [Download Git](https://git-scm.com/downloads)

---

## 🔧 Setup Instructions
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/Harsh6637/ContactManager.git
cd ContactManager
```

### 2️⃣ Backend Setup
```sh
cd contact-manager-backend
bundle install
rails db:create db:migrate
rails server
```
Backend server runs on **port 3000**: [http://localhost:3000](http://localhost:3000)

### 3️⃣ Frontend Setup
```sh
cd ../contact-manager-frontend
npm install
npm start
```
Frontend server runs on **port 3001**: [http://localhost:3001](http://localhost:3001)

---

## 🔗 Backend and Frontend Communication
The frontend interacts with the backend via RESTful API endpoints.
- **Backend Base URL:** `http://localhost:3000`
- **Frontend Base URL:** `http://localhost:3001`

---

## 🌟 Features & API Endpoints

### 1️⃣ Add Contacts
- **Endpoint:** `POST /contacts`
- **Request Payload:**
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com"
  }
  ```
- **Response:** Adds contact if the email is unique.

### 2️⃣ View All Contacts
- **Endpoint:** `GET /contacts`
- **Response:** Returns all contacts as a JSON array.

### 3️⃣ Search Contacts (Typo-Tolerant & Partial Matching)
- **Endpoint:** `GET /contacts?query=<search_term>`
- **Functionality:** Returns results even with typos or partial matches.
- **How It Works:**
    - The search function uses fuzzy string matching through the Amatch gem.
    - It scans contact names and email addresses for close matches to the query.
    - Minor spelling errors, missing characters, or partial inputs will still yield relevant results.  
    - **Example Queries & Matches:**  
  
  | Search Query | Possible Matches         |
  |-------------|---------------------------|
  | Jon         | John Doe                  |
  | exmaple     | example@example.com       |
  | Smth        | Smith Johnson             |

### 4️⃣ Delete Contacts
- **Endpoint:** `DELETE /contacts/:id`
- **Functionality:** Deletes a contact by its unique ID.  

### 5️⃣ Contact Validation
- **Name Validation:**
    - Must be at least 2 characters long.
    - Cannot contain special characters or numbers.
- **Email Validation:**
    - Must follow a valid email format (e.g., `example@domain.com`).
    - Ensures uniqueness in the database.


---

## 🧪 Tests Implemented
### 📌 Backend Tests
- ✅ **Unit Tests:** Validate models (e.g., email uniqueness, name validation).
- ✅ **Component Tests:** Verify API responses and controller actions.
- ✅ **Integration Tests:** Simulate workflows like creating and searching contacts.
- **Run All Tests:**
  ```sh
  cd contact-manager-backend
  rails test
  ```
- **Run Individual Test Files:**
  ```sh
  rails test test/models/contact_test.rb
  ```

### 📌 Frontend Tests
- ✅ **Unit Tests:** Validate utility functions.
- ✅ **Component Tests:** Test React components for rendering and interactions.
- ✅ **Integration Tests:** Ensure UI communicates correctly with the backend.
- **Run All Tests:**
  ```sh
  cd ../contact-manager-frontend
  npm test
  ```
- **Run Individual Test Files:**
  ```sh
  npm test ContactForm.test.js
  ```

---

## 🔍 Solution Highlights and Trade-offs
### ✅ Solution Overview
- Modular full-stack architecture (Rails + React.js).
- Typo-tolerant search via fuzzy string matching.
- Robust testing with unit, component, and integration tests.
- Delete functionality for better contact management.

### ⚖️ Trade-offs
| Decision | Pros | Cons |
|----------|------|------|
| **Database: SQLite (In-memory)** | Lightweight, easy setup | Not suitable for production |
| **Search: Amatch Gem** | Simple, effective typo-matching | Less powerful than Elasticsearch |
| **Authentication: Not Implemented** | Simplifies development | Lacks user security |
| **UI Design: Functionality-Focused** | Ensures usability | Could be visually improved |

---

## 💡 Future Improvements
- **Add persistent database** (PostgreSQL/MySQL).
- **Implement user authentication** (Devise or OAuth).
- **Enhance search logic** with advanced algorithms (Elasticsearch).
- **Refine UI** using Material-UI or Bootstrap.

---

## 📖 Conclusion
Contact List Manager is a robust and feature-rich contact management solution. Its clean architecture, typo-tolerant search, delete functionality, and seamless backend-frontend integration make it ideal for individuals or teams. With future enhancements like persistent storage and authentication, it can evolve into a highly scalable contact management system.



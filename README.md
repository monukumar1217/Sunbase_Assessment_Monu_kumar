### Project Explanation for CRUD Application

---

#### **Project Overview**

This project involves creating a CRUD (Create, Read, Update, Delete) application for managing customer data. The application is developed using a combination of technologies including MySQL for the database, JSP Servlet/Spring Boot for the backend, and HTML/CSS/JavaScript for the frontend. Additionally, JWT (JSON Web Token) authentication is implemented to secure the API endpoints.

---

#### **Technologies Used**

- **Database:** MySQL
- **Backend:** JSP Servlet / Spring Boot
- **Frontend:** HTML, CSS, JavaScript

---

#### **Phase 1: CRUD Operations Implementation**

**1. Create a Customer**
   - **Endpoint:** `/api/customer/create`
   - **Method:** POST
   - **Request Body:**
     ```json
     {
       "first_name": "Jane",
       "last_name": "Doe",
       "street": "Elvnu Street",
       "address": "H no 2",
       "city": "Delhi",
       "state": "Delhi",
       "email": "sam@gmail.com",
       "phone": "12345678"
     }
     ```
   - **Description:** This endpoint allows the creation of a new customer record in the MySQL database.

**2. Update a Customer**
   - **Endpoint:** `/api/customer/update/{id}`
   - **Method:** PUT
   - **Request Body:**
     ```json
     {
       "first_name": "Jane",
       "last_name": "Doe",
       "street": "Elvnu Street",
       "address": "H no 2",
       "city": "Delhi",
       "state": "Delhi",
       "email": "sam@gmail.com",
       "phone": "12345678"
     }
     ```
   - **Description:** This endpoint updates the details of an existing customer identified by the provided ID.

**3. Get a List of Customers**
   - **Endpoint:** `/api/customer/list`
   - **Method:** GET
   - **Parameters:** Pagination, Sorting, and Searching parameters (e.g., `page`, `size`, `sort`, `search`)
   - **Description:** This endpoint retrieves a paginated, sorted, and searchable list of customers from the database.

**4. Get a Single Customer by ID**
   - **Endpoint:** `/api/customer/{id}`
   - **Method:** GET
   - **Description:** This endpoint retrieves the details of a single customer identified by the provided ID.

**5. Delete a Customer**
   - **Endpoint:** `/api/customer/delete/{id}`
   - **Method:** DELETE
   - **Description:** This endpoint deletes the customer identified by the provided ID from the database.

---

#### **Authentication**

- **Technology:** JWT (JSON Web Token)
- **Description:** Implemented JWT authentication to secure the API endpoints. Users must log in to receive a token, which must be included in the Authorization header for subsequent API calls.

---

#### **Frontend Implementation**

**1. Login Screen**
   - **Description:** A simple login form to authenticate users and retrieve a JWT token.

**2. Customer List Screen**
   - **Description:** Displays a table of customers with options for pagination, sorting, and searching. Includes buttons for editing and deleting customers.

**3. Add a New Customer**
   - **Description:** A form to add a new customer to the database.

**UI Design**
- **Description:** The UI is kept basic with HTML tables, forms, and buttons to perform CRUD operations.

---

#### **Phase 2: Sync Functionality**

**New Feature: Sync Button**
   - **Description:** Added to the Customer List Screen to fetch the customer list from a remote API and update the local database.

**Remote API Interaction**

1. **Authenticate User**
   - **Endpoint:** `https://qa.sunbasedata.com/sunbase/portal/api/assignment_auth.jsp`
   - **Method:** POST
   - **Request Body:**
     ```json
     {
       "login_id": "test@sunbasedata.com",
       "password": "Test@123"
     }
     ```
   - **Description:** Receives a Bearer token for authentication.

2. **Get Customer List**
   - **Endpoint:** `https://qa.sunbasedata.com/sunbase/portal/api/assignment.jsp`
   - **Method:** GET
   - **Parameters:** `cmd=get_customer_list`
   - **Headers:** `Authorization: Bearer token_received_in_authentication_API_call`
   - **Description:** Retrieves a list of customers from the remote API.

**Database Update Logic**
- **Description:** Checks if the fetched customers already exist in the local database. If they exist, updates their details; otherwise, inserts them as new records.

---

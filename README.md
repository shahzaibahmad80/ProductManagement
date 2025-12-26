📘 Project Documentation
ASP.NET Core Web API (.NET 8) – Role-Based Secure Application

1. Project Overview
This project is a secure, role-based Web API application developed using ASP.NET Core Web API (.NET 8) and Clean Architecture principles.
It supports:
JWT-based authentication
Role-based authorization (Admin / Client)
Secure CRUD operations
HTML-based reporting and printing
SQL Server database with relational integrity
Asynchronous programming using async / await
The system ensures only authorized users can perform critical operations, while clients have read-only access and reporting capabilities.

2. Technology Stack
Technology
Description
.NET 8
Backend framework
ASP.NET Core Web API
RESTful API
SQL Server
Database
Entity Framework Core
ORM
JWT (JSON Web Tokens)
Authentication
HTML/CSS
Reporting & print views
Swagger (OpenAPI)
API documentation
Async / Await
Asynchronous programming


3. Solution Architecture
The solution follows Clean Architecture with proper separation of concerns.
📂 Solution Structure
MySolution
│
├── MyProject.Domain
│   ├── Entities
│   ├── Enums
│   ├── Interfaces
│
├── MyProject.Application
│   ├── DTOs
│   ├── Interfaces
│   ├── Services
│
├── MyProject.Infrastructure
│   ├── Data
│   ├── Repositories
│   ├── Migrations
│
├── MyProject.API
│   ├── Controllers
│   ├── Authentication
│   ├── Authorization
│   ├── wwwroot (HTML Reports)
│   ├── Program.cs
│   └── appsettings.json


4. Dependency Flow
The dependencies strictly follow Clean Architecture rules:
Domain
   ↑
Application
   ↑
Infrastructure
   ↑
Web API

Dependency Details
Domain
Contains core business entities and rules
Has no dependency on any other layer
Application
Depends only on the Domain
Contains business logic, DTOs, and service interfaces
Infrastructure
Depends on Application and Domain
Implements database access and repositories
Web API
Depends on Application and Infrastructure
Handles HTTP requests, authentication, and authorization

5. Database Configuration
Database Type
SQL Server
Database Features
Primary key & foreign key relationships
Products linked with Categories
Users with roles (Admin / Client)
Setup Steps
Open SQL Server Management Studio (SSMS)
Restore the provided database backup file (.bak)
Note the database name
Update the connection string in:
appsettings.json

"ConnectionStrings": {
  "DefaultConnection": "Server=.;Database=MyDatabase;Trusted_Connection=True;TrustServerCertificate=True"
}


6. Running the Application
Step-by-Step Guide
Open the solution in Visual Studio
Set MyProject.API as the Startup Project
Select HTTPS profile
Run the application

7. Application Flow
Default Behavior
When the application runs on HTTPS:
The Login page is displayed
Swagger can be accessed manually by appending:
https://localhost:{port}/swagger


8. Authentication & Authorization
Authentication
Uses JWT Token-based authentication
Users must log in using valid email and password
On successful login:
A JWT token is generated
Token is used for accessing protected APIs
Authorization (Role-Based)
Role
Permissions
Admin
Full access (Create, Update, Delete, Reports)
Client
View data & Print reports only


9. Role-Based Access Control (RBAC)
Admin User
Can:
Create products
Update products
Delete products
Manage categories
View & print reports
Client User
Can:
View product and category data
Print reports
Cannot:
Create, update, or delete data
Security Enforcement
Even if a Client user manually tampers with URLs:
Access to restricted pages is blocked
User receives alert:
"Access denied. Only admin can perform this action."
This ensures frontend and backend authorization protection.

10. CRUD Operations
Product Management
Create Product
Update Product
Delete Product
View Products
Category Relationship
Products are linked to Categories
Enforced via Primary Key & Foreign Key
Ensures data integrity

11. Reporting Module
Reporting Features
HTML-based reporting pages
Used for:
Viewing reports
Printing reports
Accessible by:
Admin
Client (read-only)
Benefits
Lightweight
Easy to print
Browser-based report rendering

12. Asynchronous Programming
The application extensively uses:
async / await

Advantages
Improved performance
Non-blocking I/O operations
Better scalability
Efficient database operations
All database and service calls are implemented asynchronously.

13. Swagger (API Documentation)
Swagger is enabled for:
API testing
Request/response inspection
Token-based authorization testing
Access URL
https://localhost:{port}/swagger

JWT Authorization in Swagger
Login API → Get JWT Token
Click Authorize
Enter:
Bearer {your_token}

Access secured endpoints

14. Security Measures
JWT authentication
Role-based authorization
Secure endpoints
URL tampering protection
HTTPS enforced

15. Conclusion
This project demonstrates:
Clean Architecture best practices
Secure role-based authentication
Proper separation of concerns
Scalable and maintainable design
Real-world enterprise-level patterns
It is suitable for:
Enterprise applications
Secure business systems
Scalable APIs

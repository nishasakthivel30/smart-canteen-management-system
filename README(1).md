# 🍽️ Smart Canteen Ordering & Management System

**Java-Based Web Application for Digital Food Ordering and Canteen Management**

[![Java](https://img.shields.io/badge/Java-21-orange)](https://www.oracle.com/java/)
[![JSP](https://img.shields.io/badge/JSP-Jakarta%20EE-blue)](https://jakarta.ee/)
[![Servlet](https://img.shields.io/badge/Servlet-Jakarta%20Servlet-green)](https://jakarta.ee/)
[![MySQL](https://img.shields.io/badge/MySQL-8.4-blue)](https://www.mysql.com/)
[![Tomcat](https://img.shields.io/badge/Apache%20Tomcat-10.1-yellow)](https://tomcat.apache.org/)
[![JDBC](https://img.shields.io/badge/JDBC-Database%20Connectivity-red)](https://docs.oracle.com/javase/tutorial/jdbc/)
[![GitHub](https://img.shields.io/badge/GitHub-Version%20Control-black)](https://github.com/)

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Project Objectives](#-project-objectives)
- [Key Features](#-key-features)
- [Student Module](#-student-module)
- [Admin Module](#-admin-module)
- [System Architecture](#-system-architecture)
- [Student Workflow](#-student-workflow)
- [Admin Workflow](#-admin-workflow)
- [Order Management](#-order-management)
- [Database Architecture](#-database-architecture)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Database Configuration](#-database-configuration)
- [Running the Application](#-running-the-application)
- [Usage Guide](#-usage-guide)
- [How the System Works](#-how-the-system-works)
- [Security Features](#-security-features)
- [Troubleshooting](#-troubleshooting)
- [Learning Outcomes](#-learning-outcomes)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🌟 Overview

The **Smart Canteen Ordering & Management System** is a Java-based web application developed to simplify and digitize the food ordering and management process in a college canteen.

The system provides separate functionalities for **students** and **administrators**.

Students can:

- Register and log in
- View available food items
- Select food items
- Choose quantity
- Select pickup time
- Place food orders
- Receive order confirmation
- View previous orders
- Track order status

Administrators can:

- Log in through an admin account
- Manage food items
- Add new food items
- Edit food information
- Delete food items
- Manage food stock
- View customer orders
- Update order status

The application uses **Java Servlets and JSP** for web application development, **JDBC** for database connectivity, **MySQL** for data storage, and **Apache Tomcat** as the Servlet container.

---

## 🎯 Project Objectives

The main objectives of the project are:

- To digitize the traditional canteen ordering process.
- To reduce waiting time for students.
- To provide a convenient online food-ordering interface.
- To allow students to select food and pickup time before visiting the canteen.
- To maintain food items and stock digitally.
- To provide administrators with centralized order management.
- To maintain student, food, and order information in a database.
- To provide order-status tracking.
- To reduce manual errors in order management.

---

# ✨ Key Features

## 👨‍🎓 Student Features

- Student registration
- Student login
- Session-based authentication
- View food menu
- View available food items
- Select food item
- Select quantity
- Stock availability validation
- Select pickup time
- Place food orders
- Automatic total amount calculation
- Order confirmation
- View previous orders
- Track order status
- Logout

---

## 👨‍💼 Admin Features

- Admin login
- Admin dashboard
- Add food items
- Edit food details
- Delete food items
- Manage food stock
- View all customer orders
- Update order status
- Logout

---

# 👨‍🎓 Student Module

The Student Module provides the complete food-ordering functionality.

### 1. Student Registration

New students can create an account by providing:

- Name
- Email
- Password

The registration information is stored in the MySQL database.

---

### 2. Student Login

Registered students can log in using their email and password.

After successful authentication, a session is created containing information such as:

```text
User ID
User Name
User Email
User Role
```

---

### 3. Food Menu

Students can view available food items from the canteen.

Each food item contains information such as:

```text
Food Name
Category
Price
Available Stock
```

---

### 4. Food Selection

Students can select a food item from the menu and continue to the order page.

The selected food item can be automatically selected on the order page.

---

### 5. Quantity Selection

Students can select the required quantity.

The system validates the requested quantity against the available stock.

Example:

```text
Available Stock: 10
Requested Quantity: 3

Result: Order can be placed
```

If the requested quantity is greater than the available stock, the system displays an error message.

---

### 6. Pickup Time

Students can select their preferred pickup time while placing the order.

The selected pickup time is stored with the order information.

---

### 7. Order Placement

When the student places an order, the system:

1. Validates the food item.
2. Checks available stock.
3. Validates quantity.
4. Calculates the total amount.
5. Creates a new order.
6. Creates the order-item record.
7. Updates food stock.
8. Displays the order confirmation.

---

### 8. Order Confirmation

After successful order placement, the system displays:

```text
Order ID
Total Amount
Pickup Time
Order Status
```

The initial order status is:

```text
PLACED
```

---

### 9. My Orders

Students can view their previous orders and check their current order status.

---

### 10. Logout

Students can safely log out of the application.

The active HTTP session is invalidated when logout is performed.

---

# 👨‍💼 Admin Module

The Admin Module provides administrative control over food and customer orders.

---

## 1. Admin Login

Administrators can log in using their administrator credentials.

The system checks the user's role before allowing access to administrator functionality.

```text
Role = ADMIN
```

---

## 2. Admin Dashboard

The dashboard provides access to administrative operations such as:

- Food management
- Stock management
- Order management
- Order-status updates

---

## 3. Add Food

Administrators can add new food items by entering:

```text
Food Name
Category
Price
Stock
```

---

## 4. Edit Food

Administrators can update existing food information.

The following information can be modified:

- Food name
- Category
- Price
- Stock

---

## 5. Delete Food

Administrators can remove food items that are no longer available.

Database relationships are maintained while deleting records.

---

## 6. Stock Management

Administrators can update the available quantity of food items.

When a student places an order, the corresponding stock is automatically reduced.

Example:

```text
Initial Stock = 20
Ordered Quantity = 3

Remaining Stock = 17
```

---

## 7. View Customer Orders

Administrators can view customer order information including:

```text
Order ID
Customer Name
Food Name
Quantity
Total Amount
Pickup Time
Order Status
Order Date
```

---

## 8. Update Order Status

Administrators can update the status of an order.

The supported order flow is:

```text
PLACED
   ↓
PREPARING
   ↓
READY
   ↓
COMPLETED
```

---

# 🏗️ System Architecture

The application follows a simple layered web-application architecture.

```text
                    ┌─────────────────────┐
                    │     User Browser    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      JSP Pages      │
                    │  HTML / CSS / JS    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Java Servlets     │
                    │   Business Logic    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │        JDBC         │
                    │ Database Connectivity│
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   MySQL Database    │
                    └─────────────────────┘
```

---

# 🔄 Student Workflow

```text
Student Registration
        ↓
Student Login
        ↓
Food Menu
        ↓
Select Food
        ↓
Select Quantity
        ↓
Select Pickup Time
        ↓
Place Order
        ↓
Calculate Total
        ↓
Update Stock
        ↓
Order Confirmation
        ↓
My Orders
        ↓
Track Order Status
```

---

# 🔄 Admin Workflow

```text
Admin Login
     ↓
Admin Dashboard
     ↓
Manage Food
     ├── Add Food
     ├── Edit Food
     └── Delete Food

     ↓
Manage Stock
     ↓
View Customer Orders
     ↓
Update Order Status
```

---

# 📦 Order Management

The order-management process consists of several steps.

### Step 1 — Select Food

The student selects a food item from the menu.

### Step 2 — Select Quantity

The student specifies the required quantity.

### Step 3 — Validate Stock

The system checks whether sufficient stock is available.

### Step 4 — Calculate Amount

The total amount is calculated using:

```text
Total Amount = Food Price × Quantity
```

### Step 5 — Create Order

The order is inserted into the `orders` table.

### Step 6 — Create Order Item

The selected food and quantity are stored in the `order_items` table.

### Step 7 — Update Stock

The ordered quantity is deducted from the food stock.

### Step 8 — Confirmation

The student receives an order confirmation containing the order details.

---

# 🗄️ Database Architecture

The project uses a MySQL database named:

```text
smart_canteen
```

The database contains four main tables:

```text
users
food_items
orders
order_items
```

---

## 👤 Users Table

The `users` table stores student and administrator account information.

| Column | Description |
|--------|-------------|
| `user_id` | Unique user ID |
| `name` | User name |
| `email` | User email |
| `password` | User password |
| `role` | User role |

Possible roles include:

```text
STUDENT
ADMIN
```

---

## 🍔 Food Items Table

The `food_items` table stores available canteen food.

| Column | Description |
|--------|-------------|
| `food_id` | Unique food ID |
| `food_name` | Name of food |
| `category` | Food category |
| `price` | Food price |
| `stock` | Available quantity |

---

## 🧾 Orders Table

The `orders` table stores customer order information.

| Column | Description |
|--------|-------------|
| `order_id` | Unique order ID |
| `user_id` | Customer ID |
| `total_amount` | Total order amount |
| `pickup_time` | Selected pickup time |
| `status` | Current order status |
| `order_date` | Order date and time |

---

## 📋 Order Items Table

The `order_items` table stores individual food items belonging to an order.

| Column | Description |
|--------|-------------|
| `order_item_id` | Unique order-item ID |
| `order_id` | Related order |
| `food_id` | Related food |
| `quantity` | Ordered quantity |

---

# 🔗 Database Relationships

The basic relationship between the tables is:

```text
users
  │
  │ user_id
  ▼
orders
  │
  │ order_id
  ▼
order_items
  │
  │ food_id
  ▼
food_items
```

This allows the system to connect:

```text
User → Order → Ordered Food
```

---

# 💻 Technology Stack

## Backend

### Java

Java is used as the primary backend programming language.

It handles:

- Business logic
- Authentication
- Order processing
- Food management
- Database operations

---

### Java Servlets

Servlets handle HTTP requests and responses.

Examples include:

```text
RegisterServlet
LoginServlet
MenuServlet
OrderServlet
MyOrdersServlet
AdminServlet
AddFoodServlet
EditFoodServlet
DeleteFoodServlet
AdminOrdersServlet
UpdateOrderStatusServlet
LogoutServlet
```

---

### JSP

JSP is used to create dynamic web pages.

Examples:

```text
login.jsp
register.jsp
login-success.jsp
menu.jsp
order.jsp
order-success.jsp
myorders.jsp
admin.jsp
addfood.jsp
editfood.jsp
adminorders.jsp
```

---

### JDBC

JDBC provides communication between Java and MySQL.

The application uses JDBC for:

- SELECT
- INSERT
- UPDATE
- DELETE

operations.

---

## Database

### MySQL

MySQL is used to store:

- User information
- Food information
- Order information
- Order-item information

---

## Frontend

### HTML5

Used to structure the web pages.

### CSS3

Used to style the application interface.

### JavaScript

Used for client-side functionality where required.

---

## Server

### Apache Tomcat

Apache Tomcat acts as the Servlet container and web server for the application.

---

## Development Tools

- Visual Studio Code
- PowerShell
- Git
- GitHub
- MySQL Command Line / MySQL tools

---

# 📁 Project Structure

```text
smart-canteen-management-system/
│
├── src/
│   ├── DBConnection.java
│   ├── RegisterServlet.java
│   ├── LoginServlet.java
│   ├── MenuServlet.java
│   ├── OrderServlet.java
│   ├── MyOrdersServlet.java
│   ├── AdminServlet.java
│   ├── AddFoodServlet.java
│   ├── EditFoodServlet.java
│   ├── DeleteFoodServlet.java
│   ├── AdminOrdersServlet.java
│   ├── UpdateOrderStatusServlet.java
│   └── LogoutServlet.java
│
├── web/
│   ├── register.jsp
│   ├── login.jsp
│   ├── login-success.jsp
│   ├── menu.jsp
│   ├── order.jsp
│   ├── order-success.jsp
│   ├── myorders.jsp
│   ├── admin.jsp
│   ├── addfood.jsp
│   ├── editfood.jsp
│   ├── adminorders.jsp
│   ├── style.css
│   │
│   └── WEB-INF/
│       ├── web.xml
│       ├── classes/
│       └── lib/
│
├── lib/
│   └── mysql-connector-j-9.4.0.jar
│
├── bin/
│
├── .gitignore
└── README.md
```

---

# 📋 Prerequisites

Before running the application, install:

- JDK 21
- MySQL Server
- Apache Tomcat 10.1
- MySQL Connector/J
- Visual Studio Code
- Git

---

# 📥 Installation

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/smart-canteen-management-system.git
```

Move into the project directory:

```bash
cd smart-canteen-management-system
```

---

## 2. Verify Java Installation

Run:

```bash
java -version
```

and:

```bash
javac -version
```

The project was developed using Java 21.

---

## 3. Verify MySQL

Start MySQL and log in:

```bash
mysql -u root -p
```

---

# 🗄️ Database Configuration

Create the database:

```sql
CREATE DATABASE smart_canteen;
```

Select the database:

```sql
USE smart_canteen;
```

Create the required tables:

```text
users
food_items
orders
order_items
```

The database should contain the required primary-key and foreign-key relationships.

---

# ⚙️ Database Connection

The Java application uses:

```text
src/DBConnection.java
```

The connection contains:

```text
JDBC URL
Database name
MySQL username
MySQL password
```

Example structure:

```java
String url =
    "jdbc:mysql://localhost:3306/smart_canteen";

String username = "root";
String password = "YOUR_PASSWORD";
```

### ⚠️ Important

Do not upload your real MySQL password to a public GitHub repository.

For a public repository, use a configuration method such as environment variables or a local configuration file that is excluded through `.gitignore`.

---

# 🚀 Running the Application

## Step 1 — Open the Project

Open the project folder in Visual Studio Code.

---

## Step 2 — Configure Environment Variables

Set the Java and Tomcat paths.

### Windows PowerShell

```powershell
$env:JAVA_HOME="C:\Program Files\Java\jdk-21"
```

Set Tomcat:

```powershell
$env:CATALINA_HOME="C:\Path\To\apache-tomcat-10.1"
```

---

## Step 3 — Compile the Servlets

Compile the Java servlet classes using the Tomcat Servlet API and MySQL Connector/J.

Example:

```powershell
javac -cp ".\lib\mysql-connector-j-9.4.0.jar;$env:CATALINA_HOME\lib\servlet-api.jar" -d ".\web\WEB-INF\classes" ".\src\LoginServlet.java"
```

---

## Step 4 — Deploy the Application

Copy the web application into the Tomcat `webapps` directory.

Example:

```powershell
Copy-Item ".\web\*" "$env:CATALINA_HOME\webapps\canteen\" -Recurse -Force
```

---

## Step 5 — Start Tomcat

```powershell
& "$env:CATALINA_HOME\bin\startup.bat"
```

---

## Step 6 — Open the Application

Open the following URL in your browser:

```text
http://localhost:8080/canteen/login.jsp
```

---

# 📖 Usage Guide

## Student Usage

### Register

Open:

```text
register.jsp
```

Enter:

```text
Name
Email
Password
```

Then submit the registration form.

---

### Login

Open:

```text
login.jsp
```

Enter the registered email and password.

After successful login, the user is redirected to the login-success page.

---

### View Food Menu

Click:

```text
View Food Menu
```

The system displays available food items.

---

### Place an Order

1. Select a food item.
2. Click **Order**.
3. Select quantity.
4. Select pickup time.
5. Submit the order.

The system validates the stock before creating the order.

---

### View Order Confirmation

After successful ordering, the confirmation page displays:

```text
Order ID
Total Amount
Pickup Time
Status
```

---

### View Previous Orders

Click:

```text
View My Orders
```

Students can view their previous orders and their current status.

---

# 👨‍💼 Admin Usage

## Admin Login

Use an administrator account to access the admin functionality.

---

## Add Food

From the admin dashboard:

```text
Add Food
```

Enter:

```text
Food Name
Category
Price
Stock
```

---

## Edit Food

Select an existing food item and update its information.

---

## Delete Food

Select the food item that should be removed.

Database relationships are considered when deleting food records.

---

## Manage Orders

Open:

```text
Admin Orders
```

The administrator can view:

```text
Order ID
Customer
Food
Quantity
Total Amount
Pickup Time
Status
Order Date
```

---

## Update Order Status

The administrator can update an order through:

```text
PLACED
PREPARING
READY
COMPLETED
```

---

# 🔧 How the System Works

## Registration Flow

```text
register.jsp
      ↓
RegisterServlet
      ↓
JDBC
      ↓
users table
      ↓
Registration Completed
```

---

## Login Flow

```text
login.jsp
     ↓
LoginServlet
     ↓
JDBC
     ↓
users table
     ↓
Verify Credentials
     ↓
Create HTTP Session
     ↓
Student / Admin
```

---

## Food Menu Flow

```text
menu.jsp
    ↓
MenuServlet
    ↓
JDBC
    ↓
food_items table
    ↓
Available Food Items
```

---

## Order Flow

```text
order.jsp
    ↓
OrderServlet
    ↓
Check Food
    ↓
Check Stock
    ↓
Calculate Total
    ↓
Insert Order
    ↓
Insert Order Item
    ↓
Update Stock
    ↓
Order Confirmation
```

---

## Admin Order Flow

```text
Admin Dashboard
      ↓
AdminOrdersServlet
      ↓
Retrieve Orders
      ↓
Display Customer Orders
      ↓
UpdateOrderStatusServlet
      ↓
Update Order Status
```

---

# 🔐 Security Features

The application implements several basic security-related mechanisms.

## Prepared Statements

Database queries use `PreparedStatement` to safely pass user-provided values into SQL queries.

Example:

```java
PreparedStatement statement =
        connection.prepareStatement(sql);

statement.setString(1, email);
statement.setString(2, password);
```

---

## Session Management

The application uses `HttpSession` to maintain authenticated user information.

Session attributes include:

```text
userId
userName
userEmail
userRole
```

---

## Role-Based Access

The application distinguishes between:

```text
STUDENT
ADMIN
```

Administrative pages check the logged-in user's role before providing access.

---

## Stock Validation

Before placing an order, the system verifies that the requested quantity is available.

This helps prevent ordering more food than the available stock.

---

## Database Relationships

Primary keys and foreign-key relationships are used to maintain consistency between:

```text
Users
Orders
Order Items
Food Items
```

# 🐛 Troubleshooting

## Issue: Tomcat Does Not Start

Check whether `JAVA_HOME` is configured correctly.

```powershell
$env:JAVA_HOME="C:\Program Files\Java\jdk-21"
```

Check Tomcat:

```powershell
$env:CATALINA_HOME="C:\Path\To\apache-tomcat-10.1"
```

Then start:

```powershell
& "$env:CATALINA_HOME\bin\startup.bat"
```

---

## Issue: Database Connection Failed

Check:

- MySQL server is running.
- Database name is correct.
- Username is correct.
- Password is correct.
- MySQL port is correct.
- MySQL Connector/J is available.

---

## Issue: ClassNotFoundException

Make sure the MySQL Connector/J JAR is available:

```text
lib/mysql-connector-j-9.4.0.jar
```

Also make sure it is available to the deployed Tomcat application.

---

## Issue: 404 Error

Check:

- Tomcat is running.
- Application is deployed inside `webapps`.
- Application name is correct.
- URL is correct.
- Servlet mapping is correct.
- Servlet class has been compiled.

Application URL:

```text
http://localhost:8080/canteen/login.jsp
```

---

## Issue: Registration Failed

Check:

- MySQL is running.
- `smart_canteen` database exists.
- `users` table exists.
- Database connection is working.
- The email is not already registered.

---

## Issue: Order Failed

Check:

- User is logged in.
- Food item exists.
- Food stock is available.
- Requested quantity is valid.
- Database connection is working.
- `orders` and `order_items` tables exist.

---

## Issue: Admin Page Not Accessible

Make sure you are logged in using an account whose role is:

```text
ADMIN
```

The system uses the session role to control access to administrative pages.

---

# 📈 Advantages

The Smart Canteen Ordering & Management System provides the following advantages:

- Reduces manual ordering.
- Reduces student waiting time.
- Provides convenient food ordering.
- Provides centralized food management.
- Provides stock management.
- Provides order tracking.
- Reduces manual calculation errors.
- Maintains order information digitally.
- Provides separate student and admin functionality.
- Provides a structured database for canteen operations.

---

# 🎓 Learning Outcomes

This project provided practical experience in:

- Core Java
- Object-Oriented Programming
- Java Servlets
- JSP
- JDBC
- SQL
- MySQL
- CRUD operations
- HTTP request and response handling
- HTTP sessions
- Role-based access
- Database relationships
- Web application development
- Apache Tomcat
- HTML
- CSS
- JavaScript
- Git
- GitHub
- Application deployment

---

# 🤝 Contributing

Contributions and suggestions are welcome.

### Steps to contribute

1. Fork the repository.
2. Create a new branch.

```bash
git checkout -b feature/new-feature
```

3. Make your changes.
4. Commit the changes.

```bash
git add .
git commit -m "Add new feature"
```

5. Push the branch.

```bash
git push origin feature/new-feature
```

6. Create a Pull Request.

---

# 📄 License

This project is developed for **educational and academic purposes**.

---

# 👨‍💻 Author

**Nisha S**
nishasakthivel30gmail.com

Computer Science Engineering Student

### Project

**Smart Canteen Ordering & Management System**

### Technologies

`Java` `JSP` `Servlets` `JDBC` `MySQL` `HTML5` `CSS3` `JavaScript` `Apache Tomcat`

### GitHub

```text
https://github.com/nishasakthivel30/smart-canteen-management-system
```

---

# 🙏 Acknowledgments

- Java Development Team
- Jakarta EE Community
- Apache Tomcat Team
- MySQL Community
- Visual Studio Code
- Git and GitHub

---

# 🚀 Project Summary

The **Smart Canteen Ordering & Management System** demonstrates how Java web technologies can be integrated with a relational database to develop a complete canteen management application.

The system combines:

```text
Java
  +
JSP
  +
Servlets
  +
JDBC
  +
MySQL
  +
Apache Tomcat
```

to provide a complete workflow from **student registration and food selection to order placement, stock management, and administrator order tracking**.

---

<div align="center">

### 🍽️ Smart Canteen Ordering & Management System

**Built with Java, JSP, Servlets, JDBC and MySQL**

</div>

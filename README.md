# Online Store Database Structure Report

## Project Overview

This project involves designing and implementing a relational database for an Online Store using MySQL in XAMPP. The database is structured to manage essential entities such as products, customers, orders, and payments. It includes SQL queries that facilitate various operations related to customer orders, ensuring a seamless experience for both customers and store administrators.

## Technologies Used

- **Database**: MySQL
- **Platform**: XAMPP
- **File Format**: SQL script file (.sql)

## Database Structure

The database consists of four main tables, each serving a specific purpose:

### 1. Customers Table

This table stores detailed information about customers.

CREATE TABLE Customers (
CustomerID INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(100) NOT NULL,
Email VARCHAR(100) UNIQUE NOT NULL,
Phone VARCHAR(15),
Address TEXT
);

text

### 2. Products Table

This table contains details about the products available in the store.

CREATE TABLE Products (
ProductID INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(100) NOT NULL,
Description TEXT,
Price DECIMAL(10,2) NOT NULL,
Stock INT NOT NULL
);

text

### 3. Orders Table

This table records customer orders and their associated details.

CREATE TABLE Orders (
OrderID INT AUTO_INCREMENT PRIMARY KEY,
CustomerID INT,
OrderDate DATETIME DEFAULT CURRENT_TIMESTAMP,
TotalAmount DECIMAL(10,2),
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

text

### 4. Payments Table

This table tracks payment transactions related to orders.

CREATE TABLE Payments (
PaymentID INT AUTO_INCREMENT PRIMARY KEY,
OrderID INT,
PaymentDate DATETIME DEFAULT CURRENT_TIMESTAMP,
AmountPaid DECIMAL(10,2),
PaymentMethod VARCHAR(50),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

text

## Sample Queries

### Insert Sample Data

To populate the database with initial data, you can use the following SQL commands:

INSERT INTO Customers (Name, Email, Phone, Address) VALUES
('John Doe', 'john@example.com', '1234567890', '123 Main St');

INSERT INTO Products (Name, Description, Price, Stock) VALUES
('Laptop', 'Gaming Laptop', 1200.00, 10);

text

### Place an Order

To place an order for a customer:

INSERT INTO Orders (CustomerID, TotalAmount) VALUES (1, 1200.00);

text

### Process a Payment

To record a payment for an order:

INSERT INTO Payments (OrderID, AmountPaid, PaymentMethod) VALUES (1, 1200.00, 'Credit Card');

text

### Retrieve Order Details

To retrieve detailed information about orders:

SELECT Orders.OrderID, Customers.Name, Orders.OrderDate, Orders.TotalAmount
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

text

## How to Use

1. **Import the SQL file**: Load the SQL script into your MySQL database using XAMPP.
2. **Run Sample Queries**: Execute the provided queries to insert sample data and test transactions.
3. **Modify or Expand**: Feel free to modify or expand the database structure as needed to accommodate additional features or entities.

## Additional Features to Consider

To enhance the functionality of your online store database, consider implementing the following features:

- **Categories Table**: Organize products into categories for easier navigation.
- **Reviews Table**: Allow customers to leave reviews for products.
- **Shopping Cart Table**: Enable customers to save items before making a purchase.
- **Shipping Information Table**: Store shipping details for orders.

## Submission

The SQL script file (`store_database.sql`) contains all table creation statements and queries. Ensure that it runs without errors before submission.

## Author

[C MOHAMMED ZAID] - SQL Intern

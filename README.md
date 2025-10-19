# FINAL-DATA-TOOLS-PROJECT
# My Restaurant Ordering SQL Project

<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->

# 📗 Table of Contents

- [My SQL Project](#about-project)
- [📗 Table of Contents](#-table-of-contents)
- [📖 My SQL Project](#about-project)
  - [🛠 Built With ](#-built-with-)
    - [Tech Stack ](#tech-stack-)
    - [Key Features ](#key-features-)
  - [💻 Getting Started ](#-getting-started-)
    - [Prerequisites](#prerequisites)
    - [Setup](#setup)
    - [Usage](#usage)
  - [👥 Authors ](#-authors-)
  - [🔭 Future Features ](#-future-features-)
  - [🤝 Contributing ](#-contributing-)

<!-- PROJECT DESCRIPTION -->

# 📖 My SQL Project <a name="about-project"></a>

**My SQL Project** is a simple Database that uses SQL, Postgres via Supabase to create, query and secure a **Restaurant Ordering** database.

## 🛠 Built With <a name="built-with"></a>

### Tech Stack <a name="tech-stack"></a>
- SQL
- Postgres DB

<!-- Features -->

### Key Features <a name="key-features"></a>

- [ ] **Tables**
- [ ] **Schema**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## 💻 Getting Started <a name="getting-started"></a>

To rebuild this DB, follow these steps.

### Prerequisites

To run this project, you need:
- [A Supabase account](https://supabase.com/)
- [Knowledge on SQL](https://www.w3schools.com/sql/)
- A schema for creating your tables in the DB

<!-- ### Setup -->
### Setup

Copy the contents of this Readme.md to your Project's file

OR

Clone this repository to your desired folder:

```sh
  git clone https://github.com/joyapisi/readme-template-data
  cd restaurant-app
```

<!-- ### DB Creation -->

### DB Schema

- The DB is made up of 4 tables. Each table has 7 entries.
- To create the table, you will need a schema as shown below:

```sql
-- Drop old tables if they exist
DROP TABLE IF EXISTS orders ticket;
DROP TABLE IF EXISTS customers customer;
DROP TABLE IF EXISTS books room;
DROP TABLE IF EXISTS authors item;

-- Create customers table
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    phone_number VARCHAR(15) UNIQUE NOT NULL, 
    city VARCHAR(50) NOT NULL
);

<img width="975" height="429" alt="image" src="https://github.com/user-attachments/assets/d2fd6813-f9a5-4e58-8842-4b2e5c7bfab5" />
<img width="975" height="429" alt="image" src="https://github.com/user-attachments/assets/5542133c-3794-4310-8e40-423cbd7563c4" />


-- Create menu_items table
CREATE TABLE menu_items (
    item_id INT PRIMARY KEY,
    item_name VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL, 
    category VARCHAR(50) NOT NULL,
    is_available VARCHAR(3) NOT NULL 
);

-- Create orders table
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date DATE NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50) NOT NULL,
    order_type VARCHAR(50) NOT NULL,
    payment_method VARCHAR(50) NOT NULL
);

-- Create order_details table
CREATE TABLE order_details (
    order_detail_id INT PRIMARY KEY,
    order_id INT NOT NULL,
    item_id INT NOT NULL,
    quantity INT NOT NULL CHECK (quantity > 0), 
    unit_price DECIMAL(10, 2) NOT NULL
);

-- Insert customers (7 rows)
INSERT INTO customers (customer_id, first_name, last_name, phone_number, city) VALUES
(101, 'Alice', 'Johnson', '0722123456', 'Nairobi'),
(102, 'Bob', 'Smith', '0710987654', 'Mombasa'),
(103, 'Carol', 'Davis', '0733567890', 'Kisumu'),
(104, 'David', 'Lee', '0740234567', 'Nairobi'),
(105, 'Emma', 'Wilson', '0708876543', 'Nakuru'),
(106, 'Frank', 'Miller', '0791345678', 'Mombasa'),
(107, 'Grace', 'King', '0721456789', 'Eldoret');

-- Insert menu_items (7 rows)
INSERT INTO menu_items (item_id, item_name, price, category, is_available) VALUES
(201, 'Beef Samosa (2 pcs)', 150.00, 'Appetizer', 'Yes'),
(202, 'Pilau & Kachumbari', 450.00, 'Entree', 'Yes'),
(203, 'Ugali & Tilapia Fry', 600.00, 'Entree', 'Yes'),
(204, 'Hot Chips (Large)', 300.00, 'Side', 'Yes'),
(205, 'Cold Soda (300ml)', 100.00, 'Beverage', 'Yes'),
(206, 'Black Forest Cake Slice', 350.00, 'Dessert', 'No'),
(207, 'Fresh Mango Juice', 250.00, 'Beverage', 'Yes');

-- Insert orders (7 rows)
INSERT INTO orders (order_id, customer_id, order_date, total_amount, status, order_type, payment_method) VALUES
(3001, 101, '2024-10-13', 1050.00, 'Delivered', 'Delivery', 'M-Pesa'),
(3002, 104, '2024-10-13', 800.00, 'Ready for Pickup', 'Pickup', 'Cash'),
(3003, 103, '2024-10-12', 1800.00, 'Processing', 'Dine-in', 'Debit Card'),
(3004, 107, '2024-10-12', 300.00, 'Delivered', 'Delivery', 'M-Pesa'),
(3005, 102, '2024-10-11', 450.00, 'Canceled', 'Pickup', 'Credit Card'),
(3006, 105, '2024-10-11', 450.00, 'Pending', 'Dine-in', 'Debit Card'),
(3007, 106, '2024-10-11', 1200.00, 'Processing', 'Pickup', 'Cash');

-- Insert order_details (7 rows)
INSERT INTO order_details (order_detail_id, order_id, item_id, quantity, unit_price) VALUES
(4001, 3001, 202, 1, 450.00),
(4002, 3001, 203, 1, 600.00),
(4003, 3002, 204, 1, 300.00),
(4004, 3002, 207, 2, 250.00),
(4005, 3003, 203, 3, 600.00),
(4006, 3004, 201, 2, 150.00),
(4007, 3006, 201, 3, 150.00);

- The Tables should look like this in Supabase:
customers:


menu_items:


orders:


order_details:


- The ERD screenshot from Supabase looks like this: 


- To test the table, I used two queries: 

```sql
SELECT 
    item_id, 
    item_name, 
    price
FROM 
    menu_items
WHERE 
    is_available = 'No';
````

```sql
SELECT
    o.order_id,
    o.order_date,
    c.first_name || ' ' || c.last_name AS customer_full_name,
    o.total_amount,
    o.payment_method
FROM
    orders o
JOIN
    customers c ON o.customer_id = c.customer_id
ORDER BY
    o.order_date DESC;
````

- Here are the results of the queries:
<img width="975" height="433" alt="image" src="https://github.com/user-attachments/assets/a1c51ee9-19b7-493f-b84b-d0bfe274c937" />

<img width="975" height="605" alt="image" src="https://github.com/user-attachments/assets/4194d806-338f-45b1-8040-693aa239694e" />

<!-- AUTHORS -->

## 👥 Authors <a name="authors"></a>

👤 **Peninah Wanjiru**

- GitHub: [@penwanj](https://github.com/penwanj)
- Twitter: [@PeninahWan96693](https://x.com/PeninahWan96693)
- LinkedIn: [@Peninah Wanjiru](www.linkedin.com/in/peninah-wanjiru-3b9900200)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FUTURE FEATURES -->

## 🔭 Future Features <a name="future-features"></a>

- [ ] **Add security**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->

## 🤝 Contributing <a name="contributing"></a>

Contributions, issues, and feature requests are welcome!

Feel free to check the [issues page](../../issues/).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- SUPPORT -->

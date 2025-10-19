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

**My SQL Project** is a simple Database that uses SQL, Postgres via Supabase to create, query and secure a **Restaurant Ordering** database. Ideally, this database is designed to manage core transactions of a Kenyan restaurant ordering system.
The system handles customer information (including local phone number formats), manages the menu, tracks orders, and utilizes local payment methods (like M-Pesa and Debit Card).

## 🛠 Built With <a name="built-with"></a>

### Tech Stack <a name="tech-stack"></a>
- SQL
- Postgres DB
- dbdiagram.io

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
- knowledge on how to use dbdiagram.io to generate ERDs

<!-- ### Setup -->
### Setup

Copy the contents of this Readme.md to your Project's file

OR

Clone this repository to your desired folder:

```sh
  git clone https://github.com/penwanj/restaurant-app
cd restaurant-app
```

<!-- ### DB Creation -->

### DB Schema

- The database schema is defined in `schema.sql`.
- The DB is made up of 4 tables, each table having 7 records. 
- Execute the provided sql statements in `schema.sql` to generate your tables and their records.
- HOWEVER, before that, delete any existing tables using these sample statements adjusting the table names accordingly.

```sql
DROP TABLE IF EXISTS tickets;
DROP TABLE IF EXISTS dancer;
DROP TABLE IF EXISTS authors;
````

- The Tables should look like this in Supabase:
customers:
<img width="1055" height="469" alt="image" src="https://github.com/user-attachments/assets/bff700bf-0400-4c90-b9c7-65757423858e" />

menu_items:
<img width="1058" height="439" alt="image" src="https://github.com/user-attachments/assets/a211c5a5-038c-4d39-8df0-412e31065ff3" />

orders:
<img width="1056" height="473" alt="image" src="https://github.com/user-attachments/assets/64eb5128-61bf-463b-a759-e32e74b17e32" />

order_details:
<img width="1059" height="403" alt="image" src="https://github.com/user-attachments/assets/188aaa46-c266-48fb-b368-fba75abc2d42" />

-GENERATE ERD diagram using dbdiagram.io. by running all the statements provided in docs folder named `ERD source code`.

- The ERD screenshot from dbdiagram.io looks like this: 
<img width="1184" height="526" alt="image" src="https://github.com/user-attachments/assets/58c285f8-8cfa-4194-8303-9d7e7cb052f9" />

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
<img width="1004" height="448" alt="image" src="https://github.com/user-attachments/assets/ed582017-9f87-445c-bd60-3c7885ba1720" />

<img width="867" height="538" alt="image" src="https://github.com/user-attachments/assets/aac19533-5df0-4e73-b42b-cc611d4d6880" />

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

**Data Dictionary**: Restaurant Ordering Database

This dictionary provides a detailed breakdown of all tables, columns, data types, and constraints used in the Restaurant Ordering Database schema.

## 1. Table: `customers`

| Column Name | Data Type | Constraints | Description | 
| :--- | :--- | :--- | :--- | 
| **customer\_id** | `INT` | **Primary Key** | Unique identifier for the customer. | 
| first\_name | `VARCHAR(50)` | NOT NULL | Customer's first name. | 
| last\_name | `VARCHAR(50)` | NOT NULL | Customer's last name. | 
| phone\_number | `VARCHAR(15)` | **UNIQUE, NOT NULL** | Customer's phone number. | 
| city | `VARCHAR(50)` | NOT NULL | The customer's city of residence. |

## 2. Table: `menu_items`

| Column Name | Data Type | Constraints | Description | 
| :--- | :--- | :--- | :--- | 
| **item\_id** | `INT` | **Primary Key** | Unique identifier for each menu item. | 
| item\_name | `VARCHAR(100)` | NOT NULL | The commercial name of the item. | 
| price | `DECIMAL(10, 2)` | NOT NULL | Current selling price of the item. | 
| category | `VARCHAR(50)` | NOT NULL | Menu classification (e.g., 'Entree', 'Appetizer'). | 
| is\_available | `VARCHAR(3)` | CHECK ('Yes'/'No') | Status indicating if the item is currently in stock or available for order. |

## 3. Table: `orders`

| Column Name | Data Type | Constraints | Description | 
| :--- | :--- | :--- | :--- | 
| **order\_id** | `INT` | **Primary Key** | Unique identifier for the overall order transaction. | 
| **customer\_id** | `INT` | **Foreign Key** | Links the order to the purchasing customer. | 
| order\_date | `DATE` | NOT NULL | The calendar date the order was placed. | 
| total\_amount | `DECIMAL(10, 2)` | NOT NULL | The final calculated cost of the order. | 
| status | `VARCHAR(50)` | NOT NULL | The current fulfillment state (e.g., 'Processing', 'Delivered'). | 
| order\_type | `VARCHAR(50)` | NOT NULL | Method of fulfillment (e.g., 'Delivery', 'Pickup', 'Dine-in'). | 
| payment\_method | `VARCHAR(50)` | NOT NULL | The system used for payment (e.g., 'M-Pesa', 'Debit Card', 'Cash'). |

## 4. Table: `order_details`

| Column Name | Data Type | Constraints | Description | 
| :--- | :--- | :--- | :--- | 
| **order\_detail\_id** | `INT` | **Primary Key** | Unique identifier for this line item within the order. | 
| **order\_id** | `INT` | **Foreign Key** | Links the line item back to the main order transaction. | 
| **item\_id** | `INT` | **Foreign Key** | Links the line item to the specific product definition in `menu_items`. | 
| quantity | `INT` | NOT NULL | The number of units of this item ordered. | 
| unit\_price | `DECIMAL(10, 2)` | NOT NULL | The price of the item recorded at the moment of the order. |

Data Dictionary: Restaurant Ordering Database
This dictionary provides a detailed breakdown of all tables, columns, data types, and constraints used in the Restaurant Ordering Database schema.
Table Name	Column Name	Data Type	Key/Constraint	Description
customers	customer_id	INT	Primary Key	Unique identifier for the customer.
	first_name	VARCHAR(50)	NOT NULL	Customer's first name.
	last_name	VARCHAR(50)	NOT NULL	Customer's last name.
	phone_number	VARCHAR(15)	UNIQUE, NOT NULL	Customer's phone number.
	city	VARCHAR(50)	NOT NULL	The customer's city of residence.
menu_items	item_id	INT	Primary Key	Unique identifier for each menu item.
	item_name	VARCHAR(100)	NOT NULL	The commercial name of the item.
	price	DECIMAL(10, 2)	NOT NULL	Current selling price of the item.
	category	VARCHAR(50)	NOT NULL	Menu classification (e.g., 'Entree', 'Appetizer').
	is_available	VARCHAR(3)	CHECK ('Yes'/'No')	Status indicating if the item is currently in stock or available for order.
orders	order_id	INT	Primary Key	Unique identifier for the overall order transaction.
	customer_id	INT	Foreign Key	Links the order to the purchasing customer.
	order_date	DATE	NOT NULL	The calendar date the order was placed (without time component).
	total_amount	DECIMAL(10, 2)	NOT NULL	The final calculated cost of the order.
	status	VARCHAR(50)	NOT NULL	The current fulfillment state (e.g., 'Processing', 'Delivered').
	order_type	VARCHAR(50)	NOT NULL	Method of fulfillment (e.g., 'Delivery', 'Pickup', 'Dine-in').
	payment_method	VARCHAR(50)	NOT NULL	The system used for payment (e.g., 'M-Pesa', 'Debit Card', 'Cash').
order_details	order_detail_id	INT	Primary Key	Unique identifier for this line item within the order.
	order_id	INT	Foreign Key	Links the line item back to the main order transaction.
	item_id	INT	Foreign Key	Links the line item to the specific product definition in menu_items.
	quantity	INT	NOT NULL	The number of units of this item ordered.
	unit_price	DECIMAL(10, 2)	NOT NULL	The price of the item recorded at the moment of the order.


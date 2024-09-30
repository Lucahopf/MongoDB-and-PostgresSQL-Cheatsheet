# PostgreSQL / MongoDB Cheatsheet

> *this document was created as part of a student project if it is incomplete, please excuse us*
> *please note that some terms in the syntax of the SQL/NoSQL query commands contain german language*

## Content

- [PostgreSQL](#postgresql)
  - [Creating Tables]
      - [Creating the customer table and adding data](#customer-table1)
      - [Creating the product table and adding data](#product-table1)
      - [Creating the Shop Location table and adding data](#verkaufsstellen1)
  - [Select commands](#select)
  - [Updating Data in Queries](#update)
  - [Deleting Data in SQL Databases](#delete)
  
- [MongoDB](#mongodb)
  - [Erstellen des Customer Tables](#customer-table2)
  - [Erstellen des Product Tables](#product-table2)
  - [Erstellen des Verkaufsstellen Tables](#verkaufsstellen-table2)
  - [Create](#create-2)
  - [Insert](#insert-2)
  - [Select](#select-2)
  - [Update](#update-2)
  - [Delete](#delete-2)
  - [Lookup](#lookup)

---

# PostgreSQL


## Creating the Tables

**Creating The Customer Table and Adding Data**

```
CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    age INT,
    street VARCHAR(255),
    city VARCHAR(255),
    zip_code VARCHAR(20)
    product_id INT,
    order date VARCHAR(255),
    amount INT
);
```

**Adding Data to The Customers  Table**

```
INSERT INTO customers (name, email, age, street, city, zip_code, product_id, order_date, amount) VALUES
('Max Mustermann', 'max.mustermann@example.com', 35, 'Musterstraße 1', 'Musterstadt', '12345', '60f8f6c5e3b5a12d4c76f4a8', '2024-09-01', 2),
('Max Mustermann', 'max.mustermann@example.com', 35, 'Musterstraße 1', 'Musterstadt', '12345', '60f8f6c5e3b5a12d4c76f4b3', '2024-09-10', 1),
('Anna Beispiel', 'anna.beispiel@example.com', 28, 'Beispielweg 3', 'Beispielstadt', '54321', '60f8f6c5e3b5a12d4c76f4c2', '2024-08-15', 1),
('John Doe', 'john.doe@example.com', 42, 'Doe Lane 5', 'Doe City', '67890', '60f8f6c5e3b5a12d4c76f4a8', '2024-07-21', 3),
('John Doe', 'john.doe@example.com', 42, 'Doe Lane 5', 'Doe City', '67890', '60f8f6c5e3b5a12d4c76f4d7', '2024-07-30', 1); 
```


Credits:  Valentin H. 
          Julian S.
          Luca H.

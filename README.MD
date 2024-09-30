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

### Creating The Customer Table and Adding Data

```

CREATE TABLE Verkaufsstellen (
    id SERIAL PRIMARY KEY,
    store_name VARCHAR(255),
    street VARCHAR(255),
    city VARCHAR(255),
    zip_code VARCHAR(10),
    country VARCHAR(255),
    phone VARCHAR(20),
    email VARCHAR(255),
    monday VARCHAR(50),
    tuesday VARCHAR(50),
    wednesday VARCHAR(50),
    thursday VARCHAR(50),
    friday VARCHAR(50),
    saturday VARCHAR(50),
    sunday VARCHAR(50),
    available_products TEXT[]
);


```



Credits:  Valentin H. 
          Julian S.
          Luca H.

# PostgreSQL / MongoDB Cheatsheet

> *this document was created as part of a student project if it is incomplete, please excuse us*
> *please note that some terms in the syntax of the SQL/NoSQL query commands contain german language*

## Content

- [PostgreSQL](#postgresql)
  - [Creating Tables]  (#creating-tables)
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


## Creating Tables

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

**Creating The Products Table and Adding Data**

```
CREATE TABLE products (
	product_id SERIAL PRIMARY KEY,
	name VARCHAR(255),
	price DECIMAL(10, 2),
	available BOOLEAN,
	screen_size DECIMAL(4, 1),
	processor VARCHAR(255),
	storage VARCHAR(50),
	ram VARCHAR(50),
	features TEXT[],
	colors TEXT[],
	resolution VARCHAR(50),
	smart_tv BOOLEAN,
	sizes TEXT[],
	material VARCHAR(255),
	author VARCHAR(255),
	genre VARCHAR(255),
	camera VARCHAR(50),
	fit VARCHAR(50)
);
```

**Adding Data to The Products  Table**

```
INSERT INTO products (name, price, available, screen_size, processor, storage, ram) VALUES
('Tablet', 599, true, 10.5, 'Qualcomm Snapdragon 865', '256GB', '8GB');
INSERT INTO products (name, price, available, features, colors) VALUES
 ('Kopfhörer', 199, true, ARRAY['Noise-Cancelling', 'Bluetooth', '24h Akkulaufzeit'], 
ARRAY['schwarz', 'weiß']);
INSERT INTO products (name, price, available, screen_size, resolution, smart_tv) VALUES
 ('TV', 999, false, 55, '4K', true);
INSERT INTO products (name, price, available, sizes, material, colors) VALUES
 ('Jacke', 89.99, true, ARRAY['M', 'L', 'XL'], 'Polyester', ARRAY['rot', 'schwarz', 'grün']);
INSERT INTO products (name, price, available, sizes, material) VALUES
 ('Sneaker', 79.99, false, ARRAY[38, 39, 40, 41, 42], 'Leder');
INSERT INTO products (name, price, available, features) VALUES
 ('Staubsaugerroboter', 299, true, ARRAY['Automatische Aufladung', 'Wischfunktion', 'App-Steuerung']);
INSERT INTO products (name, price, available, author, genre) VALUES
 ('Harry Potter und der Stein der Weisen', 14.99, true, 'J.K. Rowling', 'Fantasy');
INSERT INTO products (name, price, available, screen_size, processor, storage, ram) VALUES
 ('Laptop', 1299, true, 15.6, 'Intel Core i7', '512GB SSD', '16GB');
INSERT INTO products (name, price, available, colors, camera) VALUES
 ('Smartphone', 799, false, ARRAY['schwarz', 'silber'], '50MP');
INSERT INTO products (name, price, available, features) VALUES
 ('Smartwatch', 349, true, ARRAY['Herzfrequenzmessung', 'Schlafverfolgung', 'Benachrichtigungen']);
INSERT INTO products (name, price, available, sizes, colors) VALUES
 ('T-Shirt', 19.99, true, ARRAY['S', 'M', 'L', 'XL'], ARRAY['weiß', 'schwarz', 'blau']);
INSERT INTO products (name, price, available, fit, material) VALUES
 ('Jeans', 69.99, true, 'slim', 'Denim');
INSERT INTO products (name, price, available, features) VALUES
 ('Kaffeevollautomat', 599, true, ARRAY['Milchaufschäumer', 'Aromawahl', 'Timer']);
INSERT INTO products (name, price, available, author, genre) VALUES
('Der kleine Prinz', 12.99, true, 'Antoine de Saint-Exupéry', 'Literatur');
```
 
**Creating The Shoplocation Table and Adding Data**

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


```
INSERT INTO Verkaufsstellen (store_name, street, city, zip_code, country, phone, email, monday, tuesday, wednesday, thursday, friday, saturday, sunday, available_products) VALUES
('Store Berlin Mitte', 'Alexanderplatz 1', 'Berlin', '10178', 'Deutschland', '+49 30 1234567', 'berlin-mitte@company.com', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 20:00', '10:00 - 18:00', 'Geschlossen', ARRAY['Laptop', 'Smartphone', 'Smartwatch']),
('Store München Zentrum', 'Marienplatz 12', 'München', '80331', 'Deutschland', '+49 89 9876543', 'muenchen-zentrum@company.com', '09:00 - 19:00', '09:00 - 19:00', '09:00 - 19:00', '09:00 - 19:00', '09:00 - 21:00', '10:00 - 19:00', 'Geschlossen', ARRAY['Kaffeevollautomat', 'Tablet', 'Kopfhörer']),
('Store Hamburg Altona', 'Große Bergstraße 15', 'Hamburg', '22767', 'Deutschland', '+49 40 7654321', 'hamburg-altona@company.com', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 18:00', '09:00 - 20:00', '10:00 - 18:00', 'Geschlossen', ARRAY['TV', 'T-Shirt', 'Staubsaugerroboter'])
```

To Show You How a database is going to look like We Use Here 

Result:
 

Insert
INSERT INTO customers (name, email, age, street, city, zip_code) VALUES
('Max Mustermann', 'max.mustermann@example.com', 35, 'Musterstraße 1', 'Musterstadt', '12345'),
('Anna Beispiel', 'anna.beispiel@example.com', 28, 'Beispielweg 3', 'Beispielstadt', '54321'),
('John Doe', 'john.doe@example.com', 42, 'Doe Lane 5', 'Doe City', '67890');

Select

Select:
`SELECT * FROM Verkaufsstellen`

Ergebnis:
 

Befehl:

```
SELECT id,
       street,
       city
FROM Verkaufsstellen
```

Ergebnis:
 

Befehl:
SELECT *FROM verkaufsstellen
WHERE city= ‘Berlin’
Ergebnis:
 


Befehl:
SELECT store_name, street, city FROM verkaufsstellen
WHERE city = 'Berlin'

Ergebnis:
 

Befehl:
SELECT * FROM verkaufsstellen
WHERE city != 'Berlin'

Ergebnis:
 

Befehl:
SELECT * FROM verkaufsstellen
WHERE city = 'Berlin' AND zip_code = '10178'

Ergebnis:
 

Befehl:
SELECT * FROM Verkaufsstellen
WHERE city = 'Berlin' OR city = 'München'

Ergebnis:
 

 
Befehl:
SELECT * FROM Verkaufsstellen WHERE id > 1

Ergebnis:
 

Befehl:
SELECT * FROM Verkaufsstellen WHERE id < 2

Ergebnis:
 

Befehl:
SELECT * FROM Verkaufsstellen WHERE id < 4 AND id > 2

Ergebnis:
 

Befehl:
SELECT * FROM Verkaufsstellen WHERE city like '%burg%'

Ergebnis:
 

 
Befehl:
SELECT * FROM Verkaufsstellen WHERE zip_code like '22%'

Ergebnis:
 

Befehl:
SELECT * FROM customers
WHERE email LIKE '%example.com%' ORDER BY age ASC

Ergebnis:
 

Befehl:
SELECT * FROM customers
WHERE email LIKE '%example.com%' ORDER BY age DESC

Ergebnis:
 

Befehl:
SELECT COUNT(*) FROM customers

Ergebnis:
 

Befehl:
SELECT COUNT (age) FROM customers

Ergebnis:
 

Befehl:
SELECT COUNT(*) FROM customers WHERE age > 30

Ergebnis:
 

Befehl:
SELECT DISTINCT(age) FROM customers

Ergebnis:
 

 
Befehl:
SELECT * FROM customers LIMIT 1

Ergebnis:
 

Befehl:
SELECT * FROM customers LIMIT 2 OFFSET 2;

Ergebnis:
 

Befehl:
EXPLAIN SELECT * FROM customers WHERE age = '28'

Ergebnis:
 


 
Update
UPDATE verkaufsstellen
SET montag = 'Geschlossen', dienstag = 'Geschlossen', mittwoch = 'Geschlossen'
WHERE name = 'Store Hamburg Altona';

 
Output: 
 

Delete

DELETE FROM verfügbare_produkte
WHERE produkt_name = 'Smartwatch' AND verkaufsstelle_id = 1;


 
MongoDB
Erstellen des Customer Tables
db.customers.insertMany([
{ name:"MaxMustermann",email:"max.mustermann@example.com",
age: 35, address: {street: "Musterstraße 1", city: "Musterstadt",zipCode: "12345" },    orders: [       
{productId: "60f8f6c5e3b5a12d4c76f4a8", date: "2024-09-01", amount: 2 },       
{productId: "60f8f6c5e3b5a12d4c76f4b3", date: "2024-09-10", amount: 1 }     ]  }, 
 { name: "Anna Beispiel",email: "anna.beispiel@example.com",     age: 28,     address: {       street: "Beispielweg 3",       city: "Beispielstadt",       zipCode: "54321"    },    orders: [       { productId: "60f8f6c5e3b5a12d4c76f4c2", date: "2024-08-15", amount: 1 }     ]  },  {    name: "John Doe",     email: "john.doe@example.com",     age: 42, address: { street: "Doe Lane 5", city: "Doe City", zipCode: "67890" }, orders: [ { productId: "60f8f6c5e3b5a12d4c76f4a8", date: "2024-07-21", amount: 3 }, { productId: "60f8f6c5e3b5a12d4c76f4d7", date: "2024-07-30", amount: 1 } ] } ]);

Ergebnis:
 

Erstellen des Product Tables
db.products.insertMany([{name:"Tablet",price:599,available:true,specs:{screenSize:10.5,processor:"Qualcomm Snapdragon 865",storage:"256GB",ram:"8GB"}},{name:"Kopfhörer",price:199,available:true,features:["Noise-Cancelling","Bluetooth","24h Akkulaufzeit"],colors:["schwarz","weiß"]},{name:"TV",price:999,available:false,specs:{screenSize:55,resolution:"4K",smartTV:true}},{name:"Jacke",price:89.99,available:true,sizes:["M","L","XL"],material:"Polyester",colors:["rot","schwarz","grün"]},{name:"Sneaker",price:79.99,available:false,sizes:[38,39,40,41,42],material:"Leder"},{name:"Staubsaugerroboter",price:299,available:true,features:["Automatische Aufladung","Wischfunktion","App-Steuerung"]},{name:"Harry Potter und der Stein der Weisen",price:14.99,available:true,author:"J.K. Rowling",genre:"Fantasy"}]);
db.products.insertMany([ {    name: "Laptop",     price: 1299,     available: true,     specs: {       screenSize: 15.6,       processor: "Intel Core i7",       storage: "512GB SSD",       ram: "16GB"    }  },  {    name: "Smartphone",     price: 799,     available: false,     colors: ["schwarz", "silber"],     camera: "50MP"  },  {    name: "Smartwatch",     price: 349,     available: true,     features: ["Herzfrequenzmessung", "Schlafverfolgung", "Benachrichtigungen"]   },  {    name: "T-Shirt",     price: 19.99,     available: true,     sizes: ["S", "M", "L", "XL"],     colors: ["weiß", "schwarz", "blau"]   },  {    name: "Jeans",     price: 69.99,     available: true,     fit: "slim",     material: "Denim" },  { name: "Kaffeevollautomat", price: 599, available: true, features: ["Milchaufschäumer", "Aromawahl", "Timer"] }, { name: "Der kleine Prinz", price: 12.99, available: true, author: "Antoine de Saint-Exupéry", genre: "Literatur" } ]);





Ergebnis:
 

Erstellen des Verkaufsstellen Tables
db.verkaufsstellen.insertMany([{name:"Store Berlin Mitte",adresse:{straße:"Alexanderplatz 1",stadt:"Berlin",postleitzahl:"10178",land:"Deutschland"},kontakt:{telefon:"+49 30 1234567",email:"berlin-mitte@company.com"},öffnungszeiten:{montag:"09:00 - 18:00",dienstag:"09:00 - 18:00",mittwoch:"09:00 - 18:00",donnerstag:"09:00 - 18:00",freitag:"09:00 - 20:00",samstag:"10:00 - 18:00",sonntag:"Geschlossen"},verfügbareProdukte:["Laptop","Smartphone","Smartwatch"]},{name:"Store München Zentrum",adresse:{straße:"Marienplatz 12",stadt:"München",postleitzahl:"80331",land:"Deutschland"},kontakt:{telefon:"+49 89 9876543",email:"muenchen-zentrum@company.com"},öffnungszeiten:{montag:"09:00 - 19:00",dienstag:"09:00 - 19:00",mittwoch:"09:00 - 19:00",donnerstag:"09:00 - 19:00",freitag:"09:00 - 21:00",samstag:"10:00 - 19:00",sonntag:"Geschlossen"},verfügbareProdukte:["Kaffeevollautomat","Tablet","Kopfhörer"]},{name:"Store Hamburg Altona",adresse:{straße:"Große Bergstraße 15",stadt:"Hamburg",postleitzahl:"22767",land:"Deutschland"},kontakt:{telefon:"+49 40 7654321",email:"hamburg-altona@company.com"},öffnungszeiten:{montag:"09:00 - 18:00",dienstag:"09:00 - 18:00",mittwoch:"09:00 - 18:00",donnerstag:"09:00 - 18:00",freitag:"09:00 - 20:00",samstag:"10:00 - 18:00",sonntag:"Geschlossen"},verfügbareProdukte:["TV","T-Shirt","Staubsaugerroboter"]}]);

Ergebnis:
 

Create
Befehl:
db.createCollection("Distributionszentren")

Ergebnis:
 

Insert
Befehl:
db.customers.insertOne({ name: "Frieda Meier", email: "frieda.meier@example.com", age: 35, address: { street: "Kaßberg 2 city: "Chemnitz", zipCode: "09112" }, orders: [ { productId: "60f8f6c5e3b5a12d4c76f4a8", date: new Date("2024-09-01"), amount: 2 }, { productId: "60f8f6c5e3b5a12d4c76f4b3", date: new Date("2024-09-10"), amount: 1 } ] });

Ergebnis:
 
 
Select

Befehl:
db.customers.find()
Ergebnis:
 

Befehl:
db.products.findOne(
    { _id: ObjectId("66f4f62bc9c44ec86ce24182") },
);

Ergebnis:
 

 
Befehl:
db.products.findOne(
    { _id: ObjectId("66f4f62bc9c44ec86ce24182") },
    { colors: 1 }
);

Ergebnis:
 

Befehl:
db.products.find({ price: { $eq : 599 }})

Ergebnis:
 


Befehl:

db.products.find(
    { price:{ $ne: 599 } }
)

Ergebnis:
 
 

Befehl:
db.products.find(
    { name: "T-Shirt",
      price: 19.99 }
)

Ergebnis:
 


Befehl:
db.products.find(
    { $or: [ { price: 999 } , { name: "Kaffeevollautomat" } ] }
)

Ergebnis:
 


Befehl:
db.products.find(
    { price: { $gt: 100 } }
)

Ergebnis:
 
 

Befehl:
db.products.find(
    { price: { $lt: 100 } }
)

Ergebnis:
 

Befehl:
db.products.find(
   { price: { $gt: 50, $lte: 500 } }
)

Ergebnis:
 

Befehl:
db.products.find( { name: /Shirt/ } )

Ergebnis:
 

Befehl:
db.products.find({ "name": { $regex: /v/i } })

Ergebnis:
 

Befehl:
db.products.find( { available: true, } ).sort( { price: 1 } )
Ergebnis:
 

Befehl:
db.products.find( { available: true, } ).sort( { price: -1 } )

Ergebnis:
 

Befehl:
db.products.count()

Ergebnis:
 

Befehl:
db.products.count({ available: false });

Ergebnis:
 



Befehl:
db.products.count( { price: { $gt: 300 } } )
Ergebnis:
 

Befehl:
db.products.aggregate( [ { $group : { _id : "$available" } } ] )

Ergebnis:
 

Befehl:
db.products.findOne()

Ergebnis:
 

Befehl:
db.products.find().limit(5).skip(9)

Ergebnis:
 
 
Befehl:
db.products.find( { price: "599" } ).explain()

Ergebnis:
  

 

Update
Befehl:
db.verkaufsstellen.updateOne( { name: "Store Hamburg Altona" },  { $set: { öffnungszeiten: { montag: "geschlossen", dienstag: "09:00 - 18:00", mittwoch: "09:00 - 18:00", donnerstag: "09:00 - 20:00", freitag: "09:00 - 20:00", samstag: "geschlossen", sonntag: "geschlossen" } } } );

Ergebnis:
 

Delete
Befehl:
db.verkaufsstellen.deleteOne({ name: "Store München Zentrum" });

Ergebnis: 
 
Lookup
Befehl:
db.products.aggregate([
  { $lookup: {from: "customers",localField: "66f40472b4a93e69582c044c",         
      foreignField: "customers.productId", 
      as: "customers_who_ordered"} }
]);


Ergebnis:
Hier ein Screenshot des Ergebnis des Commands:
 

Volle Länge des Outputs findet man im Anhang 
(wirdd. Als. Verknüpfter Link zu einem Onedrive. Directory Realisiert)



Credits:  Valentin H. 
          Julian S.
          Luca H.

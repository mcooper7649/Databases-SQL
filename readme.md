### Databases
---

Databases Explained: SQL VS NOSQL

- Databases allow the userdata to persist.
- So in previous modules, when we restart the server, our data was gone.
- Databases will allow us to keep that data.


SQL and NOSQL are the two types of databases.

SQL = Structured Query Language

- SQL is an older type of DB that has been in use for years, lots of existing business run on SQL.


NOSQL =  Not Only Structured Query Language

- NOSQL can be either format


## Popular SQL Platforms 
---

1. MySQL
2. PostgreSQL

## Popular NoSQL Platforms 
---

1. mongoDB
2. redis


## SQL Databases
---

1. Not Very Flexible
    - For Example, if your DB doesn't support email but your client only want to contact w/ email. SQL will square off the new categorie, email, that is created, thus all previous accounts will return null when email is accessed.
    - Null, can be dangerous as it can break automations.

2. Relational Database 
    - SQL is better at being relational, as it allows groups of dbs to link up together. For example, if you have a customers table, products table, and orders table, if they shared common fields, we can see the relationship better between each customers orders.

3. SQL Databases can grow vertically, fast and make it a very expensive db down the road.

4. SQL has been around for ages, technology is more mature.

5. SQL works in a TABLE Structure

6. SQL requires a Schema. (Columns and Tables pre-specified)




## NoSQL Databases
---

1. More Flexible
    - In a NoSQL DB like mongo, we return JSON objects so our blob of data doesn't return any null key value pairs

2. Non-Relational Database 
    - NoSQL can be linked together in a similiar fashion as SQL but since they are all Objects or Embedded objects it gets more clumsy.

3. NoSQL store their data in JSON objects so it can grow more dynamically while keep the costs lower in comparison. JSON objects can be easily distributed that how it can grow while also keeping the price/performance scalable.

4. MongoDB is shiny and new, but their are more changes, frequently.

5. MongoDB works in a Document Structure.

6. MongoDB is more flexible to changes to the db, as a schema isn't required.


## Choosing a DB
---

- It is very situational on which DB you want to select to achieve the best outcome.
- If you have an exisitng DB with lots of relationships between each other, you might be better off choosing SQL as your DB.
- If you have a DB where your relationships may vary significiantly, think instagram with user posts, ie arrays and lots of content,  you would likely want to use a more flexible DB like mongoDB.
- SQL will outperform NoSQL in relationship queries
- NoSQL is much more flexible and better for startups
- SQL Scales Vertically, costs more, while NoSQL scales horizontally, cheaper.


### Structure Query Language
---

[w3schools/sql](w3schools.com/sql)
[sql-testingDB](https://sqliteonline.com/)  | Lets you get familiar with the language

- With Every Single DB we have the things we will do to the data. CRUD is the acronym
    - Create
    - Read
    - Update
    - Destroy
    
- How to create a table to store int, string and store a monetary value, for price.
```
 CREATE TABLE products (
    id INT,
    name STRING,
    price MONEY,
   ....
);

```

- Primary Keys will assign a unique id to an item in our table, in thix example the product. This primary key will only be assigned to the ID of this product, we will also add the NOT NULL so every product has to have an ID.

## Scheme Creation for the products table
---

- Schema Format

```
 CREATE TABLE products (   
    id INT NOT NULL,
    name STRING,
    price MONEY,
    PRIMARY KEY (id)
   ....
);

```

## Insert Data into Table
---

- If you are going to insert data for each and every column use insert code below

```
INSERT INTO products
VALUES (1, "pen", 1.20)

```

- If you were to go to your products table and right click "Show table" you will now see your Pen we added


- If you are going to insert data but we don't yet have the values for all the columns. You must specify the column in parenthesis that you do have values for.

```
INSERT INTO products (id, name)
VALUES (2, "pencil")

```

- If you were to try to insert a product but don't specify the ID information, you will be prompted with "Not NULL" constraint error. Remember this is due to the schemea "NOT NULL" we assigned to the ID.

## Read, Select, Where
---

How to read the data from a SQL database

```
SELECT * FROM 'products';  // This returns all the columns from the prodcuts table

SELECT name, price FROM 'products';  // This returns only the the columns we specified; name and price

SELECT * FROM 'products' WHERE id=1;  // This returns all columns from products where the id is equal to 1.

```

## Updating Records in a SQL DB
---


How to update a product
```
UPDATE products   // Updates our products table or collection
SET price = 0.80 // Sets the price column value to 0.80
WHERE id = 2  // Specifies that where id=2 only will be updated
```


How to add a column 


```
ALTER TABLE table_name   // Example from w3 schools
ADD column_name datatype;  // Example from w3 schools


ALTER TABLE products  // How we would do it for our challenge
ADD stock INT;  // How we would do it for our challenge

```



## Updating Records in a SQL DB Challenge
---

1. How would you update our pen and pencil so the pen has 32 stock and 12 for the pencil?

```
UPDATE products
SET stock = 32
WHERE id = 1  

UPDATE products
SET stock = 12
WHERE id = 2

```


## Deleting Records in a SQL TABLE DB
---

```
DELETE FROM table_name   // Example from w3
WHERE condition;        // Example from w3

DELETE FROM products  // Deletes ALL items from products table if no WHERE specified
WHERE id = 2   // Specifies the ID we are deleteing, try to use ID when possible.
```

## Add Pencil Records Challenge
---

- Add the Pencil product we just deleted

```

INSERT INTO products
VALUES (2, "pencil", 0.80, 12)

```


## Understanding SQL Relationships and Forgein Keys and Inner joins
---

- While the Primary Key lets you assign a column to create a unique ID, a FOREIGN key lets you link tables together.
- In our table below our first foreign key is assigned to the customer_id column that REFERENCES the customers table (id) column. Making a relationship that can be referenced later.
- In our table below our second foreign key is assigned to the product_id column that REFERENCES the products table (id) column. Making a relationship that can be referenced later.


```
CREATE TABLE orders(
    id INT NOT NULL,
    order_number INT,
    customer_ID INT,
    product_ID INT,
    PRIMARY KEY (id),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
    FOREIGN KEY (product_id) REFERENCES products(id)
)
```


- Lets Insert our first order

```
INSERT INTO orders
VALUES (1, 4362, 2, 1)

```

- Lets Inner JOIN our tables where a foreign key matches. This will allow us to access data that is connected via a foreign key


```
SELECT orders.order_number, customers.first_name, customers.last_name, customers.address
FROM orders
INNER JOIN customers ON orders.customer_id = customers.id

// Returns Order number from orders table, but firstname, lastname and address from customers table.
```


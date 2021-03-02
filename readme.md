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
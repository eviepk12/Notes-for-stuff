---
title: Notes for SQL and Database related subjects
tags: [SQL, Database]
---

## Definitions

- A database is any **collection of related information** i.e (phone book, todo list, shopping list, etc)
- Databases can be stored in different ways i.e (on paper, in your mind, computer, etc)
- Database Management Systems *(DBMS)* is a special software that helps users create and maintain a database
- C.R.U.D (Create, Read, Update, Delete) is the 4 main pillars of operations in a database

### Type of Databases

1. Relational Databases(SQL)
Organises data into one or more tables which each table has columns and rows and a unique key to identify each row
2. Non-Relational Databases(NoSQL)
Organise data with anything but a traditional table i.e documents like JSON, XML, graphs, flexible tables, etc

- query is a request made to the database system for a specific piece information according to the conditions set out by your particular need

## Tables and Keys

- Every table has 2 distinct aspects

1. Columns
The vertical section of a table which represents the attribute of that particular column (can be remembered as a vertical column on a building)
2. Rows
The horizontal section of a table which represents a single entry of the given object (i.e a student in the student table)

- Every table has a special column called the "Primary Key" which is used to uniquely define a particular row in the database (usually using a particular attribute that cannot have doubles to other attributes)

### Types of a Primary Key

1. Surrogate Key
A type of primary key that has no real meaning in the real word is called a "Surrogate Key" which can take form in a random set of numbers or an incrementing number based on the table
2. Natural Key
A natural key is a key which has meaning or representation in the real world i.e NIK, NIS, effect
3. Foreign Key
A foreign key is a key that

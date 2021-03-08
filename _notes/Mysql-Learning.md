---
layout: collection_item
title:  "Mysql Notes"
category: sql
tags: mysql, sql
---

#Mysql learning Notes 

## How to connect to a mysql database from command line:
Important options while connecting:
<br>
`-h`  : host <br/> 
`-u` : username <br/> 
`-p`: ask for passoword after pressing enter if don't mention the password immediately after it without any spacing
```bash
mysql -h host -u user -p 
```
or
```bash
mysql -h host -u user -pmypassword
```
**If we add an space after `-p` then the program will think it as a database** <br>
#### we can also pass on the database name to use it:
```mysql 
mysq -h host -u user -p database_name
```

### close mysql prompt
```mysql
quit
```
**We don't need any semecolon after `quit` statement**


Some basic mysql command and functions that you should know.
<br/>
**Shows the current user:**
```mysql
SELECT USER();
```
**Shows the current time:**
```mysql
SELECT NOW(), CURRENT_TIMESTAMP(); 
SELECT CURRENT_TIME(), CURRENT_DATE();
```
**Shows the current version:**
```mysql
SELECT VERSION();
```
#### SHOW LIST OF ALL DATABASES:
```mysql
show databases;
```
#### Work on a specific database
**`use` statement doesn't need a semicolon at the end of the statement.**
```mysql
use test
```

## Date Calaculation 
**Calaculate time difference**
```mysql
SELECT name, birth, CURDATE(), TIMESTAMPDIFF(YEAR, birth.CURDATE()) AS age FROM pet;
```
**Get month / year/ day**
```mysql
SELECT name, birth FROM pet WHERE MONTH(birth) = 12
```
**Inteval**
```mysql
SELECT CURDATE() + INTERVAL 1 DAY
```

**Comparing something with `null`**
To compare something with null we need to use `IS` Keyword.
```
SELECT 1 IS NULL;
```
Results:  `false`

## Pattern Matching:
**Select name that starts with `B`**:
```
SELECT * FROM pet WHERE name LIKE 'B%'; 
```
**Select name that ends with `B`**:
```
SELECT * FROM pet WHERE name LIKE '%B'; 
```
**Select name that contains `B`**:
```
SELECT * FROM pet WHERE name LIKE '%B%'; 
```
**Select all names with only 3 charachters**:
```mysql 
SELECT * FROM pet WHERE name LIKE '___';
``` 
**Select using regexp**
```mysql 
SELECT * FROM pet WHERE REGEXP_LIKE(name, '^.{5}$`)
```

## MANAGING USERS AND THIER PERMISSIONS
Grant access to a full database to a user:
```mysql
GRANT ALL ON test.* TO 'username@host';```

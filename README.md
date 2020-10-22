# addressbook-mysql
### UC1 - Create database for addressbook service
```
create database address_book_service;
```
### see the DB created using show database query
```
show databases;
```

### Go to the database created 
```
use address_book_service;
```
### UC2 - Create addressbook table with necessary details
```
CREATE TABLE address_book
    -> (
    ->    firstName                      VARCHAR(150) NOT NULL,
    ->    lastName                       VARCHAR(150) NOT NULL,
    ->    address                        VARCHAR(150) NOT NULL,
    ->    city                           VARCHAR(250) NOT NULL,
    ->    state                          VARCHAR(300) NOT NULL,
    ->    zip                            int(11),
    ->    phnNum                         int(11),
    ->    email                          VARCHAR(300),
    ->    PRIMARY KEY                    (firstName)
    -> );
```
### viewing the address book table
```
DESCRIBE address_book;
```
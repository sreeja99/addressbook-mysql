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
### UC3 - Insert new contacts to address book
```
INSERT INTO address_book(firstName,lastName,address,city,state,zip,phnNum,email) VALUES
    -> ('sreeja','godishala','hnk','wgl','telangana',1234,1234567,'srijagodishala@gmail.com'),
    -> ('krishna','sodha','naimnagar','karimnagar','telangana',874884,12340987,'krishna121@gmail.com'),
    -> ('aarush','sharma','madhavnagar','wgl','telangana',32341,4321453332,'aarushsharama@gmail.com');
    -> ('harini','burra','bank colony','huzrabad','andra pradesh',43453,12334231,'sriharini35@gmail.com');
```
### View address book
```
SELECT*FROM address_book;
```
### UC4 - Ability To Edit Existing Contact with Name
### changing city for given name
```
UPDATE address_book set city='medak' where firstName='krishna';
```
### changing state for given name
```
UPDATE address_book set state='andhra pradesh' where firstName='sreeja';
```
### viewing address book
```
SELECT*FROM address_book;
```

### UC5 - Ability To Delete Existing Contact with Name
```
DELETE FROM address_book WHERE firstName='krishna';
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC6  -Ability to Retrieve Person belonging to a City or State 
### contact of person belonging to particular state
```
 SELECT * FROM address_book WHERE state='telangana';
```
### contact of person belonging to particular city
```
 SELECT * FROM address_book WHERE city='wgl';
```
### contact of person belonging to particular state and city
```
 SELECT * FROM address_book WHERE state='telangana' and city='hyderabad';
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC7 -  Ability to understand the size of address book by City and State
### count of number of cities
```
SELECT COUNT(city) FROM address_book;
```
### count of number of states
```
SELECT COUNT(state) FROM address_book;
```
### count of contacts having same state
```
SELECT COUNT(state) FROM address_book WHERE state='andhra pradesh';
```
### count of contacts having same city
```
SELECT COUNT(city) FROM address_book WHERE city='wgl';
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC8  - Ability to retrieve entries sorted alphabetically by Person’s name for a given city
### for a given city ,sort contacts in alphabetical order
```
 SELECT * FROM address_book WHERE city='wgl'
    -> ORDER BY firstName;
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC9 -  Ability to identify each Address Book with name and Type.
```
 ALTER TABLE address_book ADD type VARCHAR(300) AFTER email;
 update address_book set type='Family' where firstName='aarush';
 update address_book set type='Friends' where firstName='sreeja';
 update address_book set type='Professional' where firstName='harini';
 update address_book set type='Family' where firstName='aditya';
```
### showing which is of which type and grouping by type
```
 SELECT type,firstName FROM address_book;
 SELECT type,firstName FROM address_book group by type;
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC10  -  Ability to get number of contact persons(count by type)
```
SELECT COUNT(type) FROM address_book
```
### viewing address book
```
SELECT*FROM address_book;
```


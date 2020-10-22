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
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

### UC11  -  Ability to add person to both Friend and Family
```
  INSERT INTO address_book(firstName,lastName,address,city,state,zip,phnNum,email,type) VALUES
    -> ('rohit','bandi','ram nagar','bhopal','Madhya pradesh',42834,12323121,'rohitbandi@gmail.com','Friends'),
    -> ('rahul','konda','ambedkar nagar','hanamkonda','Telangana',56325,12413235,'rahulkonda@gmail.com','Family');
```
### viewing address book
```
SELECT*FROM address_book;
```
### UC13 - Ensure all queries are done
### create table address_book and Contacts
```
 CREATE TABLE Address_book_name_and_type
    -> (
    ->  Address_book_name          VARCHAR(20) NOT NULL PRIMARY KEY,
    ->  Address_book_type            VARCHAR(100) NOT NULL
    -> );

mysql> CREATE TABLE Contacts
    -> (
    ->  first_name        VARCHAR(100) NOT NULL,
    ->  last_name         VARCHAR(100) NOT NULL,
    ->  Address_book_name VARCHAR(20) REFERENCES Address_book_name_and_type( Address_book_name),
    ->  Address           VARCHAR(100) NOT NULL,
    ->  City              VARCHAR(100) NOT NULL,
    ->  State             VARCHAR(100) NOT NULL,
    ->  Phone_Number      VARCHAR(100) NOT NULL,
    ->  Email_id          VARCHAR(100) NOT NULL,
    ->  Zip               INT(20) NOT NULL
    -> );
```
### insert into address book
```
 INSERT INTO  Address_book_name_and_type VALUES
    -> ('first contact','Friends'),
    -> ('second contact','Family'),
    -> ('third contact','Professional');
```
### insert into contacts
```
 INSERT INTO Contacts VALUES
    ->  ('sreeja','godishala','first contact','hnk','wgl','telangana','875429','srijagodishala@gmail.com',123456),
    ->  ('aditya','burra','second contact','bank colony','karimnagar','telangana','74576573','adityareddy@gmail.com',462786),
    ->  ('harini','varma','third contact','madhav nagar','bhopal','madhya pradesh','74372723','harinivarma@gmail.com',635314);
```
### view table
```
 select*from Contacts;
 select*from  Address_book_name_and_type;
```
### retrieve person's data according to city or state
```
 SELECT*FROM Contacts where city='wgl';
 SELECT*FROM Contacts where State='madhya pradesh';
 SELECT*FROM Contacts where Address_book_name=(SELECT Address_book_name FROM Address_book_name_And_type where Address_book_type='Family');
```
### Ability to understand the size of address book by City and State
```
SELECT City,COUNT(City) FROM Contacts GROUP BY City;
 SELECT State,COUNT(State) FROM Contacts GROUP BY State;
```
### Ability to retrieve entries sorted alphabetically by Person’s name for a given city
```
 SELECT *FROM Contacts where City='karimangar' GROUP BY first_name;
```
### Ability to get number of contact persons i.e. count by type
```
SELECT Address_book_name_And_type.Address_book_type,COUNT(Address_book_name_And_type.Address_book_type) FROM Address_book_name_And_type INNER JOIN Contacts ON
    -> Address_book_name_And_type.Address_book_name=Contacts.Address_book_name;
```


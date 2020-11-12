# Apartment-sales-systems
Database
--Zhassulan, Shantima
CREATE TABLE Manager1 (

manager_id CHAR(4) NOT NULL,

fname VARCHAR(15) NOT NULL,

lname VARCHAR(15) NOT NULL,

mbdate DATE NOT NULL,

msalary DECIMAL (32) NOT NULL,

PRIMARY KEY (manager_id)

);


CREATE TABLE Building2 (

building_id CHAR(3) NOT NULL,

building_name VARCHAR (16),

numof_floors INT NOT NULL,

manager_id CHAR(4) NOT NULL,

PRIMARY KEY (building_id),

FOREIGN KEY (manager_id) REFERENCES

Manager1(manager_id)

);
--each manager has a selling building and each selling building has its manager.

CREATE TABLE Manager_contact (

manager_id CHAR(4) NOT NULL,

m_contact CHAR(11) NOT NULL,

PRIMARY KEY (manager_id, m_contact),

FOREIGN KEY (manager_id) REFERENCES Manager1 (manager_id)

);
--each manager has his/her contacts.

CREATE TABLE sale_man (

saleman_id CHAR(3) NOT NULL UNIQUE,

saleman_name VARCHAR(15) NOT NULL,

num_ofsails CHAR (3),

salary_saleman DECIMAL (32) NOT NULL

);


CREATE TABLE selling (

selling_id CHAR(3) NOT NULL,

building_id CHAR(3) NOT NULL,

manager_id CHAR(4) NOT NULL,

PRIMARY KEY (selling_id),

FOREIGN KEY (building_id) REFERENCES

Building2(building_id)

);
--each selling has its sold building, but not each building may have its bill.

CREATE TABLE Client (

client_id CHAR(4) NOT NULL,

client_fname VARCHAR(25) NOT NULL,

client_lname VARCHAR(25) NOT NULL,

client_contact decimal(25) NOT NULL,

PRIMARY KEY (client_id)

);

CREATE TABLE apartment (

building_id CHAR(3) NOT NULL UNIQUE,

apartment_id CHAR(4) NOT NULL,

numof_room CHAR(4) NOT NULL,

numof_floor CHAR(4) NOT NULL

);

CREATE TABLE repair (

building_id CHAR(3) NOT NULL,

numof_room CHAR(5) NOT NULL,

costof_repair CHAR(16) NOT NULL,

PRIMARY KEY (numof_room,

costof_repair ),

FOREIGN KEY (building_id)

REFERENCES Building2(building_id)

);
--each repair process has its reconstructed object (building), but not all buildings may be reconstructed.

CREATE TABLE price(

building_id CHAR(3) NOT NULL,

squaremeter_price CHAR(16) NOT NULL,

PRIMARY KEY (squaremeter_price),

FOREIGN KEY (building_id)

REFERENCES Building2(building_id)

);
--each building has its price in squaremeter.

CREATE TABLE build_age(

building_id CHAR(3) NOT NULL,

numof_year CHAR(5) NOT NULL,

PRIMARY KEY (numof_year),

FOREIGN KEY (building_id)

REFERENCES Building2(building_id)

);
--each building has a data about its year of being built.

select * from Manager1, Building2, Manager_contact, selling, sale_man, Client, apartment, repair, price, build_age;

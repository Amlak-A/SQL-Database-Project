CREATE DATABASE store;

create table countries(
    code int(10) primary key ,
    name varchar(20) unique,
    continent_name varchar(20) not null
);

create table users(
    id int(10) primary key ,
    full_name varchar(20),
    email varchar(20) unique,
    gender char(1) check(gender='m' or gender='f'),
    data_of_birth varchar(15),
    created_at datetime default CURRENT_TIMESTAMP,
    country_code int(10),
    foreign key (country_code) references countries(code) 
);

create table orders(
    id int(10) primary key ,
    user_id int(10),
    status varchar(6) check(status='start' or status='finish'),
    created_at datetime default CURRENT_TIMESTAMP,
    foreign key (user_id) references users(id) 
);

create table products (
 id int(10) primary key ,
    name varchar(10) not null,
    price int(10) default 0,
    status varchar(10) check(status='valid' or status='expired'),
    created_at datetime default CURRENT_TIMESTAMP  
);

create table order_products (
    order_id int(10) ,
    foreign key (order_id) references orders(id),
    product_id int(10),
    foreign key (product_id) references products(id),
    quantity int(10) default 0
);

# DML

insert into countries values (1,'sara','Saudi Arabia');

insert into users values (1,'sara Abduallah','a@a.com','f','1995-5-15','2022-4-17',1);

insert into orders values (1,1,'start','2022-4-17 13:47');

insert into products values (1,'sara',200,'valid','2022-4-17 13:52');

insert into order_products values (1,1,9);


update countries set continent_name='Europe' where code='1';


insert into products values (2,'saleh',100,'valid','2022-4-17 ');
delete from products where id=2;


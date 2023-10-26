```pyhton


--1) Создать таблицу employees

create table employees (
id serial primary key,
employee_name Varchar(50) not null
);

drop table employees;
select * from employees;

--2) Наполнить таблицу employee 70 строками.

INSERT INTO employees(employee_name)
values 
('Robert Lopez'),
('David Tucker'),
('Anthony Hendricks'),
('Carol Sostre'),
('Kenneth Hatfield'),
('Laura Bolt'),
('Romeo Whittle'),
('Julia Pitt'),
('Christopher Jensen'),
('Gerald Pulliam'),
('Debra Taylor'),
('Ashley Pena'),
('Henry Dellavalle'),
('Joseph Pressley'),
('Monty Alexander'),
('Jimmy Wild'),
('Lakisha Sutter'),
('Pablo Booker'),
('Luna Marti'),
('William Park'),
('William Perez'),
('Maria Jackson'),
('Elizabeth Hicks'),
('Michael Smith'),
('Troy Perry'),
('Helen Pullen'),
('Wilfred Foster'),
('Kathryn Morris'),
('Fred Cox'),
('Audrey Fobes'),
('Joy Larrivee'),
('Chester Holder'),
('Darrell Seng'),
('William Kimpton'),
('Michael Carter'),
('Wade Alexis'),
('Mark Bernard'),
('Diann Hammock'),
('Sarah Whitehouse'),
('Jodie Davis'),
('Charles Koonce'),
('Stephen Leung'),
('Jessica Reed'),
('Kip Mcqueen'),
('Irma Lucero'),
('Paula Allen'),
('Harry Green'),
('Brent Galloway'),
('Michelle Gay'),
('Charles Harris'),
('John Thomas'),
('Brian Knudsen'),
('Chris Lucero'),
('Danny Stolle'),
('Bobby Dierking'),
('Harry Chait'),
('Angela Jewell'),
('David Copeland'),
('Ernest Kruger'),
('Angelina Reynolds'),
('Alex Larsen'),
('Brian Sim'),
('Edward Mitchell'),
('David Gordon'),
('George Campbell'),
('Daphne Tatum'),
('Gerald Lalonde'),
('Lakeisha Small'),
('Diana Denney'),
('Nicole Lipka');


--3)	Создать таблицу salary
--- id. Serial  primary key,
--- monthly_salary. Int, not null


create table salary_1 (
id serial primary key,
monthly_salary int not null
);

drop table salary_1; 
select * from salary_1;
select * from salary;

--4)	Наполнить таблицу salary 15 строками:

insert into salary_1(monthly_salary)
values
    (1000),
	(1100),
	(1200),
	(1300),
	(1400),
	(1500),
	(1600),
	(1700),
	(1800),
	(1900),
	(2000),
	(2100),
	(2200),
	(2300),
	(2400),
	(2500);

--Таблица employee_salary

--5)	Создать таблицу employee_salary
--- id. Serial  primary key,
--- employee_id. Int, not null, unique
--- salary_id. Int, not null


create table employee_salary (
id serial primary key,
employee_id int not null unique,
salary_id int not null
);

select * from employee_salary;
drop table employee_salary;

--6)	Наполнить таблицу employee_salary 40 строками:
--- в 10 строк из 40 вставить несуществующие employee_id

insert into employee_salary(id, employee_id, salary_id)
values
	(1,5,14),
	(2,7,1),
	(3,9,12),
	(4,10,10),
	(5,13,3),
	(6,14,10),
	(7,16,9),
	(8,17,6),
	(9,21,9),
	(10,23,4),
	(11,26,5),
	(12,27,5),
	(13,28,9),
	(14,30,7),
	(15,31,5),
	(16,32,2),
	(17,37,12),
	(18,38,4),
	(19,40,15),
	(20,45,15),
	(21,46,1),
	(22,47,1),
	(23,51,14),
	(24,55,1),
	(25,56,6),
	(26,61,13),
	(27,66,10),
	(28,67,15),
	(29,68,2),
	(30,69,4),
	(31,96,9),
	(32,97,2),
	(33,100,6),
	(34,73,14),
	(35,74,8),
	(36,75,13),
	(37,76,2),
	(38,80,1),
	(39,85,6),
	(40,93,5);
	

--Таблица roles

--7) Создать таблицу roles
--- id. Serial  primary key,
--- role_name. int, not null, unique

create table roles_1(
id serial primary key,
role_name int not null unique
);

select * from roles_1;
drop table roles_1;
--8) Поменять тип столба role_name с int на varchar(30)

ALTER TABLE roles_1
ALTER COLUMN role_name type VARCHAR(30);


--9)	Наполнить таблицу roles 20 строками:

--id	role_name
--1	Junior Python developer
--2	Middle Python developer
--3	Senior Python developer
--4	Junior Java developer
--5	Middle Java developer
--6	Senior Java developer
--7	Junior JavaScript developer
--8	Middle JavaScript developer
--9	Senior JavaScript developer
--10	Junior Manual QA engineer
--11	Middle Manual QA engineer
--12	Senior Manual QA engineer
--13	Project Manager
--14	Designer
--15	HR
--16	CEO
--17	Sales manager
--18	Junior Automation QA engineer
--19	Middle Automation QA engineer
--20	Senior Automation QA engineer


insert into roles_1(id, role_name)
values
(1,'Junior Python developer'),
(2,'Middle Python developer'),
(3,'Senior Python developer'),
(4,'Junior Java developer'),
(5,'Middle Java developer'),
(6,'Senior Java developer'),
(7,'Junior JavaScript developer'),
(8,'Middle JavaScript developer'),
(9,'Senior JavaScript developer'),
(10,'Junior Manual QA engineer'),
(11,'Middle Manual QA engineer'),
(12,'Senior Manual QA engineer'),
(13,'Project Manager'),
(14,'Designer'),
(15,'HR'),
(16,'CEO'),
(17,'Sales manager'),
(18,'Junior Automation QA engineer'),
(19,'Middle Automation QA engineer'),
(20,'Senior Automation QA engineer');

--SELECT datname FROM pg_database;

Таблица roles_employee

--10) Создать таблицу roles_employee
--- id. Serial  primary key,
--- employee_id. Int, not null, unique (внешний ключ для таблицы employees, поле id)
--- role_id. Int, not null (внешний ключ для таблицы roles, поле id)

create table roles_employee(
 id serial primary key,
 employee_id int not null unique,
 role_id int not null,
 foreign key (role_id)
 	references roles_1(id)
);

select * from roles_employee;
drop table roles_employee;

--11) Наполнить таблицу roles_employee 40 строками:

insert into roles_employee(id,employee_id,role_id)
values
	(1,7,14),
	(2,20,1),
	(3,3,12),
	(4,5,10),
	(5,23,3),
	(6,11,10),
	(7,10,9),
	(8,22,6),
	(9,21,9),
	(10,34,4),
	(11,6,5),
	(12,27,5),
	(13,2,9),
	(14,30,7),
	(15,1,5),
	(16,15,2),
	(17,40,12),
	(18,38,4),
	(19,19,15),
	(20,45,15),
	(21,46,1),
	(22,47,19),
	(23,51,14),
	(24,55,1),
	(25,56,6),
	(26,61,13),
	(27,66,10),
	(28,67,15),
	(29,68,2),
	(30,69,4),
	(31,96,9),
	(32,97,20),
	(33,100,6),
	(34,73,14),
	(35,74,8),
	(36,75,13),
	(37,76,2),
	(38,80,18),
	(39,85,6),
	(40,93,5);






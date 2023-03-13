# completesqlbootcamp
create table employees(employee_id number primary key,employee_name varchar2(100),employee_age number,employee_email varchar2(100)) 
insert into employees values (1,'abc',22,'abc@gmail.com')
insert into employees values (2,'bcd',23,'bcd@gmail.com')
insert into employees values (3,'cgh',24,'cgh@gmail.com')
insert into employees values (4,'tyh',25,'tyh@gmail.com')
insert into employees values (5,'jkl',25,'jkl@gmail.com')
desc employees
select * from employees
create table employees1(employee_id number,employee_project_name varchar2(100),employee_experience number,employee_work_email varchar2(100)) 
desc employees1 
select * from employees1
insert into employees1 values (1,'qwe',1,'qwe@gmail.com')   
insert into employees1 values (2,'opi',2,'opi@gmail.com')   
insert into employees1 values (3,'lop',3,'lop@gmail.com')   
insert into employees1 values (4,'lay',4,'lay@gmail.com')   
insert into employees1 values (5,'ald',3,'ald@gmail.com')   
select * from employees1
select * from employees order by employee_id  asc
select employee_id Employee_idn , employee_name name from employees
select employee_id as Employee_idn , employee_name as name from employees
select employee_experience, employee_experience + 1 as employee_updated_experience from employees1
select employee_email as "employe-eemail" from employees
select employee_email as "Employee Email" from employees
select employee_email as "Employee-Email" from employees
select employee_email as "Employee- 897809Email" from employees
select employee_email as "Employee- 897809 *Email" from employees
select * from dual
select 'my name is santhosh' from dual
select 'my name is santhosh' output from dual
select q'[my name is santhosh]' "output" from dual
select q'[my name is 'santhosh']' output from dual
select q'[my name is santhosh]' "output" from dual
select q'[* hi ' kol' lop ]' as example from dual
select distinct employee_experience from employees1 -- distict works for only one column 
select  employee_experience from employees1
select unique employee_experience from employees1
select 'the name of employee is ' || employee_name from employees --concatination
select employee_id || ',' || employee_name as "Id&Name" from employees
-- arithmetic expressions +-/*
select employee_id,employee_experience,employee_experience + 1 as "Current-experience"  from employees1
select employee_id,employee_salary,(employee_experience + 100) * 12  as "Annual salaryt"  from employees1
select sysdate from dual 
select sysdate + 4 from dual --added 4 days
-- null values return null values with operators
-- using where class
select * from employees where employee_age > 22;
select * from employees where employee_age < 22;
select * from employees1 where employee_experience > 2;
select * from employees where employee_name = 'jkl'; --duplicate/redudant data is also shown 
-- comparison operators < ,>,<=,>= , <>,! , between,and,like,is null
select * from employees where employee_age is null
select * from employees where employee_age is not null
--  We can also use dates 
ALTER TABLE employees1 ADD date_of_joining date; -- adding column to the previous table
select * from employees1 where date_of_joining is null
select * from employees1 where date_of_joining is not null
update employees1 set date_of_joining = to_date('12/01/2022','dd/mm/yyyy') where employee_id =1;
update employees1 set date_of_joining = to_date('15/04/2022','dd/mm/yyyy') where employee_id =2;
update employees1 set date_of_joining = to_date('06/06/2022','dd/mm/yyyy') where employee_id =3;
update employees1 set date_of_joining = to_date('20/09/2022','dd/mm/yyyy') where employee_id =4;
update employees1 set date_of_joining = to_date('21/11/2022','dd/mm/yyyy') where employee_id =5;
select * from employees1 where date_of_joining > to_date('10/05/2022','dd/mm/yyyy') 
select * from employees1 where date_of_joining between to_date('10/01/2022','dd/mm/yyyy') and to_date('10/01/2023','dd/mm/yyyy')
select * from employees where employee_age <> 22
select * from employees where employee_age = 22
select * from employees where employee_age between 24 and 29
select * from employees where employee_age in (22,24)
select * from employees where employee_name in ('cgh','tyh')
select * from employees1 where date_of_joining in (to_date('12/01/2022','dd/mm/yyyy'))
-- sql like operator
select * from employees where employee_name like 'a%'
select * from employees where employee_name like 'c%_h%'
select * from employees where employee_name like '%d'
-- logical operators
select * from employees where employee_name ='bcd' or employee_name = 'abc'
select * from employees where employee_age = 22 and employee_name ='abc'
select * from employees where employee_age not in (22,24)
-- order by 
select * from employees order by employee_id asc
select * from employees order by employee_id desc
select * from employees order by employee_name asc
select * from employees order by employee_name desc
select * from employees order by employee_age asc
select * from employees order by employee_age desc
select * from employees1 order by employee_experience asc
select * from employees1 order by employee_experience desc
select * from employees1 order by date_of_joining asc
select * from employees1 order by date_of_joining desc
-- nulls first and last operator
select * from employees1 order by employee_work_email  nulls first
insert into employees1 (employee_id,employee_project_name,employee_experience) values (6,'alg',7)
update employees1 set date_of_joining = to_date('12/03/2023','dd/mm/yyyy') where employee_id = 6;
select * from employees1 order by employee_work_email asc nulls first
select * from employees1 order by employee_work_email  nulls last
select * from employees1 order by employee_work_email desc nulls last
-- rowid and rownum
select employee_id,employee_name from employees;
select employee_id,employee_name,rowid from employees;
select employee_id,employee_name,rownum from employees;
select employee_id,employee_name,rowid,rownum from employees;
select employee_id,employee_name,rowid,rownum from employees order by employee_id asc;
select employee_id,employee_name,employee_age,rowid,rownum from employees where employee_age > 22;
-- note : rowid is entire row id this is permanent whatever the query is
-- rownum is tempory based om the query the rownum is dependent
select employee_id,employee_project_name,employee_experience,rowid,rownum from employees1 where employee_experience >2 order by employee_experience desc;
select employee_id,employee_project_name,employee_experience,rowid,rownum from employees1 where rownum <= 4 order by employee_experience desc;
-- above query getting incorrect data
select employee_id,employee_project_name,employee_experience,rowid,rownum from 
(select employee_id,employee_project_name,employee_experience,rowid from employees1 
order by employee_experience desc) where rownum <= 4 ;
-- fetch class
select employee_name,employee_age from employees order by employee_age desc;
select employee_name,employee_age from employees order by employee_age desc offset 1 row; 
--offset skip the given rows 
select employee_name,employee_age from employees order by employee_age desc offset 1 row fetch first 2 rows only; 
select employee_name,employee_age from employees order by employee_age desc fetch last 2 rows only;
-- substitution value nothing but input values in programing language
select * from employees where employee_age = 23 ;
select * from employees where employee_age = &employee_number;
-- & used for input value for finding values
select '&column_name' from '&table_name' 
-- && used to save the value for repeated variable 
select '&column_name' from '&table_name' where employee_age between &emp_age and &emp_age + 2;
-- need to give two inputs for same variable
select '&column_name' from '&table_name' where employee_age between &&emp_age and &emp_age + 2;
-- need to give one input for same variable any times 
-- accept and prompt 
accept and prompt 'please enter valid employee id' select employee_id,employee_age from employees where employee_id = &emp_id;
-- define and undefine are used to assign and unassign values
--  set verify on and off
set verify on;
select '&column_name' from '&table_name' 
set verify off;
select '&column_name' from '&table_name' 


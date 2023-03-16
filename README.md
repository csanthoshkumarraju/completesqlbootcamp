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
-- case connversion function
select employee_name,lower(employee_name),employee_email,lower(employee_email) from employees
select employee_name,upper(employee_name),employee_email,upper(employee_email) from employees
select employee_name,initcap(employee_name),employee_email,initcap(employee_email) from employees
select * from employees where lower(employee_name) = 'bcd'
select * from employees where upper(employee_name) = 'BCD'
select * from employees where initcap(employee_name) = 'Bcd'
-- character functions
select employee_name,substr(employee_name,1,3) from employees;
-- index starts at 1
select employee_name,length(employee_name) from employees;
select concat(employee_name,employee_email) from employees;
select employee_name || length(employee_name) || employee_age || employee_email from employees;
select employee_name,instr(employee_name,'b') from employees;
select employee_name,trim('   sql course    ') from employees;
select employee_name,instr('sql course ','e') from employees;
select employee_name,trim(employee_name) from employees;
select employee_name,ltrim(employee_name) from employees;
select employee_name,ltrim('   sql course    ') from employees;
select employee_name,rtrim(employee_name) from employees;
select employee_name,rtrim('   sql course    ') from employees;
select replace('sql cource','q','Q') from dual
select replace('sql cource','q','Q') from dual
select employee_name,replace(employee_name,'b','a') from employees;
select lpad('sqlcource',10,'-') from dual
select rpad('sqlcource',10,'-') from dual
select employee_name,lpad(employee_name,2,'-') from employees;
select round(12.136,2) from dual
--  round returns ., next numbers and round value
select round(employee_age,2) from employees
select trunc(12.136,2) from dual
-- trunc returns ., next numbers and same value
select trunc(employee_age,2) from employees
select ceil(12.136) from dual
select ceil(employee_age) from employees
select floor(12.136) from dual
select floor(employee_age) from employees
select mod(12,2) from dual
select mod(employee_age,2) from employees
-- nested functions
select employee_name,length(upper(concat(employee_name,employee_email))) as "nested functions" from employees
select length(instr(substr(employee_name,1,3),'c')) as "instr length" from employees
--  dates
select sysdate from dual
select current_date from dual
select sessiontimezone from dual
select systimestamp from dual
select current_timestamp from dual
select date_of_joining,add_months(date_of_joining,3) from employees1
select date_of_joining,months_between(date_of_joining,to_date('12/03/2023','dd/mm/yyyy')) from employees1
select round(sysdate,'MONTH') from dual
select date_of_joining,round(date_of_joining,'MONTH') from employees1
select trunc(sysdate,'MONTH') from dual
select date_of_joining,trunc(date_of_joining,'MONTH') from employees1
select extract(month from date_of_joining) from employees1
select next_day(date_of_joining,'tuesday') from employees1
select last_day(date_of_joining) from employees1
-- conversion functions
select * from employees where to_char(employee_age) > '22';
select date_of_joining,to_char(date_of_joining,'DD') as day ,to_char(date_of_joining,'MM') month ,to_char(date_of_joining,'YYYY') as " year " from employees1;
select date_of_joining,to_char(date_of_joining,'dd') as day ,to_char(date_of_joining,'mm') month ,to_char(date_of_joining,'yyyy') as " year " from employees1;
select date_of_joining,to_char(date_of_joining,'Dd') as day ,to_char(date_of_joining,'Mm') month ,to_char(date_of_joining,'Yyyy') as " year " from employees1;
-- above i have used three different aliases
select date_of_joining,to_char(date_of_joining,'DAY') as DAY ,to_char(date_of_joining,'MONTH') month ,to_char(date_of_joining,'YEAR') as " year " from employees1;
select date_of_joining,to_char(date_of_joining,'day') as DAY ,to_char(date_of_joining,'month') month ,to_char(date_of_joining,'year') as " year " from employees1;
select date_of_joining,to_char(date_of_joining,'Day') as DAY ,to_char(date_of_joining,'Month') month ,to_char(date_of_joining,'Year') as " year " from employees1;
select date_of_joining,to_char(date_of_joining,'DY') as DAY ,to_char(date_of_joining,'MON') month ,to_char(date_of_joining,'YY') as " year " from employees1;
select to_number('53333.8') from dual
-- conditional expression
select employee_name,
	case employee_name
        when 'abc' then 'name is abc'
        when 'bcd' then 'name is bcd'        
        when 'tyh' then 'name is tyh'
		else 'not called' 
	end as "call"
from employees

select employee_name ,
   decode(employee_name,'abc','name is abc',
                        'bcd','name is bcd') as "called"
from employees where employee_name in ('abc','bcd') ;
-- group functions
select distinct employee_age from employees;
select distinct(employee_age) from employees;
select all(employee_age) from employees;
select count(employee_age) from employees;
select count(distinct(employee_age)) from employees;
select count(all(employee_age)) from employees;
select count(*) from employees
select avg(employee_age) from employees;
select avg(distinct(employee_age)) from employees;
select min(employee_age) from employees;
select max(employee_age) from employees;
select max(employee_name) from employees;
select length(employee_name) from employees;
select sum(employee_age) from employees;
select distinct(employee_age),all(employee_age),avg(employee_age) from employees;--error
select listagg(employee_name,',') within group (order by employee_name) "listagg / concatination " from employees where employee_id > 1;
select listagg(employee_name,'-') within group (order by employee_name) "listagg / concatination " from employees where employee_id > 1;
-- grouping data
select avg(employee_age) , avg(employee_id) from employees
-- syntax select exp_1,...exp_n  agg_function(agg_expression) from table where condition group by after //select// exp_1,...exp_n //not agg_function order by __;
select employee_id,avg(employee_age) from employees -- single group function error // need to use  same function or groupby
select employee_id,avg(employee_age) from employees group by employee_id order by employee_id asc 
select avg(employee_age) from employees group by employee_id order by employee_id asc 
select employee_id,avg(employee_age),sum(employee_age)from employees group by employee_id order by employee_id asc 
-- order of group -->from-->where-->groupby-->having-->select-->orderby--
select employee_id,avg(employee_age) from employees where avg(employee_age) >20 group by employee_id --error // having comes here
select employee_id,avg(employee_age) from employees group by employee_id having avg(employee_age) >20
select employee_id,avg(employee_age) from employees where employee_age> 20 group by employee_id having avg(employee_age) >20
select max(employee_name) , min(employee_age) from employees group by employee_id
--sql joins
select * from employees inner join employees1 on employees.employee_id = employees1.employee_id; 
select * from employees union select * from employees1;
select * from employees natural join employees1;
select * from employees join employees1 using (employee_id);
--ambiguisly defined error occurs when the table names are common in both tables
--column --for solving ambiguity we give aliases names
select employees.employee_id,employees.employee_name from employees inner join employees1 on employees.employee_id=employees1.employee_id;
select * from employees inner join employees1 using (employee_id) 
--using // avoid aliases joining multiple
select employees.employee_id,employees.employee_name from employees join employees1 on employee_id= employee1_id join employees2 on employees2_id = employees3_id
--self join
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience
from employees join employees1 on (employees.employee_id=employees1.employee_id)
--not equijoins
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees join employees1 on (employees1.employee_age > employees.employee_id)
and employees.employee_age employees1. employee_id
select employee_name from employees join employees1 using(employee_id);
select * from employees left outer join employees1 on employees.employee_id = employees1.employee_id
-- left outer join is same as left join we can use any one like alias as or space
select employees.employee_id,employees.employee_age,employees1.employee_project_name,employees1.employee_experience from employees
left outer join employees1 on employees.employee_id = employees1.employee_id
select employees.employee_id,employees.employee_age,employees1.employee_project_name,employees1.employee_experience from employees
right outer join employees1 on employees.employee_id = employees1.employee_id
select * from employees right outer join employees1 on employees.employee_id = employees1.employee_id
select employees.employee_id,employees.employee_age,employees1.employee_project_name,employees1.employee_experience from employees
full outer join employees1 on employees.employee_id = employees1.employee_id
select * from employees full outer join employees1 on employees.employee_id = employees1.employee_id
select * from employees join employees1 on employees.employee_id = employees1.employee_id 
--cross join example t1(1,2) and t2(3,4) t1 cross join t2 is (1,3;1,4;2,3;2,4)
create table colour(color_id number,colour_name varchar2(29));
create table size1(color_id number ,size_name varchar2(29));
insert into colour values(2,'blue')
insert into size1 values(4,'extra_large')
--dangerous tables get large no of columns
select  colour.color_id,colour.colour_name,size1.color_id,size1.size_name from colour cross join size1
--old method
select * from colour,size1
-- old join syntax inner join
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees ,employees1
where employees.employee_id = employees1.employee_id
-- got same result but use only  joins syntax
--we can join multiple tables with old syntax
-- old join syntax outer join
--left 
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees ,employees1
where employees.employee_id = employees1.employee_id(+)
--right
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees ,employees1
where employees.employee_id(+) = employees1.employee_id
--full join 
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees ,employees1
where employees.employee_id = employees1.employee_id(+) union 
select employees.employee_id,employees.employee_name,employees1.employee_project_name,employees1.employee_experience from employees ,employees1
where employees.employee_id(+) = employees1.employee_id
-- entity relation tables
--one to many/many to one


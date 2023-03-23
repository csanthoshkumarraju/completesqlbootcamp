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
-- subqueries/inline views
-- single subquery note :-!!! here where employee_id  (select employee_id ) employee_id is same column
select employee_name from employees where employee_id =
  (select employee_id from employees where employee_age =22)
select employee_name from employees where employee_id =
  (select employee_id from employees where employee_age > 22) --error returns multiple queries 
select employee_email from employees where employee_id =
  (select employee_id from employees where employee_age = 24)
-- multiple subqueries
select employee_id,employee_name from employees where employee_name in 
    (select employee_name from employees where employee_age in (22,23,24))
select employee_id,employee_name from employees where employee_name in 
    (select employee_name from employees where employee_age > 22)
select employee_id,employee_name from employees where employee_name,employee_age in 
    (select employee_name,employee_age from employees where employee_age in (22,23,24))
--  subqueries as a table name 
select * from (select employee_id,employee_name from employees)
select employee_name from (select employee_id,employee_name from employees)
-- scalar subquery // subquery have 1 row and 1 column
select employee_name,employee_id,employee_age from employees where employee_id =
  (select employee_id from employees where employee_age =22)
select employee_name from employees where employee_id =
  (select employee_id from employees where employee_age > 22) -- error 
--  exists
select employee_name,employee_id,employee_age from employees where exists
  (select employee_id from employees where employee_age =22)
--above vs below 
select employee_name,employee_id,employee_age from employees where employee_id =
  (select employee_id from employees where employee_age =22)
-- not  exists
select employee_name,employee_id,employee_age from employees where not exists
  (select employee_id from employees where employee_age in (22,23))
-- set operators
-- output table structure like top to bottom 
select * from employees union select * from employees1
-- union returns unique and merging table values with id 
select * from employees union all select * from employees1
-- union returns all and returns first table at top and second at bottom 
select * from employees intersect select * from employees1
-- intersect returns only common values
select * from employees minus select * from employees1
-- minus returns without common values from first table 
select employee_id,employee_name from employees union all select employee_id,employee_project_name from employees1
select employee_id,employee_name from employees union all select employee_id,employee_project_name,employee_work_email from employees1
-- ORA-01789: query block has incorrect number of result columns //solution//give/select same no.of columns in both tables 
-- using null we can solve above error
select employee_id,employee_name,null from employees union all select employee_id,employee_project_name,employee_work_email from employees1
select employee_id,employee_name,null from employees union all 
select employee_id,employee_project_name,employee_work_email from employees1 order by employee_id asc 
-- set operators with sub queries
select * from employees union (select * from employees intersect select * from employees1)
select employee_id,employee_name from employees union all 
          (select employee_id,employee_name from employees intersect select employee_id,employee_project_name from employees1) 
select * from employees intersect (select * from employees intersect select * from employees1)
select employee_id,employee_name from employees intersect 
          (select employee_id,employee_name from employees union select employee_id,employee_project_name from employees1) 
select employee_id,employee_name from employees union 
          (select employee_id,employee_name from employees minus select employee_id,employee_project_name from employees1) 
select employee_id,employee_name from employees union 
          (select employee_id,employee_name from employees minus select employee_id,employee_project_name from employees1)
           order by employee_id asc
--  create table as select / or copy from previous table
create table employees3 as select * from employees
select * from employees3
create table employees4[(employee_phone)] as select * from employees3 -- got error
select * from employees4
create table employees5 as select * from employees where employee_age > 22;
select * from employees5
alter table employees1 add project_manager varchar2(30);
alter table employees1 add (project_tl varchar2(30),project_loc varchar2(30));
desc employees1
alter table employees1 modify project_loc varchar2(100)
alter table employees1 modify (project_loc varchar2(120),project_tl varchar2(100))   
drop table employees3
desc employees3
alter table employees5 drop column employee_name
desc employees5
-- set unused /drop same workability
alter table employees5 add (project_doma varchar2(30),project_flo varchar2(30));
alter table employees5 set unused column employee_age
alter table employees5 set unused (project_tl,project_flo)
-- read only and read write
alter table employees read only
alter table employees read write
-- flashback is restoring
flashback table employees3 to before drop
select * from employees3
create table employees6 as select * from employees;
select * from employees6
delete employees6 
-- delete deletes row by row
create table employees7 as select * from employees;
truncate table employees7
-- truncate delete all at a time 
-- comments to the  columns and table   
comment on column employees.employee_id is 'this is the id of table'
comment on table employees is 'this is the employees of table'
-- rename
alter table employees rename column EMPLOYEE_NAME to employee_first_name
select * from employees
--  rename table name
rename employees to employees_data
select * from employees_data
alter table employees_data rename to employees
select * from employees
-- dml data manipulation language // insert,update,delete,merge
insert into employees1 values (1,'qwe',1,'qwe@gmail.com')   
update employees set employee_name = 'mio' where employee_id =3;
update employees set employee_name = 'miol',employee_age = 29 where employee_id =3;
create table employees3 as select * from employees
select * from employees3
delete employees3
create table employees4 as select * from employees
delete from employees4 where employee_id = 2;
insert into employees (employee_id,employee_name,employee_age,employee_email) values (6,'laq',29,'laq@gmail.com')
create table employees5(employee_id number,employee_name varchar2(100),employee_age number,employee_email varchar2(100))
insert into employees5 (employee_id ,employee_name ,employee_age ,employee_email)
select employee_id ,employee_name ,employee_age ,employee_email from employees
create table employees6(employee_id number,employee_name varchar2(100),employee_age number,employee_email varchar2(100))
insert into employees6 select * from employees
insert all 
   into employees4 values(8,'mqp',32,'mqp@gmail.com')
   into employees5 values(8,'mbp',10,'mbp@gmail.com') select * from employees;
select * from employees4
insert into employees (employee_id ,employee_name ,employee_age ,employee_email) values
  (10,'jklop',21,'jklop@gmail.com'),
  (15,'jkaql',23,'jkaql@gmail.com'),
  (25,'jkmal',34,'jkmal@gmail.com');
-- we can insert using condition
insert all 
  when employee_age > 20 then 
   into employees4 values(8,'mqp',32,'mqp@gmail.com')
   into employees5 values(8,'mbp',10,'mbp@gmail.com') select * from employees;
--  also a pivoting insert // above query
insert first 
  when employee_age > 20 then
   into employees4 values(8,'mqp',32,'mqp@gmail.com')
   into employees5 values(8,'mbp',10,'mbp@gmail.com') select * from employees;
select employee_id from employees offset 1 row 
-- tcl // commit,rollback,savepoint
delete from employees4 where employee_id = 4;
rollback 
select * from employees4 where employee_id = 4;
commit
savepoint
select * from employees where employee_age = 22 for update;
update employees set employee_name ='gfhjsg' where employee_age = 22
--for update locks the rows
--  tracking changes
select * from employees as of timestamp (sysdate - interval '3' minute) where employee_id =2;
-- constraints // primary key ,unique,not null,foreign key ,chech
create table employees6(employee_id number primary key,employee_name varchar2(100) not null,employee_age number foreign key,
    employee_email varchar2(100) unique)
-- constraints check 
create table employees2(employee_id number primary key,employee_name varchar2(100),employee_age number,employee_email varchar2(100) ,
    constraint age_check check (employee_age <30 and employee_age > 20))
insert into employees2 values (1,'abc',22,'abc@gmail.com')
insert into employees2 values (2,'bcd',23,'bcd@gmail.com')
insert into employees2 values (3,'cgh',24,'cgh@gmail.com')
insert into employees2 values (4,'tyh',25,'tyh@gmail.com')
insert into employees2 values (6,'jklu',40,'jkl@gmail.com') -- we can't insert against/without conditiom satisfaction
-- add alter constraints
alter table employees add constraint emp_name unique(employee_name)
insert into employees values (7,'jkl',25,'jkl@gmail.com') --violating if add same name 
insert into employees values (7,'jllkl',25,'jkl@gmail.com')
alter table employees add unique (employee_email);
alter table employees add check (employee_age > 20);
--  drop constraint name
alter table employees drop constraint employee_age > 20;
alter table employees drop constraint employee_age > 20 cascade constraint;
alter table employees drop constraint employee_age > 20 online;
desc employees
alter table employees drop constraint employee_age > 20 online;
-- renaming constraint
alter table employees rename constraint employee_name to employee_first
-- disable  cfonstraint
alter table employees disable constraint employee_age > 20;
alter table employees enable constraint employee_age > 20;
-- views
create view employees2 as select * from employees
select * from employees2
create view employees3 as select employee_id,employee_name from employees
select * from employees3
create view employees4 (ename,minage,maxmail) as 
   select distinct employee_name, employee_age,employee_email from employees
select * from employees4
create or replace view employees4 (ename,minage,maxmail,eid) as 
   select employee_name, employee_age,employee_email,employee_id from employees
select * from employees4
--  dml operations on views
insert into employees4 values ('anj',22,'gghss',9)
update employees4 set ename = 'cbsjbd' where eid = 2;
delete from employees4
drop table employees3
create or replace view employees5 (ename,minage,maxmail,eid) as 
   select employee_name, employee_age,employee_email,employee_id from employees
select * from employees5
drop view employees5
-- From here I am using oracle master training in udemy course codes, I have enrolled course and using (oracle master training)'s codes for learning purpose only.
--data dictionary views
select * from dictionary; 
select * from dict; 
select * from dict WHERE table_name = 'USER_CONSTRAINTS';
select * from dict WHERE lower(comments) LIKE '%CONSTRAINT%';
select * from user_objects;
select * from user_catalog;
select * from cat; 
select * from all_objects;
select * from dba_objects;
select * from user_tables; 
select * from tabs;
select * from all_tables;
select * from dba_tables;
select  * from user_tab_columns; 
select * from user_tab_columns where table_name = 'employees'; 
select * from all_tab_columns where table_name = 'employees1';
select * from user_constraints;
select * from all_constraints;
select * from dba_constraints;
select * from user_cons_columns;
select * from user_cons_columns where table_name = 'employees';
select * from user_tab_comments; 
select * from user_tab_comments where lower(comments) like '%employee_name%';
select * from user_tab_comments where lower(comments) like '%employee_age%';
select * from employees1;
select * from user_col_comments where lower(comments) like '%mail%';
-- oracle sequences
-- creating 
create sequence employee_seq start with 1 increment by 7 maxvalue 100 cache 40 nocycle;
create sequence employee_seq1 start with 10 increment by 2 maxvalue 999 cache 30 nocycle;
-- modifying
create sequence employee_seq2 start with 5 increment by 4 maxvalue 999 cache 10 nocycle;
alter sequence employee_seq2 start with 5 increment by 4 maxvalue 999 cache 10 nocycle;
-- getting error
alter sequence employee_seq2 increment by 5 maxvalue 999 cache 10 nocycle;
alter sequence employee_seq1 increment by 4 nocycle;
-- using sequences
drop sequence employee_seq;
create sequence employee_seq start with 10 increment by 4 maxvalue 7848 cache 78 nocycle;  
select employee_seq.currval from dual;
select employee_seq.nextval from dual; 
insert into employees (employee_id, employee_name,employee_email,employee_age)
            values (employee_seq.nextval, 'abjas','abjas@gmail.com',32);
select * from employees; 
select employee_seq.nextval from employees;
-- default values
create table example (employee_id integer default employee_seq.nextval, employee_name  varchar2(50));
insert into example(employee_name) values ('steve');
select * from example;
drop table example; 
create table example (employee_id integer default employee_seq.currval, employee_name varchar2(50));
select employee_seq.nextval from dual;
insert into example(employee_id,employee_name) values(null,'steve');
-- identity
create table iden (id number generated as identity, 
                   text varchar2(100));
drop table iden;                   
create table iden (id number generated always as identity, 
                   text varchar2(100));                   
drop table iden;
create table iden (id number generated by default as identity, 
                   text varchar2(100));
drop table iden;
create table iden (id number generated by default on null as identity, 
                   text varchar2(100)); 
drop table iden;
create table iden (id number generated by default on null as identity start with 30 increment by 2, 
                   i_text varchar2(100)); 
insert into iden (id, i_text) values (2,'vsdhjgvhiusdgf');
insert into iden (id, i_text) values (3,'dgYIUGF');
insert into iden (id, i_text) values (null,'ghsdgfhfih');
insert into iden (i_text) values ('fgshjgf');
select * from iden;
select * from user_objects where object_name = 'iseq$$_74510';
select * from user_sequences where sequence_name = 'iseq$$_74510';
select iseq$$_74510.nextval from dual; 
drop table iden;
purge recyclebin;
-- oracle synonyms
create synonym example_syno for employees;
select * from example_syno;
create or replace synonym example_syno for employees1;
drop synonym example_syno;
create synonym example_syno for sys.user_objects;
select * from user.example_syno;
create or replace public synonym example_syno for user.employees;
create or replace public synonym example_syno for system.redo_db;
create synonym employees1 for employees;
create public synonym employees1 for hr.employees;
create synonym employees for employees1;
create synonym employees2 for employees122;
select * from employees2;
drop synonym example_syno;
drop synonym employees2;
drop public synonym example_syno;
drop public synonym employees;
describe user_synonyms; 
select * from user_synonyms;
create synonym employs for employees;
select * from dba_synonyms;
drop synonym employs;
-- sql indexes
create table employees4 as select * from employees; 
create unique index emp_idx on employees4 (employee_id);
select * from employees4 where employee_id = 1;
select * from employees4 where employee_name = 'abc'; 
create unique index emp_cpy_lname_idx on employees4 (employee_name);
create index emp_cpy_lname_idx on employees4 (employee_name);
create index emp_cpy_name_idx  on employees4 (employee_name);
select * from employees4 where employee_name = 'abc'; 
create bitmap index emp_cpy_comm_idx on employees4 (employee_age);
select * from employees4 where employee_age = 22;
create table orders (order_id number primary key,order_date date not null,user_id number not null,trans_id number unique,order_details varchar2(4000));                    
select * from orders where order_id = 20 and trans_id = 30;
drop table orders;
create table orders (order_id number primary key using index (create index orders_order_id_idx on orders(order_id)),
                    order_date date not null,user_id number not null,
                    trans_id number unique using index (create index sale_tran_id_idx on orders(trans_id)),
                    order_details varchar2(100));
drop table orders;
create table orders (order_id number primary key using index (create unique index orders_order_id_idx on orders(order_id)),
                    order_date date not null,
                    user_id number not null,
                    trans_id number unique using index (create bitmap index sale_tran_id_idx on orders(trans_id)),
                    order_details varchar2(4000));
drop table orders;
create table orders (order_id number primary key using index (create unique index orders_order_id_idx on orders(order_id)),
                    order_date date not null,
                    user_id number not null,
                    trans_id number using index (create bitmap index sale_tran_id_idx on orders(trans_id)),
                    order_details varchar2(4000)); 
drop table orders;
create table orders (order_id number primary key using index (create unique index orders_order_id_idx on orders(order_id)),
                    order_date date not null,
                    user_id number not null,
                    trans_id number using index (create unique index sale_tran_id_idx on orders(trans_id)),
                    order_details varchar2(4000)); 
drop table orders;
create table orders (order_id number primary key using index (create unique index orders_order_id_idx on orders(order_id)),
                    order_date date not null,
                    user_id number not null,
                    trans_id number unique using index (create unique index sale_tran_id_idx on orders(trans_id)),
                    order_details varchar2(4000)); 
create table orders2 (order_id number primary key using index orders_order_id_idx,
                    order_date date not null,
                    user_id number not null,
                    trans_id number unique,
                    order_details varchar2(100)); 
drop table orders;
create table orders (order_id number,
                    order_date date not null,
                    user_id number not null,
                    trans_id number,
                    order_details varchar2(100));
alter table orders add primary key (order_id) using index (create unique index orders_order_id_idx on orders(order_id)); 
create unique index sale_tran_id_idx on orders(trans_id);
alter table orders add unique (trans_id) using index sale_tran_id_idx;
drop index index_name;
-- function based indexes
create table employees11 as select * from employees;
create index emp_cpy_lname_idx on employees11 (employee_name); 
select * from employees11 where employee_name = 'abc';
select * from employees11 where lower(employee_name) = 'abc';
drop index emp_cpy_lname_idx;
create index emp_cpy_fname_idx on employees11 (upper(employee_name)); 
select * from employees11 where lower(employee_name) = 'abc';
select * from employees11 where employee_name ='abc';
-- multiple indexes
create table employees12 as select * from employees;
create index emp_cpy_dpt_id_idx on employees12 (employee_id);
create index emp_cpy_dpt_id_idx2 on employees12 (employee_id) invisible;
create bitmap index emp_cpy_dpt_id_idx2 on employees12 (employee_id);
create bitmap index emp_cpy_dpt_id_idx2 on employees12 (employee_id) invisible;
select * from employees12 where employee_id = 2;
select from employees12 where employee_id = 2;
drop index emp_cpy_dpt_id_idx2;
alter index emp_cpy_dpt_id_idx invisible;
create unique index emp_cpy_empid_idx on employees12 (employee_id) invisible;
select * from employees12 where employee_id = 1;
select from employees12 where employee_id = 1; 
alter session set optimizer_use_invisible_indexes = true;
-- modify index
create table employees13 as select * from employees;
alter table employees13 add primary key (employee_id);
select * from user_indexes where table_name = 'employees13';
alter index sys_c008587 rename to emp_idx;
select * from employees13 where employee_id = 1;
alter index emp_idx unusable;
select index_name, status from user_indexes where table_name = 'employees13';
alter index emp_idx compile;
alter index emp_idx rebuild;
alter index emp_idx disable;
create index emp_cpy_name_idx on employees13(upper(),first_name);
select index_name, index_type, status, funcidx_status from user_indexes where table_name = 'employees13';
select * from employees13 where upper(last_name) = 'steven';
alter index emp_cpy_name_idx disable;
alter index emp_cpy_name_idx enable;
alter index emp_cpy_name_idx invisible;
select index_name, index_type, status, funcidx_status, visibility from user_indexes where table_name = 'employees13';
alter index emp_cpy_name_idx visible;
--privileges 
create user priv identified by 1;
drop user priv;
create user priv identified by 1
password expire account unlock container=all;
create user priv identified by 2
password expire account unlock container=current;
drop user priv cascade;
select * from dba_users;
grant create session to priv;
select * from all_users;
select * from user_users;
--alter
alter user priv identified by abc1;
select * from user_sys_privs;
select * from dba_sys_privs;
create table temp_table(temp_column number);
select * from session_privs;
-- -------------
select * from system_privilege_map;
grant create table, create view to priv with admin option container = all;
grant create table, create view to priv with admin option container = current;
create role support;
grant create session, create sequence, create table to support;
select * from dba_sys_privs where grantee = 'support';
select * from dba_sys_privs where grantee = 'priv';
grant support to priv;
create sequence temp_seq;
select * from user_role_privs;
select * from 	session_privs;
create synonym temp_synonym for temp_table;
grant create session, create sequence, create table, create synonym to support;
grant create synonym to support;
create role test_role identified by 1;
grant test_role to priv;
grant select any table to test_role;
set role test_role identified by 1;
set role all;
set role test_role identified by 1, support;
set role none;
set role all except test_role;
select * from user.employees;
drop role test_role;
select * from employees14;
grant select, delete on employees14 to user, support;
grant update (salary,commission_pct) on employees14 to user;
grant update on employees14 to support;
grant insert on employees14 to public; 
grant all on employees14 to user;
grant unlimited tablespace to user;
alter table employees15 add primary key (employee_id);
grant all on employees15 to user;
revoke all on employees15 from user;
grant select on system.redo_db to user;




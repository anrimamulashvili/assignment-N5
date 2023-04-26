
SELECT---------------------------------------------------------------


select * from hr.departments;

Select * From hr.jobs;

select * from hr.employees;

SELECT * FROM HR.DEPARTMENTS;

select department_name from hr.departments;

select department_name, location_id 
  from hr.departments;

select department_name
      ,location_id
      ,department_id
  from hr.departments;

select last_name, salary from hr.employees;

select last_name, salary, salary + 300 from hr.employees;

select last_name, salary, commission_pct, salary - salary * commission_pct 
  from hr.employees;

select last_name, salary, salary * 12 from hr.employees;

select last_name, salary, 12 * salary + 100 from hr.employees;

select last_name, salary, 12 * (salary + 100) from hr.employees;

select first_name, last_name from hr.employees;

select first_name || last_name as "Employee" from hr.employees;

select first_name || ' ' || last_name as "Employee" from hr.employees;

select last_name || ' is a ' || job_id as "Employee Details" from hr.employees;

select department_name || q'[ Department's Manager Id:]' || manager_id as "Department and Manager"
  from hr.departments;

select department_name || q'< Department's Manager's Id:>' || manager_id as "Department and Manager"
  from hr.departments;

select department_id from hr.employees;

select distinct department_id from hr.employees;

select last_name, commission_pct from hr.employees;

select last_name as name, commission_pct comm from hr.employees;

select last_name as "Name", commission_pct "Comm", salary * 12 "Annual Salary" 
  from hr.employees;

select last_name as "Name", commission_pct "Comm" from hr.employees;

desc hr.employees;
describe hr.departments;







WHERE----------------------------------------------------------



select employee_id, last_name, job_id, department_id
  from hr.employees
 where department_id = 90;

select last_name, job_id, department_id
  from hr.employees
 where last_name = 'Whalen';

select last_name
  from hr.employees
 where hire_date = '16-FEB-05';

select last_name, salary
  from hr.employees
 where salary <= 3000;

select last_name, salary
  from hr.employees
 where salary between 2500 and 3500;

select employee_id, last_name, salary, manager_id
  from hr.employees
 where manager_id in (100, 101, 201);

select first_name
  from hr.employees
 where first_name like 'S%';

select last_name 
  from hr.employees
 where last_name like '_o%';

select employee_id, last_name, job_id
  from hr.employees
 where job_id like '%SA\_%' ESCAPE '\';

select last_name, manager_id
  from hr.employees
 where manager_id is null;

select employee_id, last_name, job_id, salary
  from hr.employees
 where salary >= 10000
   and job_id like '%MAN%';

select employee_id, last_name, job_id, salary
  from hr.employees
 where salary >= 10000
    or job_id like '%MAN%';

select last_name, job_id
  from hr.employees
 where job_id not in ('IT_PROG', 'ST_CLERK', 'SA_REP');

select last_name, job_id
  from hr.employees
 where salary not between 10000 and 15000;

select last_name, job_id
  from hr.employees
 where last_name not like '%A%';

select last_name, job_id
  from hr.employees
 where commission_pct is not null;

select last_name, job_id, salary
  from hr.employees
 where job_id = 'SA_REP'
    or job_id = 'AD_PRES'
   and salary > 15000;

select last_name, job_id, salary
  from hr.employees
 where (job_id = 'SA_REP'
    or job_id = 'AD_PRES')
   and salary > 15000;

select last_name, job_id, department_id, hire_date
  from hr.employees
 order by hire_date;

select * 
  from hr.employees
 where salary > 10000
 order by manager_id;

select * 
  from hr.employees
 where salary > 10000
 order by manager_id desc;

select * 
  from hr.employees
 where salary > 10000
 order by manager_id
 nulls first;

select * 
  from hr.employees
 where salary > 10000
 order by manager_id desc
 nulls last;

select last_name, job_id, department_id, hire_date
  from hr.employees
 order by hire_date desc;

select employee_id, last_name, salary * 12 annsal
  from hr.employees
 order by salary * 12;
 
select employee_id, last_name, salary * 12 annsal
  from hr.employees
 order by annsal; 

select last_name, job_id, department_id, hire_date
  from hr.employees
 order by 3;

select last_name, department_id, salary
  from hr.employees
 order by department_id, salary desc;

select employee_id, last_name, salary, department_id
  from employees
 where employee_id = &employee_num;

select last_name, department_id, salary * 12last_name, salary, department_id
  from employees
 where job_id = '&job_title';

select employee_id, last_name, job_id, &column_nam
  from employees
 where &condition
 order by &order_column;

select employee_id, last_name, job_id, &&column_name
  from employees
 order by &column_name;

define employee_num = 200

select employee_id, last_name, salary, department_id
  from employees
 where employee_id = &employee_num;

undefine employee_num

set verify on

select employee_id, last_name, salary
  from employees
 where employee_id = &employee_num;






FUNCTIONS----------------------------------------------





select 'The job id for ' || upper(last_name) || ' is ' || lower(job_id) as "employee details"
  from hr.employees;

select employee_id, last_name, department_id
  from hr.employees
 where last_name = 'higgins';

select employee_id, last_name, department_id
  from hr.employees
 where lower(last_name) = 'higgins';

select concat(1,999) from dual;
select concat(1,'777') from dual;
select concat(sysdate,'777') from dual;

select substr('Hello World',-5,5) from dual;

select length(' ') from dual;
select length('') from dual;
select length(1.234) from dual;

select instr('Hello World','o',1) from dual;
select instr('Hello World','o',1,2) from dual;
select instr('Hello World','o',1,3) from dual;
select substr('Hello World',7) from dual;
select instr('Hello World','W',1,1) from dual;

select substr('Hello World',instr('Hello World','W',1,1)) from dual;
select trim(trailing 1 from 1231) from dual;

select employee_id, concat(first_name, last_name) name, job_id, length(last_name),
       instr(last_name, 'a') "Contains 'a'?"
  from hr.employees
 where substr(job_id, 4) = 'REP';

select employee_id, concat(first_name, last_name) name, length(last_name),
       instr(last_name, 'a') "Contains 'a'?"
  from hr.employees
 where substr(last_name, -1, 1) = 'n';

select round(45.923, 2), round(45.923, 0), round(45.923, -1)
  from dual;
  
select trunc(45.923, 2), trunc(45.923), trunc(45.923, -1)
  from dual;

select last_name, salary, mod(salary, 5000)
  from hr.employees
 where job_id = 'SA_REP';

select last_name, (sysdate-hire_date)/7 as weeks
  from hr.employees
 where department_id = 90;

select employee_id, hire_date, months_between (sysdate, hire_date) tenure, 
       add_months(hire_date, 6) review, next_day (hire_date, 'FRIDAY'), last_day (hire_date)
  from hr.employees 
 where months_between (sysdate, hire_date) < 150000;

select employee_id, hire_date,
       round(hire_date, 'MONTH'), trunc(hire_date, 'MONTH')
  from hr.employees
 where hire_date like '%08';

select employee_id, hire_date,
       round(hire_date, 'YEAR'), trunc(hire_date, 'YEAR')
  from hr.employees; 





gacharaqtereba------------------------------




SELECT TO_CHAR(TO_DATE('27-OCT-98', 'DD-MON-RR'), 'YYYY') "Year" FROM DUAL;
SELECT TO_CHAR(TO_DATE('27-OCT-17', 'DD-MON-RR'), 'YYYY') "Year" FROM DUAL; 

SELECT TO_CHAR(TO_DATE('27-OCT-98', 'DD-MON-YY'), 'YYYY') "Year" FROM DUAL;
SELECT TO_CHAR(TO_DATE('27-OCT-17', 'DD-MON-YY'), 'YYYY') "Year" FROM DUAL;

select last_name, (sysdate-hire_date)/7 as weeks
  from hr.employees
 where department_id = 90;

select employee_id, hire_date, months_between (sysdate, hire_date) tenure, 
       add_months(hire_date, 6) review, next_day (hire_date, 'FRIDAY'), last_day (hire_date)
  from hr.employees 
 where months_between (sysdate, hire_date) < 150000;

select employee_id, hire_date,
       round(hire_date, 'MONTH'), trunc(hire_date, 'MONTH')
  from hr.employees
 where hire_date like '%08';

select employee_id, hire_date,
       round(hire_date, 'YEAR'), trunc(hire_date, 'YEAR')
  from hr.employees; 
  
select employee_id, hire_date, to_char(hire_date, 'MM/YY') Month_hired
  from hr.employees;
  
select last_name,
       hire_date,
       to_char(hire_date, 'fmDD Month YYYY') as hiredate
  from hr.employees;
  
select last_name,
       hire_date,
       to_char(hire_date, 'fmDdspth "of" Month YYYY HH:MI:SS AM') as hiredate
  from hr.employees; 

select to_char(next_day(add_months (hire_date, 6), 'FRIDAY'), 'fmDay, Month ddth, YYYY') "Next 6 Month Review"
  from hr.employees
order by hire_date;

select to_char(salary, '$99,999.00') salary
  from hr.employees
 where last_name = 'Ernst';

select last_name, hire_date
  from hr.employees
 where hire_date = to_date('June  17, 2003', 'fxMonth DD, YYYY');

select last_name, upper(concat(substr(last_name, 1, 8), '_US'))
  from hr.employees
 where department_id = 60;

select to_char(next_day(add_months (hire_date, 6), 'FRIDAY'), 'fmDay, Month ddth, YYYY') "Next 6 Month Review"
  from hr.employees
 order by hire_date;

select to_char(round((salary/7), 2), '99G999D99', 'NLS_NUMERIC_CHARACTERS = '',.''') "Formatted Salary"
  from hr.employees;

select last_name, salary, nvl(commission_pct, 0), (salary * 12) + (salary *12 * nvl(commission_pct, 0)) AN_SAL
  from hr.employees;

select last_name, salary, nvl(commission_pct, 0),
	(salary * 12) + (salary * 12 * nvl(commission_pct, 0)) an_sal
  from hr.employees;

select last_name, salary, nvl(commission_pct, 0),
	nvl2(commission_pct, salary * 12 * (1 + commission_pct), (salary * 12)) an_sal
  from hr.employees; 

select last_name, salary, commission_pct,
	nvl2(commission_pct, 'SAL+COMM', 'SAL') income
  from hr.employees where department_id in (50, 80);

select first_name, length(first_name) "expr1",
	   last_name, length(last_name) "expr2",
	   nullif(length(first_name), length(last_name)) result
  from hr.employees;

SELECT  NULLIF(NULL,100)
  FROM dual;

SELECT NULLIF(10,'20')
  FROM dual;

SELECT NULLIF(TO_CHAR(10),'20') -- 10
  FROM dual;

select last_name, employee_id,
       coalesce(to_char(commission_pct), to_char(manager_id), 'No commission and no manager')
  from hr.employees;

select last_name, salary, commission_pct,
  coalesce((salary + (commission_pct * salary)), salary + 2000, salary) "New Salary"
  from hr.employees;

select last_name, job_id, salary,
	   case job_id when 'IT_PROG' then 1.10 * salary
                   when 'ST_CLERK' then 1.15 * salary
                   when 'SA_REP' then 1.20 * salary
            else salary 
       end "Revised Salary"
  from hr.employees;

select last_name, job_id, salary,
	   case when job_id = 'IT_PROG' then 1.10 * salary
            when job_id = 'ST_CLERK' then 1.15 * salary
            when job_id = 'SA_REP' then 1.20 * salary
            else salary 
       end "Revised Salary"
  from hr.employees;

select last_name, salary,
 (case when salary < 5000 then 'Low'
       when salary < 10000 then 'Medium'
       when salary < 20000 then 'Good'
       else 'Excellent'
  end) qualified_salary
from hr.employees;

select last_name, job_id, salary,
       decode(job_id, 'IT_PROG', 1.10 * salary,
                      'ST_CLERK', 1.15 * salary,
                      'SA_REP', 1.20 * salary,
              salary) Revised_salary
  from hr.employees;






GROUP FUNCTIONs



select avg(salary), max(salary), min(salary), sum(salary)
from hr.employees
where job_id like '%REP%';

select min(hire_date), max(hire_date)
from hr.employees;

select min(last_name), max(last_name)
from hr.employees;

select count(*)
from hr.employees
where department_id = 50;

select count(commission_pct)
from hr.employees
where department_id = 80;

select count(distinct department_id)
from hr.employees;

select avg(commission_pct)
from hr.employees;

select avg(nvl(commission_pct,0))
from hr.employees;

select department_id, avg(salary)
from hr.employees
group by department_id;

select avg(salary)
from hr.employees
group by department_id;

select department_id, avg(salary)
from hr.employees
group by department_id
order by avg(salary);

select department_id, job_id, sum(salary)
from hr.employees
group by department_id, job_id
order by job_id;

select department_id, job_id, sum(salary)
from hr.employees
where department_id > 40
group by department_id, job_id
order by department_id;

select department_id, count(last_name)
from hr.employees;

select department_id, job_id, count(last_name)
from hr.employees
group by department_id;

select department_id, avg(salary)
from hr.employees
where avg(salary) > 8000
group by department_id;

select department_id, avg(salary)
from hr.employees
group by department_id
having avg(salary) > 8000;

select department_id, avg(salary)
from hr.employees
group by department_id
having department_id = 10;

select department_id, avg(salary)
from hr.employees
group by department_id
having employee_id = 100;

select department_id, max(salary)
from hr.employees
group by department_id
having max(salary) > 10000;

select job_id, sum(salary) payroll
from hr.employees
where job_id not like '%REP%'
group by job_id
having sum(salary) > 13000
order by sum(salary);

select job_id, sum(salary), max(salary) payroll
from hr.employees
where job_id not like '%REP%'
group by job_id
having max(salary) > 10000
order by sum(salary);

select job_id, sum(salary) payroll
from hr.employees
where job_id not like '%REP%'
group by job_id
having max(salary) > 10000;

select max(avg(salary))
from hr.employees
group by department_id;







JOINS


select department_id, department_name, location_id, city
from hr.departments
natural join hr.locations;

select employee_id, last_name, location_id, department_id
from hr.employees join hr.departments
using (department_id);

select l.city, d.department_name
from hr.locations l join hr.departments d
using (location_id)
where d.location_id = 1400;

select e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id
from hr.employees e join hr.departments d
on (e.department_id = d.department_id);

select e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id
from hr.employees e, hr.departments d
where e.department_id = d.department_id;

select employee_id, city, department_name
from hr.employees e
join hr.departments d
on d.department_id = e.department_id
join hr.locations l
on d.location_id = l.location_id;

select e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id
from hr.employees e join hr.departments d
on (e.department_id = d.department_id)
and e.manager_id = 149;

select e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id
from hr.employees e join hr.departments d
on (e.department_id = d.department_id)
where e.manager_id = 149;

select worker.last_name emp, manager.last_name mgr
from hr.employees worker join hr.employees manager
on (worker.manager_id = manager.employee_id);

select e.last_name, e.department_id, d.department_name
from hr.employees e left outer join hr.departments d
on (e.department_id = d.department_id);

select e.last_name, e.department_id, d.department_name
from hr.employees e right outer join hr.departments d
on (e.department_id = d.department_id);

select e.last_name, e.department_id, d.department_name
from hr.employees e full outer join hr.departments d
on (e.department_id = d.department_id);

select last_name, department_name
from hr.employees
cross join hr.departments;

select * from hr.employees, hr.jobs;
select * from hr.employees e , hr.jobs j where e.job_id = j.job_id;

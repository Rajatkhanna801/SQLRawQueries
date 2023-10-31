# Create employee table
CREATE TABLE employee
(
    emp_id int primary key,
    emp_name varchar(50),
    dept_name varchar(50),
    salary int
);

INSERT into employee
VALUES (120, 'Monika', 'admin', 5000),
(121, 'Rosalin', 'IT', 6000),
(122, 'Ibrahim', 'IT', 8000),
(123, 'Vikram', 'IT', 10000),
(124, 'Dheeraj', 'IT', 11000)


# Write a query to get employees earning salary more than average salary
SELECT * 
from employee 
where salary > (select avg(salary) from employee);


# Sub queries
==> It is SQL query inside a another SQL query. SQL will excute the inner query first and then hold the value and then excute the outer query.

# Types of subqueries
1. Scalar subquery
==> It always have one row and one column
# Syntax
# Write a query to get employees earning salary more than average salary
==> SELECT * from employee 
    where salary > (select avg(salary) from employee);

2. Multiple row subquery
==> It return multiple rows and multiple columns
# Syntax
1. Write a SQL command to get employee earning highest salary in each department 
==> SELECT * from employee
    WHERE (dept_name, salary) in (
        SELECT dept_name, max(salary) from employee group by dept_name
    );
2. Write a SQL query to fetch all deprtments that have no employees in that.
==> SELECT * from department
    WHERE dept_name not in (SELECT DISTINCT dept_name from employee);

3. Correlated Subquery
==> The subquery which is related to outer query.
# Syntax
# Write a query to get companies those sales is more than avearge sales
==> SELECT * 
    FROM (SELECT store_name, sum(price) as total_sales
        from sales group by store_name) sales
    JOIN (Select avg(total_sales) as sales
        from sales group by store_name) avg_sales
    ON sales.total_sales > avg_sales.sales;


# SQL Commands that subqueries
1. SELECT
2. INSERT
3. UPDATE
4. DELETE





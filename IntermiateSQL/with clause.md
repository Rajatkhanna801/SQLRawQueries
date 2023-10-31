# With clause
==> Common Table expression (CTE) also known as Sub query Factoring.

# Examples
1. Write a with clause SQL query to fetch employees whose salary is above average salary

==> With average_salary(avg_salary) as 
	(SELECT cast(avg(salary) as int) from employee)
SELECT * from employee as e, average_salary as av 
WHERE e.salary > av.avg_salary;

2. Find stores who's sales where better than average sales across all stores.

CREATE Table sales
(
    store_id int,
    store_name varchar(50),
    product varchar(50),
    quantity int,
    cost int
);


Insert into sales
VALUES (1, 'Apple Originals 1', 'iphone 12 pro', 1, 1000),
(1, 'Apple Originals 1', 'MacBook pro 13', 3, 2000)
(1, 'Apple Originals 1', 'Airpods Pro', 2, 280)
(2, 'Apple Originals 2', 'iphone 12 pro', 2, 1000)
(3, 'Apple Originals 3', 'iphone 12 pro', 1, 1000)
(3, 'Apple Originals 3', 'MacBook pro 13', 1, 2000)
(3, 'Apple Originals 3', 'MacBook Air', 4, 1100)
(3, 'Apple Originals 3', 'iphone 12', 2, 1000)
(3, 'Apple Originals 3', 'Airpods pro', 3, 280)
(4, 'Apple Originals 4', 'iphone 12 pro', 2, 1000)
(4, 'Apple Originals 4', 'MacBook pro 13', 1, 2500);

(i) get sales per stores
==> select store_id, sum(cost) as total_sales_per_store
    from sales group by store_id;

(ii) get average sales of all stores
==> SELECT avg(total_sales_per_store) as avg_sales
    from (SELECT s.store_id, sum(s.cost) as total_sales_per_store
	    from sales as s 
	    group by s.store_id) as x;

(iii) get stores list that is having sales more than avarage sales
==> WITH total_sales as (
        select store_id, sum(cost) as total_sales_per_store
		from sales group by store_id
    ),
	avg_sales as (
        SELECT avg(total_sales_per_store) as                avg_sales_for_all_stores from total_sales
    )

SELECT * from total_sales 
JOIN avg_sales 
ON total_sales.total_sales_per_store > avg_sales.avg_sales_for_all_stores;

==> SELECT * 
    from (select store_id, sum(cost) as total_sales_per_store
		from sales group by store_id) as total_sales
    JOIN (SELECT avg(total_sales_per_store) as avg_sales_for_all_stores
		from (SELECT s.store_id, sum(s.cost) as total_sales_per_store
			from sales as s 
			group by s.store_id) as x) as avg_sales
    ON total_sales.total_sales_per_store > avg_sales.avg_sales_for_all_stores;
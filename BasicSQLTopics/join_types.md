# Table: Customer
+-------------+--------------+
| customer_id | customer_name|
+-------------+--------------+
| 1           | Alice        |
| 2           | Bob          |
| 3           | Charlie      |
| 4           | David        |
+-------------+--------------+

# Table: orders
+---------+-------------+
| order_id| customer_id |
+---------+-------------+
| 101     | 1           |
| 102     | 1           |
| 103     | 2           |
| 104     | 4           |
+---------+-------------+


# Types of joins 
1. Inner join ==> The INNER JOIN returns records that have matching values in both tables.

==> SELECT customers.customer_name, orders.order_id
FROM customers
INNER JOIN orders ON customers.customer_id = orders.customer_id;


# Results
+--------------+---------+
| customer_name| order_id|
+--------------+---------+
| Alice        | 101     |
| Alice        | 102     |
| Bob          | 103     |
| David        | 104     |
+--------------+---------+


2. LEFT JOIN (or LEFT OUTER JOIN):
==> The LEFT JOIN returns all records from the left table and the matched records from the right table. The result will contain NULL in the right side when there is no match.

==> SELECT customers.name, orders.order_id
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id;

# Results
+--------------+---------+
| customer_name| order_id|
+--------------+---------+
| Alice        | 101     |
| Alice        | 102     |
| Bob          | 103     |
| Charlie      | NULL    |
| David        | 104     |
+--------------+---------+


3. RIGHT JOIN (or RIGHT OUTER JOIN):
==> The RIGHT JOIN returns all records from the right table and the matched records from the left table. The result will contain NULL in the left side when there is no match.

# Syntax
==> SELECT customers.name, orders.order_id
FROM customers
RIGHT JOIN orders ON customers.customer_id = orders.customer_id;

# Results
+--------------+---------+
| customer_name| order_id|
+--------------+---------+
| Alice        | 101     |
| Alice        | 102     |
| Bob          | 103     |
| NULL         | 104     |
+--------------+---------+


4. FULL JOIN (or FULL OUTER JOIN):
==> The FULL JOIN returns all the rows when there is a match in one of the tables. It combines the results of both LEFT JOIN and RIGHT JOIN.

# Syntax
==> SELECT customers.name, orders.order_id
FROM customers
FULL JOIN orders ON customers.customer_id = orders.customer_id;

# Results


5. CROSS JOIN
==> The CROSS JOIN returns the Cartesian product of both tables, meaning it combines each row from the first table with every row from the second table.

# Systax
==> SELECT customers.name, products.product_name
FROM customers
CROSS JOIN products;

6. Self join
==> A SELF JOIN is used to join a table with itself. This is useful for comparing rows within the same table.

# syntax
==> SELECT e1.customer_name AS customer, e2.customer_name AS referred_by
FROM customers e1
INNER JOIN customers e2 ON e1.referral_id = e2.customer_id;

# Results
+--------------+--------------+
| customer     | referred_by  |
+--------------+--------------+
| Alice        | Bob          |
| Alice        | Bob          |
| Bob          | Charlie      |
+--------------+--------------+

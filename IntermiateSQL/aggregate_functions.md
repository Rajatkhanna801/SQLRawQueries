# Aggregate functions
==> Aggregate functions in SQL are functions that perform a calculation on a set of values and return a single value. These functions are often used in conjunction with the GROUP BY clause to perform calculations on groups of rows rather than individual rows

# Type of Aggregate functions
1. count()
==> SELECT count(population) from city;
2. sum()
==> Select sum(population) from city;
3. Min()
==> Select min(population) from city;
4. Max()
==> Select max(population) from city;
5. Avg()
==> Select avg(population) from city;
6. GROUP_CONCAT()
==> It concatenates values from multiple rows into a single string, grouping them by a specified column. Here's an example:
==> SELECT order_id, GROUP_CONCAT(product_name ORDER BY quantity DESC SEPARATOR ', ') AS concatenated_products
FROM orders GROUP BY order_id;

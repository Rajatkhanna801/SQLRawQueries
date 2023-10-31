# SQL views
==> It is database object. It is created over SQL query.It does not store any data. It is just representation of tables. It stores structure of query.

# Advantages
1. Security ==> By hiding the query used to generate the view.
2. Simplify complex SQL queries.

# Uses
# Rules 
(i) Data updation is only done if we have view have only one table/view.
1. Update table data using views
==> Create or replace view expensive_products
    as 
    SELECT * from tb_product_info where price > 1000;

==> update expensive_products
    SET prod_name = 'Airpods Pro', brand = 'Apple',
    WHERE prod_id = 'P10';

(ii) Cammot have distinct clause
(iii) Group by clause
(iv) WITH clause
(v) window function
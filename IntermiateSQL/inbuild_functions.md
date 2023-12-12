# Inbuild functons Types
1. Aggregate functions
==> Min, Max, Sum, Avg, Count, GROUP_CONCAT
2. String functions
==> Contact()
==> Length()
==> Upper()
==> Lower()
==> Trim()
==> SUBSTRING() or SUBSTR()
3. Date and Time function
==> Current_date
==> current_time
==> current_timestamp
==> DATEPART() or EXTRACT()
# datepart function for MySQL
==> SELECT OrderDate,
        DATEPART(YEAR, OrderDate) AS OrderYear,
        DATEPART(MONTH, OrderDate) AS OrderMonth,
        DATEPART(DAY, OrderDate) AS OrderDay
    FROM Orders;
# EXTRACT for PostGreSQL
==> SELECT
        order_date,
        EXTRACT(YEAR FROM order_date) AS order_year,
        EXTRACT(MONTH FROM order_date) AS order_month,
        EXTRACT(DAY FROM order_date) AS order_day
    FROM orders;
==> DATEDIFF()
4. Mathematical Functions:
==> ABS()
==> Round()
==> Ceil or ceiling() 
Ceil functon will provide the minimum interger
==> Floor()
Floor functon will provide the max interger
==> Power()
5. Conditional Functions
==> CASE WHEN
==> COALESCE()
COALESCE is handle to add the string and if cloumn value is null it skip that.
==> NULLIF(integer, 0)
NULLIF is used to compare two integers and if condition matchs it returns null. 
6. Conversion Functions
==> Cast
==> Convert
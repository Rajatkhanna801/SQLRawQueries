# Group By
==> It is used to club data based on specific groups like we have payment model that having different transaction based on payment mode. So, write a SQL query to get mode and total transaction per mode from payment model.

# Syntax
==> SELECT mode, sum(amount) as total
    FROM paymenet Group by mode ORDER By total DESC;


# Having CLause
==> It is apply a filter based on the result of group by based on specific condition. We can't apply filter in where condition with Group by statement.

Having clause is only used by GROUP By statement on other hand WHERE is used in SELECT statement.

# Syntax
SELECT mode, count(amount) as total
From Payment Group by mode
Having count(amount) >= 3
ORDER BY total DESC; 
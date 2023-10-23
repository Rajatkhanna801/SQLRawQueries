# SQL operators
1. Comparison operators (=, <>, !=, >=, >, <, <=)
2. Arthmetic operator (+, -, *, /, %)
3. Logical opearotors (AND, OR, NOT, IN, BETWEEN, Like, etc.)

# Operator and select examples
(i) SELECT * from Students;
(ii) SELECT ID, FIRST_NAME, LAST_NAME from Students;
(iii) SELECT * from Students WHERE subject_name = 'Mathematics';
(iv) SELECT * from Students WHERE subject_name <> (!=) 'Mathematic';
(v) SELECT * from employee WHERE SALARY >= 10000 order_by salary desc;
(vi) SELECT * from employee WHERE SALARY BETWEEN 5000 AND 1000 order by salary;
(vii) SELECT * from Subjects WHERE subject_name NOT in ('Mathematics', 'English', 'Punjabi');
(viii) SELECT * from Subjects WHERE subject_name LIKE 'S%';
(ix) SELECT * from Staff WHERE age > 50 AND GENDER = 'F';
(x) SELECT (5+2) as Total;
(xi) SELECT DISTINCT employee_type from Employee;
(xii) SELECT * from Employee limit 5;

# Case statement
SELECT STAFF_ID, SALARY,
CASE WHEN SALARY >= 10000 THEN 'High Salary'
    WHEN SALARY BETWEEN 5000 AND 10000 THEN 'Average_Salary'
    WHEN SALARY <= 5000 THEN 'Too Low'
END AS RANGE
FROM STAFF_SALARY ORDER BY 2 DESC;
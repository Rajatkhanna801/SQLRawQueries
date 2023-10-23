# Types of SQL commands
1. DDL ==> Data defination language
==> create, drop, alter, Truncate
2. DML ==> Data Manipulation language
==> Insert, update, delete, merge
3. Data control language
==> GRANT, REVOKE
4. TCL ==> Transaction control language
==> Commit, rollback, savepoint
5. DQL ==> Data Query Language
==> SELECT


###### Data defination language
==> used to define struture of database such as tables, views, functions, etc. create, modify, delete any database objects.
# Query to create student table
(i) CREATE ==> command to create a table in database

==> CREATE TABLE STUDENTS
(
    ID VARCHAR(20) PRIMARY KEY,
    FIRST_NAME VARCHAR(100) NOT NULL,
    LAST_NAME VARCHAR(100) NOT NULL,
    GENDER VARCHAR(10) CHECK (GENDER IN ('M','F','MALE','FEMALE')),
    AGE INT,
    DOB DATE,
    GRADE FLOAT,
    IS_ACTIVE BOLLEAN,
    CONSTRAINT CH_STUDENTS_AGE_CHECK(AGE > 0)
);

(ii) DROP ==> command to delete the given table.
==> DROP TABLE STUDENTS;
==> DROP USER user_name;
==> DROP ROLE role_name;

(iii) ALTER ==> Command used to rename column name, table name, add or delete new column, change the data type of column.
==> ALTER TABLE old_table_name RENAME new_table_name;
==> ALTER TABLE table_name CHANGE old_column_name new_col_name Data Type and a foreign key;
==> ALTER TABLE table_name ADD column_name data_type;
==> ALTER TABLE table_name DROP COLUMN column_name;
==> ALTER TABLE your_table ALTER COLUMN date_column VARCHAR(50);
==> ALTER TABLE table_name
ADD FOREIGN KEY (column_name) REFERENCES referenced_table(ref_column_name);
==> ALTER TABLE table_name
DROP FOREIGN KEY foreign_key_name;
==> ALTER TABLE table_name
ENGINE = new_engine;

(iii) Trunacte ==> Remove all data in given table without dropping the table schema.
==> TRUNCATE TABLE table_name;


###### Data Manipulation Language
==> Command used to modify, delete the database data

(i) Insert ==> load data into tables
==> INSERT INTO table_name (column_name1, column_name2)
    VALUES ('value1', 'value2');
==> INSERT into table_name 
    VALUES ('value1', 'value2');

(ii) Delete ==> Delete the specific entry from the table
==> DELETE FROM table_name;
==> DELETE FROM table_name where column1 == 'value';

(iii) Update ==> Update the specific entry in the database entry.
==> Update table_name 
    SET country = 'India' 
    where student_id = 1;

(iv) Merge ==> It uses insert and update in single command.
    If the condition matchs it will update the record. Otherwise it will insert new entry.
==> MERGE INTO customers AS T
    USING customer_updates AS S
    ON T.cust_id = S.cust_id
    WHEN MATCHED THEN
        UPDATE SET T.name = S.name, T.age = S.age
    WHEN NOT MATCHED THEN
        INSERT (cust_id, name, age)
        VALUES (S.cust_id, S.name, S.age);

##### DQL (data query language)
(i) SELECT 
==> Used to retreive data from one or more tables


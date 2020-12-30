# Advance-Database-Final-Exam/Project

# Database Source
A database trigger is a procedure that is automatically executed in response to certain events on a database table. A common use of database trigger is for auditing database. A trigger that records the insertion, modification and deletion of important data will let you know when and why certain change has been made to the database. MySQL supports triggers that are invoked in response to the INSERT, UPDATE or DELETE event. The SQL standard defines two types of triggers: row-level triggers and statement-level triggers.

![abb](https://user-images.githubusercontent.com/73207169/103334282-9771e000-4a25-11eb-99c4-7ed5d3fcf9d0.png)

Database source is from the Introduction to the ER Data Model. Here’s the link: 

https://flaviocopes.com/entity-relationship/ 

Books Table – Each entity can have one or more attributes like in this books table it has an id, author id, and name, solved by, and published by. These are the ones on the table where when we have something to change; it’s automatically recorded on the books table.

Author’s Table – contains the id, name, awards and date. Here we will get to insert, update and delete if we want to change the table.

Logs Table – in this table it contains the id, author id, action and cdate/created date when we can change it. We need to know when the person borrowed the books.
 
# Database Dependency Diagram

![abc](https://user-images.githubusercontent.com/73207169/103334467-3dbde580-4a26-11eb-8bd1-3141ba8ba6e7.png)

We can see in our Database Dependency Diagram it shown that the attributes in our books table are actually connected at the end of the published by and the authors connect at the end of the date and last is the logs table connect at the end of the cdate or created date which table it belongs to.

# Query 1

     INSERT INTO `category` (`categoryID`, `name`) VALUES
     (1, 'Skirt'),
     (2, 'Dress'),
     (3, 'Pants'),
     (4, 'Jackets'),
     (5, 'Accessories');

- Allows a database administrator to write code that is flexible and adaptable.

IMPORTANCE

It is a dynamic query, and it is used to update its criteria each time you click into the query. It is usually less swift and efficient but in return it is very flexible.

OUTPUT:

![skt](https://user-images.githubusercontent.com/73207169/103334527-86759e80-4a26-11eb-8335-a29e3cf95209.png)

# Query 2 

    INSERT INTO logs VALUES (null, OLD.id, 'Inserted', NOW ())

- It allows the insertion of multiple rows of literal values.

IMPORTANCE

It’s important to use INSERT statement to add data that you specifically define, or you can add data that you retrieve from other tables or views.

OUTPUT:

![image](https://user-images.githubusercontent.com/73207169/103334557-ac02a800-4a26-11eb-8da2-37ae7e9e6984.png)

# Query 3

    INSERT INTO logs VALUES (null, OLD.id, 'Updated', NOW ())

- Update trigger means that MYSQL will fire this trigger after the UPDATE operation is executed.

IMPORTANCE

This trigger is invoked after an updation occurs. (i.e., it gets implemented after an update statement is executed.).

OUTPUT:

![img](https://user-images.githubusercontent.com/73207169/103334623-ef5d1680-4a26-11eb-971a-3b226f195b1f.png)

# Query 4 

    SELECT customerName, city, state, postalCode, country
    FROM customers
    ORDER BY customerName;
    
- The following SELECT statement returns all rows in the table customers.

IMPORTANCE

Stored procedure help to reduce network traffic, centralize business logic in the database and make database more secure.

OUTPUT:

![cst](https://user-images.githubusercontent.com/73207169/103334662-11569900-4a27-11eb-842b-34e61b7bffa2.png)

# Query 5

    START TRANSACTION;
    SELECT temp_id, temp_temperature 
    FROM apartment_temps;
    UPDATE apartment_temps as tc
    SET tc.temp_temperature = (tc.temp_temperature / 3.24);
    SELECT temp_id, temp_temperature
    FROM apartment_temps;
    ROLLBACK;
    
- This ensures that the database properly changes states upon a successfully committed transaction.

IMPORTANCE

The query sees the changes made by transactions that committed before that point of time, and no changes made by later or uncommitted transactions.

OUTPUT:

![transac](https://user-images.githubusercontent.com/73207169/103334716-4e229000-4a27-11eb-9fef-a8d3190e6ab9.png)

# Query 6

    SELECT BALANCE FROM ACCOUNT WHERE ID = 1 
    BALANCE > 100 
    UPDATE ACCOUNT SET BALANCE = BALANCE – 100 WHERE ID = 1

- All queries must succeed. If one fails all should rollback.

IMPORTANCE

Atom cannot be divided and cannot be split.

OUTPUT:

![blnce](https://user-images.githubusercontent.com/73207169/103334806-a22d7480-4a27-11eb-9579-b60ec9e2ab2c.png)

# Query 7 

    INSERT INTO contacts (first_name, last _name, email)
    VALUES (‘john’, ‘doe’, ‘john.doe@mysqltutorial.org’);

- It is a way of storing data without actually sending it through the INSERT or UPDATE clauses in SQL.

IMPORTANCE

They can be indexed but they don’t allow subqueries in it.

OUTPUT:

![insrt](https://user-images.githubusercontent.com/73207169/103334847-cee18c00-4a27-11eb-9f20-b3b78899e2b6.png)

# Query 8

    SELECT  
    employee_id, first_name, last_name
    FROM 
    employees 
    WHERE 
    EXISTS( SELECT 1 
    FROM dependents
    WHERE 
    dependents.employee_id = employees.employee_id);

- The EXISTS operator allows you to specify a subquery to test for the existence of rows.

IMPORTANCE

The EXISTS operator terminates the query processing immediately once it finds a row, therefore, you can leverage this feature of the EXISTS operator to improve the query performance.

OUTPUT:

![exst](https://user-images.githubusercontent.com/73207169/103334880-f0db0e80-4a27-11eb-85f4-e52c3a7bc0ef.png)

# Query 9

    SELECT
	      department_id,
	      department_name
    FROM
	      departments
    WHERE
	      department_id IN (1, 2, 3);
        
- The INNER JOIN clause can join three or more tables as long as they have relationships, typically foreign key relationships.

IMPORTANCE

The most important and frequently used of the joins is the INNER JOIN. They are also referred to as an EQUIJOIN.

OUTPUT:

![innr](https://user-images.githubusercontent.com/73207169/103334904-0cdeb000-4a28-11eb-9112-ed76a9ad626d.png)

# Query 10

    SELECT * 
    FROM author 
    WHERE country='USA'
    
- Are virtual tables that do not store any data of their own but display data stored in other tables.

IMPORTANCE

To simplifies data access, can be used to perform a calculation and display its result, we can select of rows by means of an appropriate WHERE clause or selected only a subset of a table’s column and we can select data from multiple tables by using join or union.

OUTPUT:

![whr](https://user-images.githubusercontent.com/73207169/103334930-30095f80-4a28-11eb-805e-7e41e5775f1e.png)

# Query 11

    DELETE FROM new
    WHERE cate_id='2';
    
- The following statement will remove those records from the 'new' table which satisfies the condition 'cate_id' = '2'.

IMPORTANCE

To delete a record(s) from a table, the user must have the DELETE privilege on that particular table.

OUTPUT:

![dlt](https://user-images.githubusercontent.com/73207169/103334965-58915980-4a28-11eb-9025-c9363e1c346b.png)

# Query 12

    SELECT subjects, s_name, mark, dense_rank() 
    OVER ( partition by subjects order by mark desc ) 
    AS 'dense_rank' FROM result;

- This function will assign rank to each row within a partition without gaps.

IMPORTANCE

Here, table is partitioned on the basis of “subjects”.
order by clause is used to arrange rows of each partition in descending order by “mark”.

OUTPUT:

![dense_rank](https://user-images.githubusercontent.com/73207169/103335068-b02fc500-4a28-11eb-9142-6045e792ede8.png)

# Query 13

    SELECT subjects, s_name, mark, rank() 
    OVER ( partition by subjects order by mark desc ) 
    AS 'rank' FROM result;

- This function will assign rank to each row within a partition with gaps.

IMPORTANCE

When you want to display a rank for numeric values in a list.

OUTPUT:

![rank](https://user-images.githubusercontent.com/73207169/103335120-da818280-4a28-11eb-96d5-ba365214babb.png)

# Query 14

    SELECT subjects, s_name, mark, percent_rank() 
    OVER ( partition by subjects order by mark ) 
    AS 'percent_rank' FROM result;

- It tells the percentage of partition values less than the value in the current row, excluding the highest value.

IMPORTANCE

Here, the percent_rank () function calculate percentile rank in ascending order by “mark” column.

OUTPUT:

![percent_rank](https://user-images.githubusercontent.com/73207169/103335160-000e8c00-4a29-11eb-95f2-c9c233a5059a.png)

# Query 15

    SELECT
	    first_name,
	    last_name
    FROM
	    employees
    UNION
    SELECT
	    first_name,
	    last_name
    FROM
	    dependents
    ORDER BY
	    last_name;

- The UNION operator combines result sets of two or more SELECT statements into a single result set.

IMPORTANCE

The following statement uses the UNION operator to combine the first name and last name of employees and dependents.

OUTPUT:

![union](https://user-images.githubusercontent.com/73207169/103335183-216f7800-4a29-11eb-8499-1e5c49cfd882.png)

# Query 16

    SELECT DISTINCT Country FROM Customers;

- The following SQL statement selects only the DISTINCT values from the "Country" column in the "Customers" table.

IMPORTANCE

The SELECT DISTINCT statement is used to return only distinct (different) values.

OUTPUT:

![dstnc](https://user-images.githubusercontent.com/73207169/103335229-4237cd80-4a29-11eb-94cb-3cb66af8a382.png)

# Query 17

    SELECT * FROM Orders WHERE OrderDate='2008-11-11'

- The most difficult part when working with dates is to be sure that the format of the date you are trying to insert, matches the format of the date column in the database.

IMPORTANCE

As long as your data contains only the date portion, your queries will work as expected. However, if a time portion is involved, it gets more complicated.

OUTPUT:

![ordrdate](https://user-images.githubusercontent.com/73207169/103335296-698e9a80-4a29-11eb-9e12-175a8777e46c.png)

# Query 18

    SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE SALARY > 2000 AND age < 25;

- These operators provide a means to make multiple comparisons with different operators in the same SQL statement.

IMPORTANCE

The AND operator allows the existence of multiple conditions in an SQL statement's WHERE clause.

OUTPUT:

![and](https://user-images.githubusercontent.com/73207169/103335355-84f9a580-4a29-11eb-978d-2fea77581e40.png)

# Query 19

    SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE SALARY > 2000 OR age < 25;

- The following code block has a query, which would fetch the ID, Name and Salary fields from the CUSTOMERS table, where the salary is greater than 2000 OR the age is less than 25 years.

IMPORTANCE

The OR operator is used to combine multiple conditions in an SQL statement's WHERE clause.

OUTPUT:

![or](https://user-images.githubusercontent.com/73207169/103335387-a3f83780-4a29-11eb-9e77-2cada93df680.png)

# Query 20

    SELECT ID, NAME, AGE, ADDRESS, SALARY
    FROM CUSTOMERS
    GROUP BY age
    HAVING COUNT (age) >= 2

- The HAVING Clause enables you to specify conditions that filter which group results appear in the results.

IMPORTANCE

Which would display a record for a similar age count that would be more than or equal to 2.

OUTPUT:

![havng](https://user-images.githubusercontent.com/73207169/103335438-c5592380-4a29-11eb-9269-70de45249efd.png)





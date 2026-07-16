Difficulty: Easy
Topic: SQL, LEFT JOIN, Anti Join, NOT EXISTS

Problem Understanding

We have two tables:

Customers

Contains all customers.

Column	Description
id	Unique customer ID
name	Customer name
Orders

Contains customers who placed orders.

Column	Description
id	Order ID
customerId	Customer ID who placed the order

Goal:
Find all customers who have never placed any order.

Approach 1: LEFT JOIN (Recommended)
Query:
SELECT c.name AS Customers
FROM Customers c
LEFT JOIN Orders o
ON c.id = o.customerId
WHERE o.customerId IS NULL;
Explanation:
LEFT JOIN returns all rows from the Customers table.
If a customer has an order, matching order details will appear.
If a customer has no order, the Orders columns will contain NULL.
We filter those NULL values to get customers who never ordered.
Example:

Customers:

id	name
1	Joe
2	Henry
3	Sam
4	Max

Orders:

id	customerId
1	3
2	1

After LEFT JOIN:

name	customerId
Joe	1
Henry	NULL
Sam	3
Max	NULL

Rows with NULL customerId are customers who never ordered.

Approach 2: NOT IN
SELECT name AS Customers
FROM Customers
WHERE id NOT IN (
    SELECT customerId
    FROM Orders
);
Explanation:
First, find all customer IDs present in Orders.
Remove those IDs from Customers.
Remaining customers are those who never ordered.
Approach 3: NOT EXISTS
SELECT c.name AS Customers
FROM Customers c
WHERE NOT EXISTS (
    SELECT 1
    FROM Orders o
    WHERE c.id = o.customerId
);
Explanation:
Checks each customer.
If no matching order exists, that customer is selected.
SELECT 1 is used because we only need to check existence, not retrieve data.
Key Concept: Anti Join

This problem is an example of an Anti Join.

Definition:

An Anti Join returns rows from one table that do not have a matching row in another table.

General Pattern:
SELECT A.column
FROM TableA A
LEFT JOIN TableB B
ON A.id = B.id
WHERE B.id IS NULL;
Used When:
Finding customers without orders
Finding employees without departments
Finding products without sales
Finding users without activity
Important Learning Points

✅ LEFT JOIN keeps all rows from the left table.
✅ NULL after a LEFT JOIN means no matching record exists.
✅ LEFT JOIN + IS NULL is the most common way to solve "find missing records" problems.
✅ NOT EXISTS is usually safer than NOT IN when NULL values are possible.

Time Complexity:

LEFT JOIN → Depends on database indexing, generally O(N + M)

Where:

N = number of Customers
M = number of Orders
Pattern to Remember:

Find records in Table A that don't exist in Table B:

SELECT A.*
FROM A
LEFT JOIN B
ON A.id = B.id
WHERE B.id IS NULL;

Problem Category: SQL Joins → Anti Join → Missing Records Detection
577. Employee Bonus
Topic
LEFT JOIN
NULL Handling
WHERE Clause
Key Concept

Use LEFT JOIN when you need all records from the left table, even if there is no matching record in the right table.

In this problem:

Employee is the left table.
Bonus is the right table.
Employees without a bonus should also be included in the result.
Important Points
1. LEFT JOIN
Employee
LEFT JOIN Bonus
ON Employee.empId = Bonus.empId

Returns all employees. If an employee has no bonus, the bonus value becomes NULL.

2. NULL Comparison

NULL cannot be compared using =.

 Incorrect

bonus = NULL (#)

 Correct

bonus IS NULL
3. Logical Operator

The problem requires employees who satisfy either of the following conditions:

Bonus is less than 1000
No bonus exists

Therefore, use OR.

bonus < 1000 OR bonus IS NULL
Solution
SELECT e.name, b.bonus
FROM Employee e
LEFT JOIN Bonus b
ON e.empId = b.empId
WHERE b.bonus < 1000
   OR b.bonus IS NULL;
Common Mistakes
Using RIGHT JOIN instead of LEFT JOIN.
Using = NULL instead of IS NULL.
Using AND instead of OR.
Pattern Learned

Whenever a problem asks for:

All records from one table, including those without a matching record in another table → use LEFT JOIN.
Missing values → use IS NULL.
Complexity
Time Complexity: O(n + m) (depends on indexing and join implementation)
Space Complexity: O(1) (excluding the output)
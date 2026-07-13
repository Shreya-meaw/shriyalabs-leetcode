## Topic Name = LEFT JOIN

# Definition:
LEFT JOIN returns all rows from the left table and the matching rows from the right table. If no match exists, the right table's columns are returned as NULL.

# When to Use:

Return all table data even if they haven't been assigned a any column data.
Show all table data,  even if they haven't placed an order.
Include rows even when matching data doesn't exist.
Trick to Remember

LEFT = Left table data never lose 

or

"LEFT table is always safe." 

# Syntax
SELECT table1.col_name1,table2.col_name2
FROM table1,table2
LEFT JOIN table2
ON table1.id = table2.id;
Breakdown
FROM: Starting (driving) table.

LEFT JOIN: Connects the second table.

ON: Condition batata hai records kaise match honge.

# Why LEFT JOIN?

see in Question keywords .

if this keywords are there:

Return all from table1
Show all from table1
Even if no matching record exists
Return NULL if not found

so Use LEFT JOIN.

# Common Mistakes
1. Using INNER JOIN

Wrong if question says:

Return all table1 values.

2. Wrong ON condition
ON t1.colid1 = t2.colId2 (not correct))

Correct:

ON t1.colid1 = t2.colId1 (correct)

3. Writing column.table

Wrong: Col_name.table1

Correct: table1.col_name

# Complexity
Time Complexity: O(n) — Scan the Person table and match rows using personId.
Space Complexity: O(n) — Required to store the resulting output.

# Interview Tip

difference in INNER JOIN and LEFT JOIN?
common key identify?
able to Choose JOIN according to question keywords 

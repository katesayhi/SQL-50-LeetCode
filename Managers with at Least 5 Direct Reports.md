#### Problem
```
Table: Employee

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table indicates the name of an employee, their department, and the id of their manager.
If managerId is null, then the employee does not have a manager.
No employee will be the manager of themself.
```
Write a solution to find managers with at least five direct reports.

Return the result table in any order.

#### Intuition
Find `id` have at least five `id` reporting the same `managerID`.

#### Approach
- Using `SELECT`
- Using `WHERE` condition to find the `id` that is the `managerID` other `id`s report to
  
#### Code
```
select name
from employee
where id IN (select managerID
            from employee
            group by managerID
            having count(*) >= 5
)
```

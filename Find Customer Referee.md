#### Problem
Table: Customer
```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
```
Find the names of the customer that are **not referred** by the customer with `id = 2`

#### Intuition
- referee_id can be numberic or null.
- Using `WHERE`

#### Approach 
Using simple Select with Where clause.

#### Code
```
/* Write your T-SQL query statement below */
SELECT name
FROM Customer AS c
WHERE c.referee_id != '2' OR c.referee_id is NULL
```



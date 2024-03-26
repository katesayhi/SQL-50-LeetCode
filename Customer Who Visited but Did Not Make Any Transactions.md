#### Problem
```
Table: Visits

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| visit_id    | int     |
| customer_id | int     |
+-------------+---------+
visit_id is the column with unique values for this table.
This table contains information about the customers who visited the mall.
```
```
Table: Transactions

+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| transaction_id | int     |
| visit_id       | int     |
| amount         | int     |
+----------------+---------+
transaction_id is column with unique values for this table.
This table contains information about the transactions made during the visit_id.
```
Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.

Return the result table sorted in any order.

#### Intuition
Join 2 tables by `visit_id`, then find the user visited the mall but did not make any transactions.

#### Approach
- Using `Left Join` to connect 2 tables: `Visits`, `Transactions`
- Using `Where` to find `transaction_id` of customer is `NULL` (meaning they did not make transactions)
- Using `Group by` to group `customer_id`
- Using `Count()` to count the number of times they visited the mall without making any transaction
- Using `Select` to get `customer_id` and `Count(*)` as `count_no_trans`
  
#### Code
```
SELECT customer_id, COUNT(*) as count_no_trans
FROM Visits as V LEFT JOIN Transactions as T
ON V.visit_id = T.visit_id
WHERE T.transaction_id IS NULL
GROUP BY customer_id
```

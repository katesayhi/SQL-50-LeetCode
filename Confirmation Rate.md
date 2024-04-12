#### Problem
```
Table: Signups

+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| user_id        | int      |
| time_stamp     | datetime |
+----------------+----------+
user_id is the column of unique values for this table.
Each row contains information about the signup time for the user with ID user_id.
```
```
Table: Confirmations

+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| user_id        | int      |
| time_stamp     | datetime |
| action         | ENUM     |
+----------------+----------+
(user_id, time_stamp) is the primary key (combination of columns with unique values) for this table.
user_id is a foreign key (reference column) to the Signups table.
action is an ENUM (category) of the type ('confirmed', 'timeout')
Each row of this table indicates that the user with ID user_id requested a confirmation message at time_stamp and that confirmation message was either confirmed ('confirmed') or expired without confirming ('timeout').
```
The **confirmation rate** of a user is the number of `'confirmed'` messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. 
Round the confirmation rate to **two decimal** places.

Write a solution to find the confirmation rate of each user.

#### Intuition
Join two tables then find the confirmation rate of each user.

#### Approach
- Using `LEFT JOIN` to join two tables
- Using `CASE` expression
- Using `AVG()` to calculate the confirmation rate
- Using `ROUND()` to round the results
  
#### Code
```
select S.user_id, 
round(AVG(case when action='confirmed' then 1.0 else 0.0 end),2) as confirmation_rate
from Signups as S LEFT JOIN Confirmations as C
on S.user_id = C.user_id
group by S.user_id
```

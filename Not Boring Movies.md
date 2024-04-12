#### Problem
```
Table: Cinema

+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| id             | int      |
| movie          | varchar  |
| description    | varchar  |
| rating         | float    |
+----------------+----------+
id is the primary key (column with unique values) for this table.
Each row contains information about the name of a movie, its genre, and its rating.
rating is a 2 decimal places float in the range [0, 10]
```
Write a solution to report the movies with an odd-numbered ID and a description that is **not** `"boring"`.

Return the result table ordered by `rating` in **descending order**.

#### Intuition
Find not boring movies with odd-numbered IDs.

#### Approach
- Using `WHERE` to filter odd-numbered IDs and not boring description.
- Using  `ORDER` to print the result table ordered by `rating` in descending order.
  
#### Code
```
select id, movie, description, rating
from Cinema
where (id%2)<>0 and description not like 'boring'
order by rating desc
```

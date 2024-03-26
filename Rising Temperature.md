#### Problem
```
Table: Weather

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.
```
Write a solution to find all dates' `Id` with higher temperatures compared to its previous dates (yesterday).

Return the result table in any order.

#### Intuition
Create a child table of `Weather` which include weather of previous dates, then join `Weather` and compare the temperature.

#### Approach
- Using `DATEADD(interval, number, date)` where `interval` is `day`, `number`= -1, `date` is `recordDate`
- Using `INNER JOIN` to create a table that include infor of date and previous date in a row
- Using `WHERE` to compare temperature
- 
#### Code
```
SELECT Weather.id
FROM Weather INNER JOIN Weather AS w 
ON w.RecordDate = DATEADD (day, -1, Weather.RecordDate) 
WHERE  Weather.Temperature > w.Temperature
```

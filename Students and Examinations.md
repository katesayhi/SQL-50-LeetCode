#### Problem
```
Table: Students

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| student_id    | int     |
| student_name  | varchar |
+---------------+---------+
student_id is the primary key (column with unique values) for this table.
Each row of this table contains the ID and the name of one student in the school.
```
```
Table: Subjects

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| subject_name | varchar |
+--------------+---------+
subject_name is the primary key (column with unique values) for this table.
Each row of this table contains the name of one subject in the school.
```
```
Table: Examinations

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | int     |
| subject_name | varchar |
+--------------+---------+
There is no primary key (column with unique values) for this table. It may contain duplicates.
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.
```
Write a solution to find the number of times each student attended each exam.

Return the result table ordered by `student_id` and `subject_name`.

#### Intuition
Create a big table including 3 above tables' info, group rows based on `student_id`,`student_name`, `subject_name` then count the `subject_name` each student has.

#### Approach
- Using `CROSS JOIN`, `LEFT JOIN` to join 3 tables
- Using `GROUP BY` to group rows by `student_name`, `student_id`, `subject_name`
- Using `ORDER BY` to return table ordered by `student_id` and `subject_name`
  
#### Code
```
select S.student_id, S.student_name, Su.subject_name, count(E.subject_name) as attended_exams
from Students as S 
CROSS JOIN Subjects as Su
LEFT JOIN Examinations as E
on S.student_id = E.student_id
and E.subject_name = Su.subject_name
group by S.student_name,  S.student_id, Su.subject_name
order by S.student_id, Su.subject_name
```

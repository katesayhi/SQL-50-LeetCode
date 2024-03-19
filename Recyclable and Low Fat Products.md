### Intuition
I need to find the ID of products that are both low fat and recylable using Where, AND.

### Approach
Using Select, Where, And.
### Code
````
/* Write your T-SQL query statement below */
SELECT product_id 
FROM Products AS p
WHERE p.low_fats = 'Y' AND p.recyclable = 'Y'
````
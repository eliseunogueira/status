# Define failure
## What / Where / When / How to solve it

*SQL command ALL*
    [Where](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/submissions/)
    07/10/2022 07:50PM
## Write your MySQL query statement below
### Solution:
``` sql
select customer_number from Orders group by customer_number having count(customer_number) >= all(Select count(customer_number) from orders group by customer_number)
```

Example 1:

Input: 
Orders table:

|order_number | customer_number|
|----|---|
| 1  | 1 |
| 2  | 2 |
| 3  | 3 |
| 4  | 3 |

Output: 

| customer_number |
|-----------------|
| 3 |

Explanation: 
The customer with number 3 has two orders, which is greater than either customer 1 or 2 because each of them only has one order. 
So the result is customer_number 3.
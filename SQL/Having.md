# Having
**Q1:The following SQL statement lists the number of customers in each country, sorted high to low (Only include countries with more than 5 customers):**

```
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC;
```


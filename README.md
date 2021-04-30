<p>
<img src="images/Shopify.jpg" width="900" height="500">
</p>

# Fall 2021 Data Science Intern Challenge 

**Applicant**: Ning Chen \
[LinkedIn](https://www.linkedin.com/in/ningchen345/) \
[Blog](https://kinder-chen.medium.com)


## Question 1
Given some sample data, write a program to answer the following: [click here to access the required data set](https://docs.google.com/spreadsheets/d/16i38oonuX1y1g7C_UAmiK9GkY7cS-64DfiDMNiR41LM/edit#gid=0).

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $\$3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

- a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

**There are duplicates in the data. After calculating the unit price, I find there are also significant large item price which seems wrong.**

- b. What metric would you report for this dataset?

**Instead of AOV (average order value), we can use weighted AOV in which total # of items is considered.**

- c. What is its value?

**WAOV (weighted average order value) = 293.72**

```diff
Please find detailed code in [Jupyter Notebook](https://github.com/ghcn345/Shopify-Technical-Challenge/blob/master/TechnicalChallenge.ipynb).
```

## Question 2
For this question you’ll need to use SQL. [Follow this link](https://www.w3schools.com/SQL/TRYSQL.ASP?FILENAME=TRYSQL_SELECT_ALL) to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

- a. How many orders were shipped by Speedy Express in total?

Queries: 
```sql
SELECT SUM(od.Quantity) FROM OrderDetails od 
JOIN ORDERS o USING(OrderID) 
WHERE o.ShipperID = 1 
```
Result: 3575

- b. What is the last name of the employee with the most orders?

Queries: 
```sql
SELECT e.Lastname, SUM(od.Quantity) as total FROM OrderDetails od 
JOIN ORDERS o USING(OrderID) 
JOIN Employees e USING(EmployeeID) 
GROUP BY EmployeeID 
ORDER BY total DESC 
LIMIT 1
```
Result: Peacock

- c. What product was ordered the most by customers in Germany?

Queries: 
```sql
SELECT c.CategoryName, COUNT(c.CategoryName) as total FROM Categories c 
JOIN Products p USING(CategoryID) 
JOIN OrderDetails od USING(ProductID) 
JOIN Orders o USING(OrderID) 
JOIN Customers cu USING(CustomerID) 
WHERE cu.Country = 'Germany' 
GROUP BY CategoryID 
ORDER BY total DESC 
LIMIT 1
```
Result: 17

## For More Information

Please review question analysis in [Jupyter Notebook](https://github.com/ghcn345/Shopify-Technical-Challenge/blob/master/TechnicalChallenge.ipynb). \
For any additional questions, please contact **Ning Chen—chen.ning345@gmail.com**.

## Repository Structure

Description of the structure of the repository and its contents:
```
├── README.md                           <- Solution of Fall 2021 Data Science Intern Challenge
├── TechnicalChallenge                  <- Technical Challenge Code in Jupyter notebook
├── data                                <- 2019 Winter Data Science Intern Challenge Data Set
└── images                              <- logo
```
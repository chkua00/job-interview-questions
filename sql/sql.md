# SQL


### 1. Students
Given the following data definition, write a query that returns the number of students whose first name is John.

``` sql
TABLE students
   id INTEGER PRIMARY KEY,
   firstName VARCHAR(30) NOT NULL,
   lastName VARCHAR(30) NOT NULL
```

**Solution:**
``` sql
SELECT COUNT(*) FROM students WHERE firstName = 'John';
```



***
### 2. Enrollment
A table containing the students enrolled in a yearly course has incorrect data in records with ids between 20 and 100 (inclusive).
``` sql
TABLE enrollments
  id INTEGER NOT NULL PRIMARY KEY
  year INTEGER NOT NULL
  studentId INTEGER NOT NULL
```
Write a query that updates the field 'year' of every faulty record to 2015.

**Solution:**
``` sql
UPDATE enrollments SET year = 2015 WHERE id BETWEEN 20 AND 100;
```


***
### 3. Pets
Information about pets is kept in two separate tables:
``` sql
TABLE dogs
  id INTEGER NOT NULL PRIMARY KEY,
  name VARCHAR(50) NOT NULL

TABLE cats
  id INTEGER NOT NULL PRIMARY KEY,
  name VARCHAR(50) NOT NULL
```
Write a query that select all distinct pet names.

**Solution:**
``` sql
SELECT DISTINCT(name) FROM dogs
UNION
SELECT DISTINCT(name) FROM cats;
```


***
### 4. Social Network
A new social network site has the following data tables:

**users** table:
|  id  |  name  |  sex  |
|------|--------|-------|
|  1  |  Ann  |  null  |
|  2  |  Steve  |  m  |
|  3  |  Mary  |  f  |
|  4  |  Brenda  |  f  |

**friends** table:
|  user1  |  user2  |
|---------|---------|
|  1  |  2  |
|  1  |  3  |
|  2  |  3  |

Select data that will be returned by the following SQL query:
``` sql
SELECT users.name, COUNT(*) as count FROM users
LEFT JOIN friends
ON users.id = friends.user1 OR users.id = friends.user2
WHERE users.sex = 'f'
GROUP BY users.id, users.name;
```
(Select all acceptable answers.)


**Solution:**
``` sql
Mary, 2
Brenda, 1
```


***
### 5. Sessions
App usage data are kept in the following table:
``` sql
TABLE sessions
  id INTEGER PRIMARY KEY,
  userId INTEGER NOT NULL,
  duration DECIMAL NOT NULL
```
Write a query that selects userId and average session duration for each user who has more than one session.


**Solution:**
``` sql
SELECT userId, AVG(duration) FROM sessions GROUP BY userId HAVING COUNT(userId) > 1;
```


***
### 6. Web Shop
Each item in a web shop belongs to a seller. To ensure service quality, each seller has a rating.
The data are kept in the following two tables:
``` sql
TABLE sellers
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  rating INTEGER NOT NULL

TABLE items
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  sellerId INTEGER
  FOREIGN KEY (sellerId) REFERENCES sellers(id)
```
Write a query that selects the item name and the name of its seller for each item that belongs to a seller with a rating greater than 4. The query should return the name of the item as the first column and name of the seller as the second column.


**Solution:**
``` sql
SELECT items.name, sellers.name FROM items
INNER JOIN sellers
ON items.sellerId = sellers.id
WHERE sellers.rating > 4;
```


***
### 7. Workers
The following data definition defines an organization's employee hierarchy.

An employee is a manager if any other employee has their managerId set to this employee's id. That means John is a manager if at least one other employee has their managerId set to John's id.
``` sql
TABLE employees
  id INTEGER NOT NULL PRIMARY KEY
  managerId INTEGER
  name VARCHAR(30) NOT NULL
  FOREIGN KEY (managerId) REFERENCES employees(id)
```
Write a query that selects only the names of employees who are not managers.


**Solution:**
``` sql
SELECT name FROM employees
WHERE id NOT IN (
    SELECT e1.id FROM employees AS e1 JOIN employees AS e2 ON e1.id = e2.managerId
);
```


***
### 8. Users And Roles
The following two tables are used to define users and their respective roles:
``` sql
TABLE users
  id INTEGER NOT NULL PRIMARY KEY,
  userName VARCHAR(50) NOT NULL

TABLE roles
  id INTEGER NOT NULL PRIMARY KEY,
  role VARCHAR(20) NOT NULL
```
The users_roles table should contain the mapping between each user and their roles. Each user can have many roles, and each role can have many users.

Modify the provided SQL create table statement so that:

- Only users from the users table can exist within users_roles.
- Only roles from the roles table can exist within users_roles.
- A user can only have a specific role once.


**Solution:**
``` sql
CREATE TABLE users_roles (
  userId INTEGER not null,
  roleId INTEGER not null,
  foreign key (userId) references users(id),
  foreign key (roleId) references roles(id),
  unique (userId, roleId)
);
```


***
### 9. Regional Sales Comparison
An insurance company maintains records of sales made by its employees. Each employee is assigned to a state. States are grouped under regions. The following tables contain the data:
``` sql
TABLE regions
  id INTEGER PRIMARY KEY
  name VARCHAR(50) NOT NULL

TABLE states
  id INTEGER PRIMARY KEY
  name VARCHAR(50) NOT NULL
  regionId INTEGER NOT NULL
  FOREIGN KEY (regionId) REFERENCES regions(id)

TABLE employees
  id INTEGER PRIMARY KEY
  name VARCHAR(50) NOT NULL
  stateId INTEGER NOT NULL
  FOREIGN KEY (stateId) REFERENCES states(id)

TABLE sales
  id INTEGER PRIMARY KEY
  amount INTEGER NOT NULL
  employeeId INTEGER NOT NULL
  FOREIGN KEY (employeeId) REFERENCES employees(id)  
```
Management requires a comparative region sales analysis report.

Write a query that returns:

- The region name.
- Average sales per employee for the region (Average sales = Total sales made for the region / Number of employees in the region).
- The difference between the average sales of the region with the highest average sales, and the average sales per employee for the region (average sales to be calculated as explained above).

Employees can have multiple sales. A region with no sales should be also returned. Use 0 for average sales per employee for such a region when calculating the 2nd and the 3rd column.


**Solution:**
``` sql
WITH sales_avg AS (
	SELECT r.name AS region, 
    CASE WHEN SUM(IFNULL(s.amount,0)) = 0 THEN 0
    ELSE SUM(IFNULL(s.amount,0))/COUNT(DISTINCT e.id) end AS average

	FROM regions r
	LEFT JOIN states st ON r.id = st.regionid
	LEFT JOIN employees e ON st.id = e.stateid
	LEFT JOIN sales s ON e.id = s.employeeid
	GROUP BY r.id, r.name)
 
SELECT region, average, (SELECT MAX(average) FROM sales_avg) - average AS difference
FROM sales_avg
GROUP BY 1
```

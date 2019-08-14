# SQL - 2



**ORDER BY = 정렬하기**

: ASC 내림차순 정렬, DESC 오름차순 정렬  

```mysql
-- ORDER BY
SELECT *
FROM Customers
ORDER BY CustomerID ASC

SELECT *
FROM Customers
ORDER BY CustomerID DESC
```

**LIMIT** 

:원하는 만큼만 출력

```mysql
SELECT * 
FROM Customers
LIMIT 1
```

**LIMIT & ORDER BY**

```mysql
SELECT * 
FROM Customers
LIMIT 1
```



**LEFT(column, index)**

: 왼쪽부터 index개의 column을 가져옴

```mysql
-- LEFT(column, index)
SELECT LEFT(name, 3)
FROM students

/*
Samantha Sam 
Julia Jul 
Britney Bri
*/
```

**RIGHT(column, index)**

:오른쪽부터 index개의 column을 가져옴

```mysql
-- RIGHT(column, index)
SELECT RIGHT(name, 3)
FROM students

/*
Samantha tha 
Julia lia 
Britney ney
*/
```

**SUBSTRING(column, index, index)**

:첫번째 index부터 두번째 index까지의 column을 가져옴

```mysql
-- SUBSTRING(column, index, index)
SELECT name, SUBSTRING(name, 2, 4)
FROM students

/*
Samantha aman 
Julia ulia 
Britney ritn
*/
```



**GROUP BY**

: 데이터들을 원하는 그룹으로 나눠 줌, 집계함수와 함께 사용을 많이 함. 

WHERE 대신 HAVING을 사용하며 GROUP BY 한 column은 SELECT 에 있어야 함. (집계함수안의 column은 없어도 됨.)

```mysql
-- GROUP BY와 집계함수(AVG(), SUM(), MIN(), MAX(), COUNT())
SELECT Company
     , AVG(Salary) as AVERAGE
     , SUM(Salary) as SUMMATION
FROM www_salary
GROUP BY Company

/*
Company  AVERAGE       SUMMATION
바로     1771.428571   12400
유니콘    4750          9500
*/
```

**ORDER BY & GROUP BY**

```mysql
-- ORDER BY와 GROUP BY
SELECT Company, AVG(Salary)
FROM www_salary
GROUP BY Company
ORDER BY AVG(Salary)
```

**HAVING**

```mysql
-- HAVING
SELECT Company
     , AVG(Salary) as AVERAGE
FROM www_salary
GROUP BY Company
HAVING AVG(Salary) > 3000

/*
Company  AVERAGE
유니콘    4750
*/
```


# SQL

#### 형식

SELECT 열

FROM 테이블

WHERE 조건(row에 대한 이야기)



 **`*`= 모두 선택**
```sql
-- SELECT ALL
    SELECT * 
    FROM employees;
```

**AS = 별칭 붙이기 **

- SELECT - 속성 이름 바꿔서 출력(대부분 원래 컬럼의 의미가 아닐때 사용)
- FROM -  별칭

```sql
-- SELECT Columns and AS
SELECT e.emp_name
FROM employees as e;
```

**AND, OR, IN, BETWEEN**

```sql
-- give condition with WHERE
SELECT *
FROM employees as e
WHERE e.salary >= 5000;

-- AND & OR
SELECT *
FROM employees as e
WHERE e.salary >= 5000
AND e.hire_date >= '2005-05-01';

-- IN & BETWEEN
SELECT *
FROM employees as e
WHERE e.salary in (5000, 6000);

SELECT *
FROM employees as e
WHERE e.salary BETWEEN 5000 AND 6000;
-- 5000<= e.salary <=6000
```

**DISTINCT = 중복제거**

```sql
SELECT DISTINCT city
FROM station;
```

**MOD = 나머지 계산**

```sql
SELECT *
FROM station
WHERE MOD(id, 2) = 0;
```

**COUNT = 갯수세기**

```sql
SELECT count(city)
FROM station;

-- count안에 distinct를 넣어 유니크한 갯수 세기
SELECT count(distinct city)
FROM station;
```

**LIKE = 글자 찾기**

```sql
SELECT *
FROM station
-- WHERE city LIKE 'a%'
-- WHERE City LIKE '%a%'
WHERE city LIKE '%a'

-- REGEXP (정규표현식)
SELECT DISTINCT city 
FROM station
WHERE city REGEXP '^a|^e|^i|^o|^u';
```

**NOT LIKE = 아닌 글자**

```sql
SELECT *
FROM station
WHERE city NOT LIKE 'a%'
```

**SUM = 합**

```sql
SELECT SUM(population)
FROM city
```

**AVG = 평균**

```sql
SELECT AVG(population)
FROM city
```

**MAX = 최대 , MIN = 최소**

```sql
SELECT MAX(population), MIN(population)
FROM city
```

**ROUND = 반올림**

```sql
SELECT AVG(population)
FROM city

SELECT AVG(SUM(population),2)
FROM city
```
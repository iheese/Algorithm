```sql
— sessions : userId 와 duration의 평균 조회 근데 1개 이상의 세션만 조회 
SELECT userId, AVG(duration) FROM sessions GROUP BY userId HAVING COUNT(userId) >1;

- GROUP BY : userId로 그루핑
- HAVING : 그루핑 된거 중에 1개 이상인거 

— students
SELECT COUNT(*) FROM students WHERE firstName = 'John';

— Regional Sales Comparison
WITH RegionSales AS (
    SELECT
        r.name AS regionName,
        COALESCE(SUM(s.amount) / NULLIF(COUNT(DISTINCT e.id), 0), 0) AS averageSales
    FROM
        regions r
    LEFT JOIN
        states st ON r.id = st.regionId
    LEFT JOIN
        employees e ON st.id = e.stateId
    LEFT JOIN
        sales s ON e.id = s.employeeId
    GROUP BY
        r.name
)

SELECT
    regionName,
    averageSales,
    (SELECT MAX(averageSales) FROM RegionSales) - averageSales AS difference
FROM
    RegionSales;

— Enrollment
UPDATE enrollments SET year = 2015 WHERE id BETWEEN 20 AND 100;
- BETWEEN 은 각 숫자의 이상 이하를 의미


— Users And Roles
CREATE TABLE usersRoles (
  userId INTEGER,
  roleId INTEGER,
  FOREIGN KEY(userId) REFERENCES users(id),
  FOREIGN KEY(roleId) REFERENCES roles(id),
  PRIMARY kEY(userId, roleId)
);

—Pets : 두 개의 테이블에서 결과를 합쳐서 보여준다. 
SELECT name
FROM cats
UNION
SELECT name
FROM dogs;

- 조회 결과를 중복 없이 모두 합쳐서 보여줌

SELECT name
FROM cats
UNION ALL
SELECT name
FROM dogs;

- 조회 결과를 중복 있게 모두 합쳐서 보여줌

— Workers

select name
from employees
where id not in (
                select a.id
                from employees as a
                inner join employees as b
                on a.id = b.managerId
                )

select a.name
from employees as a
left join employees as b 
on a.id = b.managerId
where b.name is null;

select name
from employees as a
where not exists
                 (
                   select name
                   from employees as b
                   where a.id = b.managerId
                 )

—Web Shop
SELECT b.name, a.name
FROM sellers AS a
INNER JOIN items AS b ON a.id = b.sellerId
WHERE a.rating > 4;
```

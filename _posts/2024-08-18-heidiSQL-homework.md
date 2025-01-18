---
layout: post
title:  "데이터베이스 숙제"
date:   2024-07-26
excerpt: "숙제"
tag:
comments: true
---

# HeidiSQL 관련 숙제
## 일반 문제 20문제에 고급 문제 5문제가 있습니다.

### 1. employees테이블의 employee_id가 5보다 작은 행을 검색
``` SELECT * FROM employees WHERE employee_id < 5; ```
### 2. employees테이블의 name열만 조회
``` SELECT name FROM employees; ```
### 3. employees테이블의 employee_id가 1 또는 2 또는 4인 행을 검색
``` SELECT * FROM employees WHERE employee_id IN (1,2,4); ```
### 4. items테이블의 item_id가 5보다 큰 행을 item_name열만 조회
```select DISTINCT item_name from items WHERE item_id > 5;```
### 5. employees테이블의 id는 5보다 크고  hourly_pay은 10보다 큰 행을 검색
```SELECT * FROM employees WHERE employee_id > 5 AND hourly_pay > 10;```
### 6. employees테이블의 id는 5보다 크거나  hourly_pay은 10보다 큰 행을 검색
```SELECT * FROM employees WHERE employee_id > 5 or hourly_pay > 10;```
### 7. employees테이블의 id가 5인 데이터를 hourly_pay 15로 수정
```UPDATE employees SET hourly_pay = 15 WHERE employee_id = 5;```
### 8. items테이블의 item_id값이 5보다 크고 10보다 작은 행을 검색
```SELECT * FROM items where item_id > 5 AND item_id < 10;```
### 9. sales테이블의 employee_id값을 내림차순으로 검색
```SELECT employee_id FROM sales ORDER BY employee_id DESC;```
### 10. items테이블의 item_id값을 오름차순으로 검색
```SELECT item_id from items ORDER BY item_id ASC;```
### 11. items테이블의 item_name값이 'oo' 또는 'ee'값이 포함되어 있는 행을 검색
```select * from items where item_name LIKE '%oo%' or item_name LIKE '%ee%';```
### 12. items테이블의 item_name값이 'oo'와 'ee' 둘 다 포함되어 있지 않은 행을 검색
```select * from items where item_name not LIKE '%oo%' and item_name not LIKE '%ee%';```
### 13. items테이블의 item_name값이 'CHEESE'인 행을 item_name열을 'ITEM NAME'로 별칭을 부여한 뒤 검색
```SELECT * FROM items AS ITEMNAME WHERE ITEMNAME.item_name = 'Cheese';```
### 14. sales테이블의 item_id값이 5이고  employee_id값이 2인 행의 수를 얻기
```SELECT COUNT(*) FROM sales WHERE item_id = 5 AND employee_id = 2;```
### 15. items테이블의 price열의 평균값을 얻기
```SELECT AVG(price) FROM items;```
### 16. employees테이블 hourly_pay열의 최소값을 얻기
```SELECT MIN(hourly_pay) FROM employees;```
### 17. items테이블 price열의 최대값을 얻기
```SELECT MAX(price) FROM items;```
### 18. sales테이블의 employee_id값이 2와 20인 경우를 UNION을 사용하여 검색
```SELECT * FROM sales WHERE employee_id = 2 UNION SELECT * FROM sales WHERE employee_id = 20;```
### 19. sales테이블의 employee_id별 판매한 아이템의 수
```SELECT employee_id, COUNT(*) from sales GROUP BY employee_id;```
### 20. sales테이블의 employee_id별 판매한 아이템이 15개 이상인 employee들을 employee_id로 오름차순 정렬한 결과를 조회
```SELECT employee_id, COUNT(*) from sales GROUP BY employee_id HAVING COUNT(*) >= 15 ORDER BY employee_id ASC;```

<span style="color:red">

# 고급 문제

</span>

## **1. 직원 이름 중 '샘' 이라는 글자가 들어간 직원들의 총 판매금액**
```SELECT SUM(C.price) AS 총합  From employees A, sales B, items C WHERE A.employee_id = B.employee_id AND B.item_id = C.item_id and A.name LIKE '%샘%';```
## **2. 제품별 판매횟수를 큰 순서로 정렬**
```SELECT A.item_name, COUNT(*) FROM items A, sales B WHERE A.item_id = B.item_id GROUP BY B.item_id order by COUNT(*) DESC;```
## **3. 가장 판매 횟수가 높은 제품 이름**
```SELECT A.item_name, count(B.item_id) AS C FROM items A, sales B WHERE A.item_id = B.item_id GROUP BY A.item_name order BY C DESC LIMIT 1;```
## **4. 가장 판매금액이 높은 직원 이름**
```SELECT A.name, SUM(D.price) AS S FROM employees A, sales B, items D WHERE A.employee_id = B.employee_id AND D.item_id = B.item_id group BY A.name order BY S DESC LIMIT 1;```
## **5. 각 POSITION별 시급(HOURLY_PAY)이 높은 직원 이름**
```SELECT NAME, A.POSITION, hourly_pay FROM employees A, (SELECT POSITION, MAX(hourly_pay) AS C FROM employees GROUP BY position) B WHERE B.position = A.position AND A.hourly_pay = B.C```

일반 문제는 생각보다 쉬웠고, 고급 문제의 문제가 단순해서 할만 할 줄 알았는데 아니더라구요;;
그래도 다 풀어서 뿌듯합니다. ^^   
그리고 문제를 푼지 한참 되었는데 까먹어서~~귀찮아서~~ 안올렸습니다ㅎㅎ

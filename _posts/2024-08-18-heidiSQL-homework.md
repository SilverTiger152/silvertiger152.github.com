---
layout: post
title:  "데이터베이스 숙제"
date:   2024-07-26
excerpt: "숙제"
tag:
comments: true
---

# HeidiSQL 관련 숙제
## 일반 문제 20문제에 고급 문제 5문제가 있습니다. 2024년 8월 18일에는 일반 문제 1번에서 13번까지 진행했습니다.

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

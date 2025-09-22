# SQL_ADVANCED 2주차 정규 과제 

## Week 2 :집합 연산자 & 그룹 함수

📌**SQL_ADVANCED 정규과제**는 매주 정해진 주제에 따라 **MySQL 공식 문서 또는 한글 블로그 자료를 참고해 개념을 정리한 후, 프로그래머스/ Solvesql / LeetCode에서 SQL 3문제**와 **추가 확인문제**를 직접 풀어보며 학습하는 과제입니다. 

이번 주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 주제를 중심으로 개념을 학습하고, 주차별 **학습 목표**에 맞게 정리해주세요. 정리한 내용은 GitHub에 업로드한 후, **스프레드시트의 'SQL' 시트에 링크를 제출**해주세요. 



**👀 (수행 인증샷은 필수입니다.)** 

> 프로그래머스 문제를 풀고 '정답입니다' 문구를 캡쳐해서 올려주시면 됩니다. 



## SQL_ADVANCED_2nd

**1. 집합 연산자**

### 15.2.18. UNION Clause

### 15.2.14. Set Operations with UNION, INTERSECT

- UNION, UNION ALL 중심으로 개념을 정리하고, INTERSECT, EXCEPT는 구문이 어떤 기능을 하는지 간단히만 알아봅니다. EXCEPT와 INTERSECT는 대부분 MySQL 버전에서 공식 지원되지 않기 때문에, **이번주 학습은 `UNION, UNION ALL` 만 집중적으로 정리해주세요.**

**2. 그룹 함수 (집계 함수)**

### 14.19.1. Aggregate Function Descriptions



## 🏁 주차별 학습 (Study Schedule)

| 주차  | 공부 범위               | 완료 여부 |
| ----- | ----------------------- | --------- |
| 1주차 | 서브쿼리 & CTE          | ✅         |
| 2주차 | 집합 연산자 & 그룹 함수 | ✅         |
| 3주차 | 윈도우 함수             | 🍽️         |
| 4주차 | Top N 쿼리              | 🍽️         |
| 5주차 | 계층형 질의와 셀프 조인 | 🍽️         |
| 6주차 | PIVOT / UNPIVOT         | 🍽️         |
| 7주차 | 정규 표현식             | 🍽️         |



### 공식 문서 활용 팁

>  **MySQL 공식 문서는 영어로 제공되지만, 크롬 브라우저에서 공식 문서를 열고 이 페이지 번역하기에서 한국어를 선택하면 번역된 버전으로 확인할 수 있습니다. 다만, 번역본은 문맥이 어색한 부분이 종종 있으니 영어 원문과 한국어 번역본을 왔다 갔다 하며 확인하거나, 교육팀장의 정리 예시를 참고하셔도 괜찮습니다.**



# 1️⃣ 학습 내용 

> 아래의 링크를 통해 *MySQL 공식문서*로 이동하실 수 있습니다.
>
> - 15.2.18. UNION Clause : MySQL 공식문서 
>
> https://dev.mysql.com/doc/refman/8.0/en/union.html
>
> - 15.2.14. Set Operations with UNION, INTERSECT : MySQL 공식문서
>
> https://dev.mysql.com/doc/refman/8.0/en/set-operations.html
>
> (한국어 버전) https://dart-b-official.github.io/posts/mysql-UNION/
>
> - 14.19.1. Aggregate Function Descriptions : MySQL 공식문서
>
> https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html
>
> (한국어 버전) https://dart-b-official.github.io/posts/mysql-aggregate_function/



<!-- 여기까진 그대로 둬 주세요-->

# 2️⃣ 학습 내용 정리하기

## 1. 집합 연산자

~~~
✅ 학습 목표 :
* UNION과 UNION ALL의 차이와 사용법을 이해한다.
* 중복 제거 여부, 컬럼 정렬 조건 등을 고려하여 올바르게 집합 연산자를 사용할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

예시에서 헤더와 데이터를 구분하지 못해서 한참 헤맸으나 해결했다.<br>
UNION에선 중복이 제거된다. 중복값도 모두 보기 위해선 UNION ALL을 이용한다.<br>
JOIN이 가로로 합치는 것 이라면, UNION은 세로로 합치는 것 인 것 같다.

집합연산
- UNION: 두 쿼리 블록의 모든 결과를 결합하고, 중복 제거
    - 교환법칙 성립
- INTERSECT: 두 쿼리 블록 모두에 공통으로 존재하는 행만 반환, 중복 제거
    - 교환법칙 성립
- EXCEPT: 두 쿼리 블록 A, B에서 A에만 존제하고 B에는 없는 행 반환, 중복 제거
    - 교환법칙 불가
- 집합 연산자 + ALL: 중복을 제거하지 않음
- 집합 연산자 + DiSTINCT: 중복을 제거함(기본값, 생략 가능)

ORDER BY, LIMIT을 전체 결과에 적용하려면 마지막에 배치한다.


## 2. 그룹함수

~~~
✅ 학습 목표 :
* COUNT, SUM, AVG, MAX, MIN 함수의 기본 사용법을 익힌다.
* GROUP BY와 HAVING 절을 적절히 활용할 수 있다.
* NULL과 집계 함수가 어떻게 상호작용하는지 이해한다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

주요 집계 함수 목록
- AVG()
- COUNT()
- MAX()
- MIN()
- SUM()

시간형에 동작하지 않는 집계 함수
- SUM()
- AVG()

<hr/>

AVG([DISTINCT]expr)[over_clause]
- expr의 평균값을 반환한다. DISTINCT의 경우 서로 다른 값 만의 평균을 구한다.
- 일치 행이 없거나 expr이 NULL이면 NULL을 반환한다.
- OVER 사용 시 윈도 함수로 실행 가능하다.

COUNT
- (*)으로 정확한 총 행수를 저장하지 않으므로 가시 행만 집계
- COUNT(DISTINCT expr[,expr...])
    - 서로 다른 NULL이 아닌 표현식(들)의 조합 수

<br><br>

---

# 3️⃣ 실습 문제

https://leetcode.com/problems/customers-who-never-order/

> LeetCode 183. Customers Who never Order
>
> 학습 포인트 : 주문 내역이 없는 고객을 찾기 위한 패턴 익히기  

초안
~~~sql
# Write your MySQL query statement below
SELECT
    c.name
FROM Customers AS c
JOIN (
    SELECT
        id
    FROM Orders) as O
ON c.id = o.customerID
WHERE
    c.id IS NOT NULL
~~~
에러가 발생했다.
- JOIN 내부쿼리가 필요하지 않음
- JOIN이 아닌 INNER JOIN이 필요함
- 마지막 WHERE문에서 c.id가 아닌 o.id가 사용되어야 함



최종 답안
~~~sql
SELECT
    c.name as Customers
FROM Customers AS c
LEFT JOIN Orders as o
ON c.id = o.customerID
WHERE
    o.id IS NULL
~~~



https://leetcode.com/problems/department-highest-salary/description/

> LeetCode 184. Department Highest Salary
>
> 학습 포인트 : 부서별 최고 연봉자 추출을 위한 **그룹별 정렬 / 필터링** 방식 이해하기


~~~sql
SELECT
    D.name AS Department,
    E.name AS Employee,
    E.salary AS Salary
FROM Employee as E
LEFT JOIN Department as D
    ON E.departmentId = D.id
WHERE (E.departmentID, E.salary) IN (
    SELECT 
        S.departmentId,
        MAX(s.salary)
    FROM Employee as S
    GROUP BY departmentId
)
~~~
서브쿼리를 WHERE문에 사용하는 것 에서 어려움을 겪었지만, '2 컬럼 IN' 을 사용하여 해결했다.

---

## 문제 인증란

<!-- 이 주석을 지우고 여기에 문제 푼 인증사진을 올려주세요. -->

<img width="686" height="443" alt="image" src="https://github.com/user-attachments/assets/88d1d949-6e7d-4dba-b463-49d983c5c01a" />

<img width="685" height="440" alt="image" src="https://github.com/user-attachments/assets/02b36bc7-5612-4af6-9521-deabc8850a00" />


---

# 확인문제

## 문제 1

> **🧚동혁이는 SQL 문제를 풀면서 `UNION과 UNION ALL`의 차이를 명확히 이해하지 못해 중복된 값이 생기거나 누락되는 문제를 계속 겪고 있습니다.** 아래는 동혁이가 작성한 쿼리입니다.

~~~sql
SELECT name FROM member
UNION
SELECT name FROM blackList;
~~~

> **그런데 예상과 달리 blacklist에만 있는 이름이 결과에 안 나오거나, 중복된 이름이 사라져서 헷갈리고 있습니다. UNION과 UNION ALL의 차이를 설명하고, 중복 포함 여부에 따라 어떤 경우에 어떤 쿼리를 써야 하는지 예시와 함께 설명해주세요**

<br>

~~~sql
SELECT name FROM member
UNION ALL
SELECT name FROM blackList;
~~~
UNION만 사용하는 경우 중복된 값은 제거되기 때문에 중복 관계없이 모든 내용을 확인하고 싶을 때는 UNION ALL을 사용해야 한다.

## 참고자료
그룹 함수가 많아서 중요하게 많이 쓰이는 함수들을 정리해놓은 참고자료를 첨부합니다. 아래 블로그를 통해서 더욱 쉽게 공부해보시고 문제를 풀어보세요.
1. [SQL 10] 그룹 함수, GROUP BY 절, HAVING 절
https://keep-cool.tistory.com/37

또한, MySQL 문서 이외에 Oracle 함수에서 사용하는 그룹함수에 대한 소개도 같이 첨부합니다. SQLD 시험 준비하시는 분이 있다면 이 자격증 시험에서는 Oracle 언어를 기반으로 문제가 출제하오니 아래 블로그도 같이 공부해보세요. (선택사항입니다.)
2. 그룹 함수 (Group FUNCTION)
https://dkkim2318.tistory.com/48

<br>

### 🎉 수고하셨습니다.

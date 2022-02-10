---
title: "[programmers-SQL] SELECT-역순 정렬하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SELECT
  - 역순 정렬하기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SELECT-역순 정렬하기"
toc_icon: "bookmark"
---

# 문제 설명

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| INTAKE_CONDITION | VARCHAR(N) | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_INTAKE  | VARCHAR(N) | FALSE    |

동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

| NAME   | DATETIME            |
| ------ | ------------------- |
| Rocky  | 2016-06-07 09:17:00 |
| Shelly | 2015-01-29 15:01:00 |
| Benji  | 2016-04-19 13:28:00 |
| Jackie | 2016-01-03 16:25:00 |
| *Sam   | 2016-03-13 11:17:00 |

..이하 생략

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT NAME, DATETIME 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID DESC;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 모든 동물의 이름과 보호 시작일을 조회하기 위해 `NAME`, `DATETIME`의 열을 콤마(,)를 통해서 복수 열을 선택하였습니다. 

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## ORDER BY 구
- 문제에서 동물 보호소에 들어온 모든 동물의 정보를 `ANIMAL_ID` 역순으로 조회하라고 했기 때문에 ORDER BY 뒤에 `ANIMAL_ID DESC`를 지정해줍니다.
- `ANIMAL_ID` 뒤에 DESC(descendant)를 지정해주면 내림차순으로 정렬됩니다.

# Reference

> [Programmers - SQL 고득점 Kit (역순 정렬하기)](https://programmers.co.kr/learn/courses/30/lessons/59035)<br>
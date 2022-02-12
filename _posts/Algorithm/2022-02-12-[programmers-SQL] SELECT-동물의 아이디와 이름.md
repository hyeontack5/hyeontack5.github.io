---
title: "[programmers-SQL] SELECT-동물의 아이디와 이름"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SELECT
  - 동물의 아이디와 이름
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SELECT-동물의 아이디와 이름"
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

동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID | NAME         |
| --------- | ------------ |
| A349996   | Sugar        |
| A350276   | Jewel        |
| A350375   | Meo          |
| A352555   | Harley       |
| A352713   | Gia          |
| A352872   | Peanutbutter |
| A353259   | Bj           |

((이하 생략))

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 동물 보호소에 들어온 모든 동물의 아이디와 이름을 조회하기 위해 `ANIMAL_ID`, `NAME`의 열을 콤마(,)를 통해서 복수 열을 선택하였습니다. 

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## ORDER BY 구
- 문제에서 아이디 순으로 조회하라고 했기 때문에 ORDER BY 뒤에 `ANIMAL_ID`를 지정해줍니다.
- `ANIMAL_ID` 뒤에 아무것도 지정해주지 않으면 Mysql 같은 경우 default가 ASC(asendanct), 오름차순으로 정렬됩니다.

# Reference

> [Programmers - SQL 고득점 Kit (동물의 아이디와 이름)](https://programmers.co.kr/learn/courses/30/lessons/59403)<br>
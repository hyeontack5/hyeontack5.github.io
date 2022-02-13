---
title: "[programmers-SQL] IS NULL-이름이 없는 동물의 아이디"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - IS NULL
  - 이름이 없는 동물의 아이디
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] IS NULL-이름이 없는 동물의 아이디"
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

동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME       | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ---------- | --------------- |
| A368930   | Dog         | 2014-06-08 13:20:00 | Normal           | NULL       | Spayed Female   |
| A524634   | Dog         | 2015-01-02 18:54:00 | Normal           | *Belle     | Intact Female   |
| A465637   | Dog         | 2017-06-04 08:17:00 | Injured          | *Commander | Neutered Male   |

이름이 없는 채로 들어온 동물의 ID는 A368930입니다. 따라서 SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID |
| --------- |
| A368930   |

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID 
FROM ANIMAL_INS 
WHERE NAME IS NULL
ORDER BY ANIMAL_ID ASC;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하기 위해 `ANIMAL_ID`의 열을 지정합니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## WHERE 구
- WHERE는 테이블에서 조건에 의해서 행을 제한하는 역할을 합니다.
- 이름이 없는 채로 들어온 동물만 행으로 제한하기 위해 `NAME IS NULL`인 행만을 나타냅니다.

## ORDER BY 구
- ORDER BY 뒤에 복수 열을 지정하여 정렬 순서 조건을 중복하여 조정할 수 있습니다.
- 문제에서 동물의 ID는 오름차순으로 정렬하라는 조건이 있기 때문에 ORDER BY 뒤에 `ANIMAL_ID ASC`을 지정하여 오름차순으로 정렬하여 조회되도록 합니다.

# Reference

> [Programmers - SQL 고득점 Kit (이름이 없는 동물의 아이디)](https://programmers.co.kr/learn/courses/30/lessons/59039)<br>
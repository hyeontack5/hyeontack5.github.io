---
title: "[programmers-SQL] GROUP BY-동명 동물 수 찾기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - GROUP BY
  - 동명 동물 수 찾기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] GROUP BY-동명 동물 수 찾기"
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

동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME   | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ------ | --------------- |
| A396810   | Dog         | 2016-08-22 16:13:00 | Injured          | Raven  | Spayed Female   |
| A377750   | Dog         | 2017-10-25 17:17:00 | Normal           | Lucy   | Spayed Female   |
| A355688   | Dog         | 2014-01-26 13:48:00 | Normal           | Shadow | Neutered Male   |
| A399421   | Dog         | 2015-08-25 14:08:00 | Normal           | Lucy   | Spayed Female   |
| A400680   | Dog         | 2017-06-17 13:29:00 | Normal           | Lucy   | Spayed Female   |
| A410668   | Cat         | 2015-11-19 13:41:00 | Normal           | Raven  | Spayed Female   |

- Raven 이름은 2번 쓰였습니다.
- Lucy 이름은 3번 쓰였습니다
- Shadow 이름은 1번 쓰였습니다.

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| NAME  | COUNT |
| ----- | ----- |
| Lucy  | 3     |
| Raven | 2     |

# 문제 정답 - [Mysql]

```sql
-- 코드를 입력하세요
SELECT NAME, COUNT(NAME) AS "COUNT"
FROM ANIMAL_INS
GROUP BY NAME
HAVING COUNT(NAME) >= 2
ORDER BY NAME ASC;
```

# 문제 풀이

**실행 순서**
- FROM -> GROUP BY -> HAVING -> SELECT -> ORDER BY 순

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 문제에서 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하기 위해 `NAME`과 `COUNT(NAME)`을 이용하여 그룹화된 동물의 이름과 해당 이름이 쓰인 횟수를 가져올 수 있습니다.
  - `COUNT(NAME)`을 `AS COUNT`를 이용하여 COUNT 별명으로 지정해줬습니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## GROUP BY 구
- 특정 열(컬럼/필드)를 그룹화하는 키워드입니다.
- `GROUP BY NAME`을 이용하여 동물의 이름으로 그룹화해줬습니다.
  - 이름이 없는 동물은 집계에서 제외하는 조건은 GROUP BY를 해주게 되면 NULL을 제외하고 그룹으로 만들어줍니다.

## HAVING 구
- 문제에서 동물 이름 중 두 번 이상 쓰인 이름을 조회하기 위해 `HAVING COUNT(NAME) >= 2`으로 조건을 설정해줬습니다.

## ORDER BY 구
- 문제에서 결과는 이름 순으로 조회하라는 조건이 있었기 때문에 `ORDER BY NAME ASC`으로 오름차순으로 정렬하였습니다.

# Reference

> [Programmers - SQL 고득점 Kit (동명 동물 수 찾기)](https://programmers.co.kr/learn/courses/30/lessons/59041)<br>
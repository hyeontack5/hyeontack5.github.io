---
title: "[programmers-SQL] SELECT-여러 기준으로 정렬하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SELECT
  - 여러 기준으로 정렬하기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SELECT-여러 기준으로 정렬하기"
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

동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.

**예시**

예를 들어, `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME  | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ----- | --------------- |
| A349996   | Cat         | 2018-01-22 14:32:00 | Normal           | Sugar | Neutered Male   |
| A350276   | Cat         | 2017-08-13 13:50:00 | Normal           | Jewel | Spayed Female   |
| A396810   | Dog         | 2016-08-22 16:13:00 | Injured          | Raven | Spayed Female   |
| A410668   | Cat         | 2015-11-19 13:41:00 | Normal           | Raven | Spayed Female   |

1. 이름을 사전 순으로 정렬하면 다음과 같으며, 'Jewel', 'Raven', 'Sugar'
2. 'Raven'이라는 이름을 가진 개와 고양이가 있으므로, 이 중에서는 보호를 나중에 시작한 개를 먼저 조회합니다.

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME  | DATETIME            |
| --------- | ----- | ------------------- |
| A350276   | Jewel | 2017-08-13 13:50:00 |
| A396810   | Raven | 2016-08-22 16:13:00 |
| A410668   | Raven | 2015-11-19 13:41:00 |
| A349996   | Sugar | 2018-01-22 14:32:00 |

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME, DATETIME DESC;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하기 위해 `ANIMAL_ID`, `NAME`, `DATETIME`의 열을 콤마(,)를 통해서 복수 열을 선택하였습니다. 

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## ORDER BY 구
- ORDER BY 뒤에 복수 열을 지정하여 정렬 순서 조건을 중복하여 조정할 수 있습니다.
- 문제에서 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 하기 때문에 ORDER BY 뒤에 `NAME`을 지정하여 오름차순으로 정렬하고 
이름이 같은 경우에 `DATETIME DESC`를 이용하여 보호를 나중에 시작한 동물을 조회하게 하였습니다.

# Reference

> [Programmers - SQL 고득점 Kit (여러 기준으로 정렬하기)](https://programmers.co.kr/learn/courses/30/lessons/59404)<br>
---
title: "[programmers-SQL] SUM, MAX, MIN-중복 제거하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SUM, MAX, MIN
  - 중복 제거하기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SUM, MAX, MIN-중복 제거하기"
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

동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME     | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | -------- | --------------- |
| A562649   | Dog         | 2014-03-20 18:06:00 | Sick             | NULL     | Spayed Female   |
| A412626   | Dog         | 2016-03-13 11:17:00 | Normal           | *Sam     | Neutered Male   |
| A563492   | Dog         | 2014-10-24 14:45:00 | Normal           | *Sam     | Neutered Male   |
| A513956   | Dog         | 2017-06-14 11:54:00 | Normal           | *Sweetie | Spayed Female   |

보호소에 들어온 동물의 이름은 NULL(없음), `*Sam`, `*Sam`, `*Sweetie`입니다. 이 중 NULL과 중복되는 이름을 고려하면, 보호소에 들어온 동물 이름의 수는 2입니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| count |
| ----- |
| 2     |

※ 컬럼 이름(위 예제에서는 count)은 일치하지 않아도 됩니다.

# 문제 정답 - [Mysql]

```sql
-- 코드를 입력하세요
SELECT COUNT(DISTINCT NAME) AS count
FROM ANIMAL_INS;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- `DISTINCT 열명`을 이용하면 열명으로 지정한 행의 중복을 제거할 수 있습니다.
  - `DISTINCT NAME`을 이용하여 NAME열의 중복된 값을 제거합니다.
- `COUNT()` 함수를 통해 행 수를 집계할 수 있습니다.
  - `COUNT(DISTINCT NAME)`를 통해 중복 제거된 NAME열의 행 수를 집계합니다.
- 문제에서는 컬럼 이름은 위 예제와 일치하지 않아도 된다고 하였지만 `AS count`를 이용하여 지정해줬습니다.


## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

# Reference

> [Programmers - SQL 고득점 Kit (중복 제거하기)](https://programmers.co.kr/learn/courses/30/lessons/59408)<br>
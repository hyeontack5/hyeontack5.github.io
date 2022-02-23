---
title: "[programmers-SQL] GROUP BY-고양이와 개는 몇 마리 있을까"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - GROUP BY
  - 고양이와 개는 몇 마리 있을까
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] GROUP BY-고양이와 개는 몇 마리 있을까"
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

동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ---- | --------------- |
| A373219   | Cat         | 2014-07-29 11:43:00 | Normal           | Ella | Spayed Female   |
| A377750   | Dog         | 2017-10-25 17:17:00 | Normal           | Lucy | Spayed Female   |
| A354540   | Cat         | 2014-12-11 11:48:00 | Normal           | Tux  | Neutered Male   |

고양이는 2마리, 개는 1마리 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_TYPE | count |
| ----------- | ----- |
| Cat         | 2     |
| Dog         | 1     |

# 문제 정답 - [Mysql]

```sql
-- 코드를 입력하세요
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS count
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE;
```

# 문제 풀이

**실행 순서**
- FROM -> GROUP BY -> SELECT -> ORDER BY 순

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 문제에서 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하기 위해 `ANIMAL_TYPE`과 `COUNT(ANIMAL_TYPE)`을 이용하여 동물 종류의 수를 가져올 수 있습니다.
  - `COUNT(ANIMAL_TYPE)`을 `AS count`를 이용하여 count 별명으로 지정해줬습니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## GROUP BY 구
- 특정 열(컬럼/필드)를 그룹화하는 키워드입니다.
- `GROUP BY ANIMAL_TYPE`을 이용하여 동물의 종류별로 그룹화해줬습니다.
  - Cat, Dog로 그룹화 됩니다.

## ORDER BY 구
- 문제에서 고양이를 개보다 먼저 조회하라는 조건이 있었기 때문에 `ORDER BY ANIMAL_TYPE`으로 오름차순으로 정렬하였습니다.
  - `ANIMAL_TYPE`의 자료형은 `VARCHAR(N)` 타입이기 때문에 Cat, Dog 순으로 정렬됩니다.

# Reference

> [Programmers - SQL 고득점 Kit (고양이와 개는 몇 마리 있을까)](https://programmers.co.kr/learn/courses/30/lessons/59040)<br>
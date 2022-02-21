---
title: "[programmers-SQL] SUM, MAX, MIN-최솟값 구하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SUM, MAX, MIN
  - 최솟값 구하기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SUM, MAX, MIN-최솟값 구하기"
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

동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME     | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | -------- | --------------- |
| A399552   | Dog         | 2013-10-14 15:38:00 | Normal           | Jack     | Neutered Male   |
| A379998   | Dog         | 2013-10-23 11:42:00 | Normal           | Disciple | Intact Male     |
| A370852   | Dog         | 2013-11-03 15:04:00 | Normal           | Katie    | Spayed Female   |
| A403564   | Dog         | 2013-11-18 17:03:00 | Normal           | Anna     | Spayed Female   |

가장 먼저 들어온 동물은 Jack이고, Jack은 2013-10-14 15:38:00에 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| 시간                |
| ------------------- |
| 2013-10-14 15:38:00 |

※ 컬럼 이름(위 예제에서는 "시간")은 일치하지 않아도 됩니다.

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT MIN(DATETIME) as "시간"
FROM ANIMAL_INS;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 가장 먼저 들어온 동물을 조회하기 위해 `MIN(DATETIME)`를 이용하여 열을 선택하였고 이 결과를 별명으로 "시간"으로 설정해주기 위해 AS를 사용하여 지정해줍니다.
  - 문제 조건에서 컬럼 이름은 위 예제 처럼 "시간"은 일치하지 않아도 된다고 하였지만 일치시켰습니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

# Reference

> [Programmers - SQL 고득점 Kit (최솟값 구하기)](https://programmers.co.kr/learn/courses/30/lessons/59038)<br>
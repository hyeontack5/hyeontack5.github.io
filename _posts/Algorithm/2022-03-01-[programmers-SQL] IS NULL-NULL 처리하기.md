---
title: "[programmers-SQL] IS NULL-NULL 처리하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - IS NULL
  - NULL 처리하기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] IS NULL-NULL 처리하기"
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

입양 게시판에 동물 정보를 게시하려 합니다. 동물의 생물 종, 이름, 성별 및 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 프로그래밍을 모르는 사람들은 NULL이라는 기호를 모르기 때문에, 이름이 없는 동물의 이름은 "No name"으로 표시해 주세요.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME  | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ----- | --------------- |
| A350276   | Cat         | 2017-08-13 13:50:00 | Normal           | Jewel | Spayed Female   |
| A350375   | Cat         | 2017-03-06 15:01:00 | Normal           | Meo   | Neutered Male   |
| A368930   | Dog         | 2014-06-08 13:20:00 | Normal           | NULL  | Spayed Female   |

마지막 줄의 개는 이름이 없기 때문에, 이 개의 이름은 "No name"으로 표시합니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_TYPE | NAME    | SEX_UPON_INTAKE |
| ----------- | ------- | --------------- |
| Cat         | Jewel   | Spayed Female   |
| Cat         | Meo     | Neutered Male   |
| Dog         | No name | Spayed Female   |

※ 컬럼 이름은 일치하지 않아도 됩니다.

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT ANIMAL_TYPE, 
CASE 
	WHEN NAME IS NULL THEN "No name" 
    ELSE NAME 
END AS "NAME",
SEX_UPON_INTAKE
FROM ANIMAL_INS
ORDER BY ANIMAL_ID ASC;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 동물의 생물 종, 이름, 성별 및 중성화 여부를 조회하기 위해 `ANIMAL_TYPE`, `NAME`, `SEX_UPON_INTAKE`을 지정하였습니다.
- 이름이 없는 동물의 이름은 "No name"으로 표시하기 위해 CASE 문을 이용하여 NAME 열이 NULL이면 "No name"으로 변경하고
그 이외에는 NAME이 그대로 나오도록 하였습니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## ORDER BY 구
- 문제에서 아이디 순으로 정렬 조건이 있기 때문에 ORDER BY 뒤에 `ANIMAL_ID ASC`을 지정하여 오름차순으로 정렬하였습니다.

# Reference

> [Programmers - SQL 고득점 Kit (NULL 처리하기)](https://programmers.co.kr/learn/courses/30/lessons/59410)<br>
---
title: "[programmers-SQL] SELECT-어린 동물 찾기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - SELECT
  - 어린 동물 찾기
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] SELECT-어린 동물 찾기"
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

동물 보호소에 들어온 동물 중 젊은 동물의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

**예시**

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME     | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | -------- | --------------- |
| A365172   | Dog         | 2014-08-26 12:53:00 | Normal           | Diablo   | Neutered Male   |
| A367012   | Dog         | 2015-09-16 09:06:00 | Sick             | Miller   | Neutered Male   |
| A365302   | Dog         | 2017-01-08 16:34:00 | Aged             | Minnie   | Spayed Female   |
| A381217   | Dog         | 2017-07-08 09:41:00 | Sick             | Cherokee | Neutered Male   |

이 중 젊은 동물은 Diablo, Miller, Cherokee입니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME     |
| --------- | -------- |
| A365172   | Diablo   |
| A367012   | Miller   |
| A381217   | Cherokee |

# 문제 정답

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
WHERE INTAKE_CONDITION <> "Aged"
ORDER BY ANIMAL_ID;
```

# 문제 풀이

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 동물 보호소에 들어온 동물 중 아픈 동물의 아이디와 이름을 조회하기 위해 `ANIMAL_ID`, `NAME`의 열을 콤마(,)를 통해서 복수 열을 선택하였습니다. 

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_INS` 테이블을 지정해 가져옵니다.

## WHERE 구
- WHERE는 테이블에서 조건에 의해서 행을 제한하는 역할을 합니다.
- WHERE 뒤에 `INTAKE_CONDITION`이라는 열에서 `"Aged"`이라는 문자열을 가지고 있지 않은 행을 조회한다는 뜻입니다.

## ORDER BY 구
- 문제에서 아이디 순으로 조회하라고 했기 때문에 ORDER BY 뒤에 `ANIMAL_ID`를 지정해줍니다.
- `ANIMAL_ID` 뒤에 아무것도 지정해주지 않으면 Mysql 같은 경우 default가 ASC(asendanct), 오름차순으로 정렬됩니다.

# Reference

> [Programmers - SQL 고득점 Kit (어린 동물 찾기)](https://programmers.co.kr/learn/courses/30/lessons/59037)<br>
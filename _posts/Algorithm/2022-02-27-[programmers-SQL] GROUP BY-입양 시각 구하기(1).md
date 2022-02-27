---
title: "[programmers-SQL] GROUP BY-입양 시각 구하기(1)"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - GROUP BY
  - 입양 시각 구하기(1)
toc: true
toc_sticky: true
toc_label: "[programmers-SQL] GROUP BY-입양 시각 구하기(1)"
toc_icon: "bookmark"
---

# 문제 설명

`ANIMAL_OUTS` 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. `ANIMAL_OUTS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `NAME`, `SEX_UPON_OUTCOME`는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_OUTCOME | VARCHAR(N) | FALSE    |

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

**예시**

SQL문을 실행하면 다음과 같이 나와야 합니다.

| HOUR | COUNT |
| ---- | ----- |
| 9    | 1     |
| 10   | 2     |
| 11   | 13    |
| 12   | 10    |
| 13   | 14    |
| 14   | 9     |
| 15   | 7     |
| 16   | 10    |
| 17   | 12    |
| 18   | 16    |
| 19   | 2     |

# 문제 정답 - [Mysql]

```sql
-- 코드를 입력하세요
SELECT HOUR(DATETIME) AS HOUR, COUNT(DATETIME) AS COUNT
FROM ANIMAL_OUTS
GROUP BY HOUR(DATETIME)
HAVING HOUR >= 9 AND HOUR <= 19
ORDER BY HOUR ASC;
```

# 문제 풀이

**실행 순서**
- FROM -> GROUP BY -> HAVING -> SELECT -> ORDER BY 순

## SELECT 구
- SELECT는 테이블에서 하나 이상의 열(컬럼/필드)를 가져오는 키워드입니다.
- 문제에서 몇 시에 입양이 가장 활발한지 시간대와 입양의 건수를 나타내기 위해 HOUR를 이용하여 DATETIME의 시간을 추출할 수 있고, COUNT를 이용하여 그룹화된 DATETIME에 대해 입양의 건수를 측정할 수 있습니다.
  - `HOUR(DATETIME)`과 `COUNT(DATETIME)`을 각각 HOUR와 COUNT로 별칭을 설정하였습니다.

## FROM 구
- FROM는 테이블을 가져오는 키워드입니다.
- 문제에서 주어진 `ANIMAL_OUTS` 테이블을 지정해 가져옵니다.

## GROUP BY 구
- 특정 열(컬럼/필드)를 그룹화하는 키워드입니다.
- `GROUP BY HOUR(DATETIME)`을 이용하여 시간대별로 그룹화해줬습니다.

## HAVING 구
- 문제에서 09:00부터 19:59까지 시간을 조회하기 위해 `HAVING HOUR >= 9 AND HOUR <= 19`으로 조건을 설정해줬습니다.

## ORDER BY 구
- 문제에서 결과는 시간대 순으로 정렬 조건이 있었기 때문에 `ORDER BY HOUR ASC`으로 오름차순으로 정렬하였습니다.
  - SELECT 구에서 HOUR(DATETIME)을 HOUR로 별칭을 설정해두었기 때문에 실행 순서에 따라 OREDER BY 구에서는 HOUR로 사용할 수 있습니다.

# Reference

> [Programmers - SQL 고득점 Kit (입양 시각 구하기(1))](https://programmers.co.kr/learn/courses/30/lessons/59412)<br>
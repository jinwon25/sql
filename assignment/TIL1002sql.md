# SQL Assignment 3주차


## 1. 연습 문제

### 데이터 탐색 - 조건, 추출, 요약 연습 문제(1)
#### 1. 포켓몬 중에 type2가 없는 포켓몬의 수를 작성하는 쿼리를 작성해주세요.
- 조건: type2가 없는
- 어떤 테이블?: pokemon
- 어떤 컬럼: 따로 없음, 포켓몬의 수만 남기면 됨
- 어떻게 집계: 포켓몬의 수 => COUNT

```js
SELECT
  COUNT (id) AS cnt
FROM basic.pokemon
WHERE
  type2 IS NULL
```

#### 2. type2가 없는 포켓몬의 type1과 type1의 포켓몬 수를 알려주는 쿼리를 작성해주세요. 단, type1의 포켓몬 수가 큰 순으로 정렬해주세요.
- 테이블: pokemon
- 조건: type2가 없는 포켓몬
- 컬럼: type1
- 집계: 포켓몬 수 => COUNT
- 정렬: type1의 포켓몬 수가 큰 순으로 정렬 => ORDER BY 큰 순으로 : 큰 것부터 작은 것으로 => 내림차순(DESC) => ORDER BY 포켓몬 수 DESC

```js
SELECT
  type1,
  COUNT(id) AS pokemon_cnt
FROM basic.pokemon
WHERE
  type2 IS NULL
GROUP BY
  type1
ORDER BY
  pokemon_cnt DESC
```

#### 3. type2 상관없이 type1의 포켓몬 수를 알 수 있는 쿼리를 작성해주세요.
- 테이블: pokemon
- 조건: type2 상관없이 => 조건인가? 아닌가? => 조건이 아님
- 컬럼: type1
- 집계: 포켓몬 수 => COUNT

```js
SELECT
  type1,
  COUNT(id) AS pokemon_cnt
FROM basic.pokemon
GROUP BY
  type1
```
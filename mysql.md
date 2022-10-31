<details>
  <summary>2022-10-26</summary>
<pre>

![있었는데 없음](https://user-images.githubusercontent.com/105253684/197935829-6f25114c-3df8-470a-9f30-ee2dbca9f78d.png)

* 보호 시작일보다 입양일이 더 빠른 동물을 찾기 위해 보호 시작일에서 입양일을 빼 0보다 큰 값 찾기
* 보호시작일이 빠른 순으로 조회하기

```mysql 
SELECT O.ANIMAL_ID, O.NAME FROM ANIMAL_OUTS O
INNER JOIN ANIMAL_INS I
ON O.ANIMAL_ID = I.ANIMAL_ID
WHERE I.DATETIME - O.DATETIME > 0
ORDER BY I.DATETIME;
```
---
![없어진 기록](https://user-images.githubusercontent.com/105253684/197937689-6a061149-d6ca-4943-87da-8e2306a00cc4.png)

* 왼쪽에 ANIMAL_OUTS 를 두고 LEFT JOIN 을 사용하여, ANIMAL_INS 의 키가 NULL 인 데이터를 찾으면, ANIMAL_OUTS 에만 존재하는 데이터를 찾을 수 있습니다.

```mysql 
SELECT O.ANIMAL_ID, O.NAME FROM ANIMAL_OUTS O
LEFT JOIN ANIMAL_INS I
ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE I.ANIMAL_ID IS NULL;
```
---
![헤비유저](https://user-images.githubusercontent.com/105253684/197938120-e3988054-963e-4f77-9543-a631cffc5531.png)

* IN절을 사용해 공간을 둘 이상 등록한 사람의 HOST_ID를 구하여 SELECT하고 아이디 순으로 조회합니다.

```mysql 
SELECT *
FROM PLACES
WHERE HOST_ID IN (
    SELECT HOST_ID 
    FROM PLACES 
    GROUP BY HOST_ID 
    HAVING COUNT(HOST_ID) > 1
)
ORDER BY ID;
```
---
![보호소에서 중성화한 동물](https://user-images.githubusercontent.com/105253684/197939104-275dd08a-8b6f-47d6-a479-ed27b7e34bab.png)

* ANIMAL_ID가 같은 동물 INNER JOIN 후 보호소에서 중성화를 거쳤다면 보호소에 들어왔을 때와 입양을 보낸 동물의 성별 및 중성화 여부가 다를 것입니다.

```mysql 
SELECT I.ANIMAL_ID, I.ANIMAL_TYPE, I.NAME FROM ANIMAL_INS I
INNER JOIN ANIMAL_OUTS O
ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE I.SEX_UPON_INTAKE != O.SEX_UPON_OUTCOME
ORDER BY ANIMAL_ID;
```
</pre>
</details>

<details>
  <summary>2022-10-27</summary>
<pre>

![중복 제거](https://user-images.githubusercontent.com/105253684/198181100-70df53ab-ff85-4992-93b2-902ef3a94be3.png)

* (DISTINCT NAME)으로 NAME에 있는 중복 값을 제거 후 COUNT합니다.

```mysql 
SELECT COUNT(DISTINCT NAME) COUNT FROM ANIMAL_INS;
```
---
![동물 수 구하기](https://user-images.githubusercontent.com/105253684/198181625-c4f5c8d1-7bcb-41a5-ad59-73315fcc2cd5.png)

* COUNT(*)로 ANIMAL_INS 테이블의 모든 로우를 COUNT합니다.

```mysql 
SELECT COUNT(*) COUNT FROM ANIMAL_INS;
```
---
![최솟값 구하기](https://user-images.githubusercontent.com/105253684/198181841-eb6e51db-f48b-4dbf-8bc7-7ea486f83679.png)

* MIN(DATETIME)으로 보호 시작일의 최솟값을 조회합니다.

```mysql
SELECT MIN(DATETIME) DATETIME FROM ANIMAL_INS;
```
---
![이름에 el 들어가는 동물 찾기](https://user-images.githubusercontent.com/105253684/198182068-a5026641-7a32-497b-bd89-992d4b32cb4e.png)

* LIKE '%el%' AND ANIMAL_TYPE = 'Dog'로 이름 사이에 EL이 들어가는 개를 조회 후 NAME 오름차순 정렬합니다.

```mysql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE NAME LIKE '%el%' AND ANIMAL_TYPE = 'Dog' ORDER BY NAME;
```
---
![동명 동물 수 찾기](https://user-images.githubusercontent.com/105253684/198190899-43960d68-cac0-4e75-a501-3f974bc73015.png)

* GROUP BY로 NAME끼리 묶은 후 HAVING으로 COUNT(NAME)이 두 개 이상인 것만 조회 후 NAME 오름차순 정렬합니다.

```mysql
SELECT NAME, COUNT(NAME) COUNT
FROM ANIMAL_INS 
GROUP BY NAME 
HAVING COUNT(NAME) > 1 
ORDER BY NAME;
```
</pre>
</details>


<details>
  <summary>2022-10-28</summary>
<pre>

![NULL 처리하기](https://user-images.githubusercontent.com/105253684/198502250-5147a992-3094-496e-9d35-dd19ee2b60b7.png)

* COALEASCE(컬럼명, NULL 대체 할 값)을 사용하여 NULL값엔 No name을 넣어줍니다.

```mysql
SELECT ANIMAL_TYPE, COALESCE(NAME, 'No name') as NAME, SEX_UPON_INTAKE FROM ANIMAL_INS;
```
---
![DATETIME에서 DATE로 형 변환](https://user-images.githubusercontent.com/105253684/198502235-d167ac8b-c690-4e84-8a35-7f53d512ecbd.png)

* DATE_FORMAT을 활용해 DATETIME의 연-월-일 만 출력합니다.
* ORDER BY ANIMAL_ID로 결과는 아이디 순으로 조회 합니다.

```mysql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID;
```
---
![고양이와 개는 몇 마리 있을까](https://user-images.githubusercontent.com/105253684/198502257-2050b3d8-ea29-471c-8c78-49851861e0b3.png)

* COUNT(ANIMAL_TYPE)으로 GROUP BY로 묶어둔 개와 고양이가 각각 몇 마리인지 조회합니다.
* 고양이를 개보다 먼저 조회하기 위해(CAT, DOG) ANIMAL_TYPE의 오름차순으로 정렬합니다.
```mysql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) 
FROM ANIMAL_INS 
GROUP BY ANIMAL_TYPE 
ORDER BY ANIMAL_TYPE;
```
---
![중성화 여부 파악하기](https://user-images.githubusercontent.com/105253684/198502288-c0fee014-4e80-4b9e-a90c-c26ebe0450be.png)

* 중성화된 동물은 SEX_UPON_INTAKE컬럼에 Neutered 또는 Spayed라는 단어가 들어갑니다.
* IF문을 사용해 성별 및 중성화 여부에 Neutered, Spayed가 들어간다면 O 그렇지 않다면 X를 출력합니다.
* 아이디 순으로 조회합니다. 
```mysql
SELECT ANIMAL_ID, NAME, 
IF((SEX_UPON_INTAKE LIKE "Neutered%") OR (SEX_UPON_INTAKE LIKE "Spayed%"), "O", "X") "중성화" 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID;
```
---
![입양 시각 구하기(1)](https://user-images.githubusercontent.com/105253684/198502261-b9a832f4-2e1b-4bf3-a30b-c892db44121c.png)

* HOUR(DATETIME)으로 DATETIME의 시간만 뽑은 후 GROUP BY로 묶어줍니다.
* GROUP BY로 묶은 시간에 해당하는 로우를 COUNT합니다.
* GROUP BY로 묶은 시간에 조건을 주기 위해 HAVING을 사용하여 9시부터 20시 전 까지의 기록들만 출력합니다.
* 결과는 시간대 순으로 정렬합니다. (ORDER BY HOUR)
```mysql
SELECT HOUR(DATETIME) HOUR, COUNT(DATETIME) COUNT
FROM ANIMAL_OUTS
GROUP BY HOUR(DATETIME)
HAVING HOUR >= 9 and HOUR < 20
ORDER BY HOUR
```

</pre>
</details>


<details>
  <summary>2022-10-31</summary>
<pre>

![오랜 기간 보호한 동물(1)](https://user-images.githubusercontent.com/105253684/198912380-4d6c0f7f-175e-4792-8d02-5686a1ec8939.png)

* ANIMAL_INS를 기준으로 ANIMAL_OUTS를 LEFT JOIN 해줍니다.
* 그 중 ANIMAL_OUTS의 입양일이 NULL인 로우만 뽑아 아직 입양을 못 간 동물만 뽑습니다.
* ANIMAL_INS의 보호시작일을 기준으로 오름차순 정렬 후 상위 3개의 로우(LIMIT 3)만 출력합니다.

```mysql
SELECT A.NAME,A.DATETIME
FROM ANIMAL_INS A
LEFT JOIN ANIMAL_OUTS B
ON A.ANIMAL_ID=B.ANIMAL_ID
WHERE B.DATETIME IS NULL
ORDER BY A.DATETIME
LIMIT 3;
```
---
![오랜 기간 보호한 동물(2)](https://user-images.githubusercontent.com/105253684/198912384-0d0af134-c213-4c9f-8fbe-3f315d1489a2.png)

* ANIMAL_OUTS 테이블의 ANIMAL_ID는 ANIMAL_INS의 ANIMAL_ID의 외래 키입니다.
* ANIMAL_INS와 ANIMAL_OUTS를 ANIMAL_ID를 기준으로 INNER JOIN 해줍니다.
* ANIMAL_INS의 보호 시작일에서 ANIMAL_OUTS의 입양일을 빼면 보호 기간입니다.
* 보호 기간을 기준으로 오름차순 정렬 후 상위 2개 로우를 출력합니다.

```mysql
SELECT O.ANIMAL_ID, O.NAME FROM ANIMAL_OUTS O
INNER JOIN ANIMAL_INS I
ON I.ANIMAL_ID = O.ANIMAL_ID
ORDER BY I.DATETIME-O.DATETIME
LIMIT 2;
```
---
</pre>
</details>


<details>
  <summary>2022-11-01</summary>
<pre>

</pre>
</details>


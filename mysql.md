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

* COALEASCE(컬럼이름, NULL 대체 할 값)을 사용하여 NULL값엔 No name을 넣어줍니다.

```mysql
SELECT ANIMAL_TYPE, COALESCE(NAME, 'No name') as NAME, SEX_UPON_INTAKE FROM ANIMAL_INS;
```
---

</pre>
</details>


<details>
  <summary>2022-10-29</summary>
<pre>

</pre>
</details>


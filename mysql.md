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
![가격이 제일 비싼 식품의 정보 출력하기](https://user-images.githubusercontent.com/105253684/198912386-7bba9737-758e-4178-bacb-c9f926c68b8b.png)

* FOOD_PRODUCT의 가장 비싼 식품 가격을 서브쿼리로 찾아줍니다.(SELECT MAX(PRICE) FROM FOOD_PRODUCT)
* 가장 비싼 식품 가격을 가진 로우를 출력합니다.

```mysql
SELECT * FROM FOOD_PRODUCT
WHERE PRICE = (SELECT MAX(PRICE) FROM FOOD_PRODUCT)
```
---
![루시와 엘라 찾기](https://user-images.githubusercontent.com/105253684/198912387-370cee1a-c034-49ac-bf23-b6b81ce4635c.png)

* IN절을 사용해 NAME이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 로우만 출력합니다.

```mysql
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE FROM ANIMAL_INS
WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty');
```
---
![카테고리 별 상품 개수 구하기](https://user-images.githubusercontent.com/105253684/198915432-3c6c28df-c30f-4019-ae4a-6462ac0848cb.png)

* SUBSTR(컬럼명, 시작 위치값, 가져올 길이값 )을 사용하여
 RODUCT_CODE의 첫 번째 문자부터 2개의 문자를 뽑아 낸 후 CATEGORY로 지정합니다.
* GROUP BY CATEGORY로 카테고리별로 묶어줍니다.
* COUNT(PRODUCT_ID)로 GROUP BY로 묶인 로우를 COUNT해줍니다.
* CATEGORY 오름차순으로 정렬합니다.

```mysql
SELECT SUBSTR(PRODUCT_CODE, 1, 2) CATEGORY, COUNT(PRODUCT_ID) PRODUCTS
FROM PRODUCT 
GROUP BY CATEGORY
ORDER BY CATEGORY;
```

</pre>
</details>


<details>
  <summary>2022-11-01</summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/199138973-9e695022-acb8-4b7c-a7bb-169027adcf16.png)

* PRODUCT테이블과 OFFLINE_SALE테이블을 PRODUCT_ID로 INNER JOIN 해줍니다.
* PRODUCT_CODE끼리 GROUP BY로 묶어줍니다.
* SUM(판매가 * 판매량)으로 상품코드 별 매출액 합계를 구합니다.
* 매출액(SALES)를 기준으로 내림차순 후 같다면 상품코드 기준 오름차순 정렬해줍니다.

```mysql
SELECT P.PRODUCT_CODE, SUM(P.PRICE*O.SALES_AMOUNT) SALES 
FROM PRODUCT P
INNER JOIN OFFLINE_SALE O
ON P.PRODUCT_ID = O.PRODUCT_ID
GROUP BY P.PRODUCT_CODE
ORDER BY SALES DESC, P.PRODUCT_CODE;
```
---
![image](https://user-images.githubusercontent.com/105253684/199139855-166b66e2-3af4-4ffa-b1d4-899201b35bdd.png)

* GROUP BY로 진료과 코드 별로 묶어줍니다.
* COUNT(진료예약일시)로 월별예약건수를 구해준 후 5월예약건수라는 별칭을 붙입니다.
* LIKE '2022-05%'를 사용해 월별예약건수 중 2022년 5월에 해당하는 데이터를 뽑아줍니다.
* 5월예약건수를 기준 오름차순 정렬 후 같다면, 진료과 코드 기준 오름차순 정렬합니다.

```mysql
SELECT MCDP_CD 진료과코드, COUNT(APNT_YMD) 5월예약건수 
FROM APPOINTMENT
WHERE APNT_YMD LIKE '2022-05%'
GROUP BY MCDP_CD
ORDER BY 5월예약건수, MCDP_CD
```
---
![image](https://user-images.githubusercontent.com/105253684/199140969-91edd614-fd8b-43ae-a79a-62e11cdcdb58.png)

* DATE_OF_BIRTH 컬럼이 출력하면 DATETIME형식이기 때문에 DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d')으로 'YYYY-mm-dd'형식으로 바꿔줍니다.
* 생일이 3월인 데이터를 뽑기위해 MONTH(DATE_OF_BIRTH) = 3 으로 생일의 월만 뽑아 3인 데이터를 뽑아줍니다.
* 여성회원은 GENDER가 'W'입니다. 조건식에 AND로 추가해줍니다.
* 전화번호가 NULL인경우를 제외하기 위해 TLNO IS NOT NULL을 추가합니다.
* MEMBER_ID를 기준 오름차순 정렬합니다.


```mysql
SELECT MEMBER_ID, MEMBER_NAME, GENDER, DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH) = 3 
AND GENDER = 'W'
AND TLNO IS NOT NULL
ORDER BY MEMBER_ID;
```
---
![image](https://user-images.githubusercontent.com/105253684/199141802-f16cc9ac-7ff5-4cf1-940a-6e35eb4a14e4.png)

* ICECREAM_INFO테이블과 FIRST_HALF테이블을 아이스크림 맛으로 INNER JOIN 해줍니다.
* GROUP BY로 INGREDIENT_TYPE별로 묶어줍니다.
* SUM(TOTAL_ORDER)로 아이스크림 총주문량을 성분 타입별로 더해준 후 TOTAL_ORDER라는 별칭을 붙여줍니다.
* TOTAL_ORDER를 기준 오름차순 정렬하면 총주문량이 작은 순서대로 조회할 수 있습니다.

```mysql
SELECT I.INGREDIENT_TYPE, SUM(TOTAL_ORDER) TOTAL_ORDER  
FROM ICECREAM_INFO I
INNER JOIN FIRST_HALF F
ON I.FLAVOR = F.FLAVOR
GROUP BY INGREDIENT_TYPE
ORDER BY TOTAL_ORDER
```
---
![image](https://user-images.githubusercontent.com/105253684/199142592-886addd6-a6f0-4481-a768-122a0cc6776d.png)

* 먼저 조건식에서 서브쿼리로 음식 종류 별 즐겨찾기가 가장 많은 식당의 음식 종류와 즐겨찾기수를 구해줍니다.
* IN절을 사용해 서브쿼리 내용에 해당하는 데이터가 들어간 식당의 음식 종류, ID, 식당 이름, 즐겨찾기수를 조회합니다.
* 음식 종류를 기준으로 내림차순 정렬해줍니다.

```mysql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES FROM REST_INFO
WHERE (FOOD_TYPE, FAVORITES)
IN (SELECT FOOD_TYPE, MAX(FAVORITES) FROM REST_INFO GROUP BY FOOD_TYPE)
ORDER BY FOOD_TYPE DESC;
```

</pre>
</details>


<details>
  <summary>2022-11-02</summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/199369525-7679692b-fc3e-4a3f-bccf-b7067638759f.png)

* DATE_FORMAT을 활용해 DATETIME형식으로 출력되는 OUT_DATE를 '%Y-%m-%d'형식으로 바꾸고, 별칭을 붙여줍니다.
* 2중 IF문을 활용해 OUT_DATE가 2022-05-01이하라면 '출고완료', 나머지 데이터 중 OUT_DATE가 NULL이면, '출고미정'
* NULL이 아니면 '출고대기'를 OUT_DATE에 넣어줍니다.
* ORDER_ID를 기준 오름차순 정렬해줍니다.

```mysql
SELECT ORDER_ID, PRODUCT_ID, DATE_FORMAT(OUT_DATE, '%Y-%m-%d') OUT_DATE, 
IF(OUT_DATE <= '2022-05-01', '출고완료', IF(OUT_DATE IS NULL, '출고미정', '출고대기')) 출고여부
FROM FOOD_ORDER
ORDER BY ORDER_ID;
```
---
![image](https://user-images.githubusercontent.com/105253684/199370578-d03ed1ea-1fdc-4826-a2cc-b80f3cc52f2d.png)

* TRUNCATE(숫자, 버림 할 자리수)을 활용해 PRICE의 1000의 자리부터 버려줍니다.
* PRICE_GROUP 별칭을 지정해주고 GROUP BY로 묶어줍니다.
* COUNT(*)로 묶인 PRICE_GROUP별로 COUNT 해줍니다.

```mysql
SELECT TRUNCATE(PRICE, -4) PRICE_GROUP, COUNT(*) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```
---
![image](https://user-images.githubusercontent.com/105253684/199371654-1a1b9f66-d209-4152-a067-b28a4177cd81.png)

* GROUP BY로 회원ID와 상품 ID를 기준으로 묶어줍니다.
* GROUP BY로 묶여있으므로 HAVING을 활용해 COUNT(*)이 2이상인 데이터만 출력합니다.
* (동일한 상품을 동일한 회원이 재구매 )
* USER_ID를 기준 오름차순, PRODUCT_ID를 기준 내림차순 정렬합니다.

```mysql
SELECT USER_ID, PRODUCT_ID FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(*) >= 2
ORDER BY USER_ID, PRODUCT_ID DESC
```
---
![image](https://user-images.githubusercontent.com/105253684/199373071-3964f2ce-a84c-438f-9ad6-f35fa78f364e.png)

* FOOD_PRODUCT테이블과 FOOD_ORDER테이블을 PRODUCT_ID를 기준으로 INNER JOIN해줍니다.
* GROUP BY로 PRODUCT_ID별로 묶어줍니다.
* SUM(FOOD_PRODUCT의 PRICE * FOOD_ORDER의 AMOUNT)는 식품의 총매출을 구할 수 있습니다.
* TOTAL_SALES 별칭을 붙여줍니다.
* 2022년 5월 데이터만 출력하기 위해 YEAR(PRODUCE_DATE)가 2022, MONTH(PRODUCE_DATE)가
* 5인 데이터만 출력합니다.
* TOTAL_SALES기준 내림차순, PRODUCT_ID를 기준 오름차순 정렬해줍니다.

```mysql
SELECT P.PRODUCT_ID, P.PRODUCT_NAME, SUM(P.PRICE*O.AMOUNT) TOTAL_SALES 
FROM FOOD_PRODUCT P
INNER JOIN FOOD_ORDER O
ON P.PRODUCT_ID = O.PRODUCT_ID
WHERE YEAR(PRODUCE_DATE) = 2022 AND  MONTH(PRODUCE_DATE) = 5
GROUP BY PRODUCT_ID
ORDER BY TOTAL_SALES DESC, PRODUCT_ID
```
---
![image](https://user-images.githubusercontent.com/105253684/199375426-4ba53fd6-bf88-40d7-8f20-c1706ec5950e.png)

* GROUP BY로 CART_ID별로 묶어줍니다.
* NAME에 'Milk'또는 'Yogurt'가 들어간 데이터만 출력합니다.
* HAVING COUNT(DISTINCT NAME) = 2로 중복을 제거한 NAME을 COUNT했을 때 2인 데이터
* (MILK와 YOGURT가 둘 다 있는 데이터)만 출력합니다.

```mysql
SELECT CART_ID
FROM CART_PRODUCTS
WHERE NAME IN ('Milk','Yogurt')
GROUP BY CART_ID
HAVING COUNT(DISTINCT NAME) = 2
```
</pre>
</details>
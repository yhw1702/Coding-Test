* 2022-10-26

*** 있었는데요 없었습니다

![있었는데 없음](https://user-images.githubusercontent.com/105253684/197935829-6f25114c-3df8-470a-9f30-ee2dbca9f78d.png)

SELECT O.ANIMAL_ID, O.NAME FROM ANIMAL_OUTS O
INNER JOIN ANIMAL_INS I
ON O.ANIMAL_ID = I.ANIMAL_ID
# 보호 시작일보다 입양일이 더 빠른 동물을 찾기 위해 보호 시작일에서 입양일을 빼 0보다 큰 값 찾기
WHERE I.DATETIME - O.DATETIME > 0
# 보호시작일이 빠른 순으로 조회하기
ORDER BY I.DATETIME;
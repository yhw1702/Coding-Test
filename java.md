<details>
  <summary> 0 Lv (1)</summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/202631497-7b2018d2-54a8-4b13-8440-f51938c412cc.png)

* 반복문을 통해 n이 배열[i]와 같으면 answer의 값을 1씩 더해줍니다.

```java
 class Solution {
    public int solution(int[] array, int n) {
        int answer = 0;
        for(int i = 0 ; i < array.length ; i++){
            if(n == array[i]){
                answer++;   
            }
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202631851-fe58d63a-be64-4ceb-9e5e-85214478ae15.png)

* for 반복문을 array.length만큼 돌려 height이 array[i]보다 큰 경우에 answer값을 1씩 더해줍니다.

```java
class Solution {
    public int solution(int[] array, int height) {
        int answer = 0;
        for(int i = 0; i < array.length; i++){
            if(array[i] > height){
                answer++;
            }
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202632281-a400a6a4-347b-47d4-a165-1657e5a42ab5.png)

* num1을 num2로 나눈 후 1000을 곱해 double타입으로 형변환하여 answer에 담아줍니다.
* answer를 int로 형변환하여 리턴해줍니다.(정수부분을 return하기 위해)

```java
class Solution {
    public int solution(int num1, int num2) {
        double answer = (double)num1/num2 * 1000;
        return (int)answer;
    }
}
```

</pre>
</details>


<details>
  <summary> 0 Lv (2)</summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/202952715-ffd7e465-8dfa-4a29-bdd9-5690aa386cee.png)

* answer배열을 numbers배열의 길이만큼 선언해줍니다.
* for 반복문을 돌려 answer에 numbers배열 두배값을 반복해서 넣어줍니다. 

```java
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = new int[numbers.length];
        for(int i = 0 ; i < numbers.length ; i++){
            answer[i] = numbers[i] * 2;
        }
        return answer;
    }
}
```
---

</pre>
</details>


<details>
  <summary> 0 Lv (3)</summary>
<pre>


</pre>
</details>
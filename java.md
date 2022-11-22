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
![image](https://user-images.githubusercontent.com/105253684/202953526-6c25fd68-963f-4b95-a417-de1b00f5252a.png)

* answer배열을 num_list배열의 길이만큼 선언해줍니다.
* 반복문을 돌려 num_list의 끝부터 answer배열에 차례로 넣어줍니다.

```java
class Solution {
    public int[] solution(int[] num_list) {
        int[] answer = new int[num_list.length];
        for(int i = num_list.length-1, j = 0 ; i >= 0  ; i--, j++){
            answer[j] = num_list[i];
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202954062-d31a396c-ee7a-45fc-bf35-4ce17a68664b.png)

* String타입 변경을 위해 StringBuffer sb를 생성해줍니다.
* sb.reverse()를 사용해 문자열을 뒤집고 toString으로 변환해 answer에 넣어줍니다.

```java
class Solution {
    public String solution(String my_string) {
        String answer = "";
        StringBuffer sb = new StringBuffer(my_string);
        answer = sb.reverse().toString();
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202954702-820d3caf-8a1f-45d5-a20d-5a30b1cbce18.png)

* String타입 x 변수를 선언, 초기화 해줍니다.
* 반복문을 n번 돌려서 x에 *을 하나씩 추가하고 x를 출력합니다.

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String x = "";
        for(int i = 0 ; i < n ; i++){
            x += "*";
            System.out.println(x);
        }
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202955166-94848ddb-a074-48a0-becc-baa2a2fd4963.png)

* 짝수와 홀수의 갯수를 담을 cnt1, cnt2 변수를 선언해줍니다.
* 반복문을 돌려 num_list[i]가 짝수일 경우(2로 나눈 나머지가 0) cnt1 1씩 증가,
홀수일 경우(else) cnt2 2씩 증가하여 answer배열에 넣어줍니다.

```java
class Solution {
    public int[] solution(int[] num_list) {
        int[] answer = new int[2];
        int cnt1 = 0;
        int cnt2 = 0;
        for(int i = 0; i < num_list.length; i++){
            if(num_list[i] % 2 == 0) cnt1 += 1;
            else cnt2 += 1;
        }
        answer[0] = cnt1;
        answer[1] = cnt2;
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/202960023-aecb5176-c083-4b62-bc01-edf39f7bfe9f.png)

* 반복문으로 my_string을 하나씩 char c에 넣어줍니다.
* answer에 String으로 형변환한 c를 repeat(n)으로 n번 반복하여 넣어줍니다.

```java
class Solution {
    public String solution(String my_string, int n) {
        String answer = "";
        for (int i = 0; i < my_string.length(); i++){
            char c = my_string.charAt(i);
            answer += String.valueOf(c).repeat(n);
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

![image](https://user-images.githubusercontent.com/105253684/203251037-6c3ed7fd-5ab8-47a3-a200-03acf83e8bdb.png)

* replace(기존 문자, 바꿀 문자)메소드를 활용해 letter에 해당하는 문자에 공백을 넣어줍니다.

```java
class Solution {
    public String solution(String my_string, String letter) {
        String answer = "";
        answer = my_string.replace(letter, "");
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
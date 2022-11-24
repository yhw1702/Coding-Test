# Coding Test

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
![image](https://user-images.githubusercontent.com/105253684/203251730-d8d05a27-81f8-471b-84cf-8753cb5a265a.png)

* 양꼬치 10인분당 음료가 무료이므로 음료의 개수 k에서 양꼬치 n인분을 10으로 나눈 값을 빼줍니다.
* n에는 12000을 곱해주고 k에는 2000을 곱해 리턴해줍니다.

```java
class Solution {
    public int solution(int n, int k) {
        k -= n/10;  
        int answer = 12000 * n + 2000 * k;
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203252477-e9462977-b2c3-49e8-a2d6-225873ebbc9e.png)

* 반복문을 i(1)부터 n번까지 돌려 i값이 짝수일 때(i를 2로 나눈 나머지가 0) answer의 값을 i만큼 계속 더해줍니다.

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        for(int i=1;i<=n;i++){
            if(i%2==0){
                answer += i;
            }
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203254921-8ae5ff0c-116a-4009-9ef9-aaa45535bb50.png)

* Arrays의 copyOfRange(배열, 복사시작인덱스, 복사끝인덱스)을 활용해 numbers배열을 원하는 배열로 잘라
복사하여 answer배열에 넣어줍니다.

```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] numbers, int num1, int num2) {
        int[] answer = Arrays.copyOfRange(numbers, num1, num2+1);
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203256079-acefb885-87ba-442c-bacb-a2990e523ea2.png)

* answer 배열 첫번째는 money를 5500으로 나눈 값을 넣고 두번째는 5500으로 나눈 나머지의 값을 넣습니다.

```java
class Solution {
    public int[] solution(int money) {
        int[] answer = {money/5500, money%5500};
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (4)</summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/203675153-69fe8551-50ec-4879-b508-267e2e816137.png)

* age를 String으로 변환해 s에 담습니다.
* split("")으로 문자열을 잘라 arr배열에 넣어줍니다.(23 -> {2,3})
* 반복문을 arr길이만큼 돌려 parseInt로 변환한 arr[i]에 97을 더해 char타입으로 다시 변환하고(아스키코드로 변환) answer에 하나씩 넣어줍니다.
(아스키코드 97=a 98=b ....)

```java
class Solution {
    public String solution(int age) {
        String answer = "";
        String s = String.valueOf(age);
        String[] arr = s.split("");
        for(int i = 0 ; i < arr.length; i++){
            answer += ((char)((Integer.parseInt(arr[i]) + 97)));
        }
        
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203676047-c4520394-1392-4ed2-8856-e83d597ce0a4.png)

* .clone()메소드를 사용해 emergency의 배열을 복사하여 copy에 넣어줍니다.
* Arrays의 sort메소드를 활용해 copy메소드를 오름차순 정렬해줍니다.
* Integer키, 값 map을 선언하고 emergency의 길이를 max변수에 담아줍니다.
* 반복문을 copy배열 길이만큼 돌려 map(키, 값)에 오름차순정렬된 copy배열에 키에는 오름차순 정렬된 emergency의 값, 
값은 max부터 하나씩 빼가며 넣어줍니다.
* 반복문을 돌려 emergency[0]부터 map.get(키)를 사용해 진료순서를 키에 맞는 값으로 하나씩 넣어줍니다.

```java
import java.util.*;
class Solution {
    public int[] solution(int[] emergency) {
        int[] copy = emergency.clone();
        Arrays.sort(copy);
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        int max = emergency.length;

        for(int i = 0 ; i < copy.length ; i++){
            map.put(copy[i], max);
            max--;
        }
        
        for(int i = 0 ; i < emergency.length ; i++){
            emergency[i] = map.get(Integer.valueOf(emergency[i]));
        }
        
        
        return emergency;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203677219-dbb0613d-d204-4839-9cdd-461a72f52a70.png)

* 반복문을 i(1)부터 n까지 돌려 n을 i로 나눈 나머지가 0인 경우에 answer를 1씩 더해줍니다.

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        for(int i = 1 ; i <= n ; i++){
            if(n%i == 0 ){
                answer++;    
            }
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203677636-6bda4e72-c9c2-447a-950a-5bd46885f494.png)

* 남은 체력을 담을 rhp와 공격횟수를 담을 cnt변수를 선언, 초기화합니다.
* 먼저 hp를 5로 나눈 값을 cnt에 넣어줍니다.(공격횟수)
* rhp에 5로 나눈 나머지 값을 넣어줍니다.(공격 후 남은 체력)
* 다시 rhp에 3을 나눈 값을 cnt에 더해주고, 남은 체력에서 남은체력을 3으로 나눈 나머지를 뺀 후 rhp에서 빼줍니다.
* 마지막으로 rhp에 1을 나눈값을 cnt에 더해줍니다.

```java
class Solution {
    public int solution(int hp) {
        
        int rhp = 0;
        int cnt = 0;
        
        cnt = hp / 5;
        rhp = hp % 5;
        cnt += rhp / 3;
        rhp -= rhp-(rhp % 3);
        cnt += rhp / 1;
        return cnt;
    }
}
```

</pre>
</details>
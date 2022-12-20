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

* 짝수와 홀수의 개수를 담을 cnt1, cnt2 변수를 선언해줍니다.
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
(아스키코드 97=a 98=b ...)

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
* Arrays의 sort메소드를 활용해 copy배열을 오름차순 정렬해줍니다.
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
---
![image](https://user-images.githubusercontent.com/105253684/203678615-2e5cd29a-6715-47a2-9251-be491e48bdff.png)

* 문자열 rsp를 split("")메소드로 하나씩 arr 배열에 넣어줍니다.
* 반복문을 arr길이만큼 돌려 arr[i]가 "2"라면 answer에 "0"을, "0"이면 "5", "5"면 "2"를 하나씩 answer에 넣어줍니다.

```java
class Solution {
    public String solution(String rsp) {
        String answer = "";
        String[] arr = rsp.split("");
        for(int i = 0 ; i < arr.length ; i++){
            if(arr[i].equals("2")) answer += "0";
            else if(arr[i].equals("0")) answer += "5";
            else if(arr[i].equals("5")) answer += "2";
        }
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (5) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/203901184-a0fb35e4-9142-403a-ae89-dcbd0b10677d.png)

* dot[0]과 dot[1]을 곱해 양수이면 1, 3 사분면이고, 음수이면 2, 4 사분면입니다.
* 조건문을 활용해 양수를 골라 dot[0]이 양수이면 1사분면이고, 음수이면 3사분면으로 return합니다.
* 그 반대의 경우는 dot[0]이 양수라면 4사분면, 음수라면 2사분면을 return 합니다.

```java
class Solution {
    public int solution(int[] dot) {
        int answer = 0;
        if(dot[0] * dot[1] > 0){
            if(dot[0] > 0){
                answer = 1;
            }else{answer = 3;}
        }else{
            if(dot[0] > 0){
                answer = 4; 
            }else{answer = 2;}
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/203901524-0317a051-9a34-414e-aaa7-fe6f4c82290a.png)

* answer배열을[num_list의 길이/n][n]으로 선언합니다.
* answer배열에 값을 차례로 넣어주기 위해 cnt변수를 선언합니다.
* 2중 반복문을 활용해 num_list의 길이 나누기 n 번을 n번만큼 돌려 answer에 0번인덱스(cnt)부터 돌려 cnt를 1씩 더해줍니다.

```java
class Solution {
    public int[][] solution(int[] num_list, int n) {
        int[][] answer = new int[num_list.length/n][n];
        int cnt = 0;
        for(int i = 0 ; i < num_list.length/n ; i++){
            for(int j = 0 ; j < n ; j++){
                answer[i][j] = num_list[cnt];
                cnt++;
            }
        }
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (6) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/206631785-685fb506-e6dd-4f55-ace8-ec3c976f645a.png)

* 공을 던지고 받은 사람이 아닌 공을 던진사람의 번호를 구해야 하기 때문에 k에 1을 빼줍니다.
* 한 명을 건너뛰므로 * 2 를 해주고 numbers의 길이만큼 나눈 나머지를 구해줍니다.

```java
class Solution {
    public int solution(int[] numbers, int k) {
        int answer = numbers[(k-1) * 2 % numbers.length];
        return answer;
    }
}
```
![image](https://user-images.githubusercontent.com/105253684/206632178-c97358a0-794b-4922-994d-f0e8a1377e89.png)

* direction이 left라면 반복문을 통해 answer배열에 numbers배열을 한칸씩 밀어 넣어주고 마지막엔 numbers 0번 인덱스 값을 넣어줍니다.
* left가 아니라면 반복문으로 answer배열의 뒤부터 numbers 배열 마지막에서 앞의 인덱스의 값을 넣어주고 
answer 배열 0번 인덱스에 numbers마지막 인덱스 값을 넣어줍니다.

```java
class Solution {
    public int[] solution(int[] numbers, String direction) {
        int[] answer = new int[numbers.length];
        if(direction.equals("left")){
            for(int i = 0 ; i < numbers.length-1 ; i++){
                answer[i] = numbers[i+1];
            }
            answer[numbers.length-1] = numbers[0];
        }else{
            for(int i = numbers.length-1 ; i > 0 ; i--){
                answer[i] = numbers[i-1];
            }
            answer[0] = numbers[numbers.length-1];
        }
        return answer;
    }
}
```
![image](https://user-images.githubusercontent.com/105253684/206632638-72459f52-870f-4805-9cee-1f73517e6ca6.png)

* 주사위의 최대 개수를 구하기 위해 가로, 새로, 높이에 각각 n을 나눠준 값을 곱해주면됩니다.

```java
class Solution {
    public int solution(int[] box, int n) {
        int answer = 0;
        answer = (box[0]/n) * (box[1]/n) * (box[2]/n);
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (7) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/206975790-ac34d36f-96ef-43da-9022-8a9b09d39719.png)
* Arrays.sort를 활용해 numbers의 배열을 오름차순 정렬해줍니다.
* numbers배열의 마지막 인덱스의 값과 그 전 인덱스의 값을 곱해줍니다.
```java
import java.util.*;
class Solution {
    public int solution(int[] numbers) {
        int answer = 0;
        Arrays.sort(numbers);
        answer = numbers[numbers.length-1] * numbers[numbers.length-2];
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/206976115-575bbfd6-4934-4310-8907-ecd601171153.png)
* a변수를 선언 후 1로 초기화해줍니다.
* 제한사항의 n은 최대 3,628,800로 10의 팩토리얼이므로 반복문을 i가 1부터 10까지 돌려 a변수에 하나씩 곱해 넣어줍니다.
* a가 n보다 커진다면 i-1을 리턴하고 아니라면 10을 리턴해줍니다.
```java
class Solution {
    public int solution(int n) {
        int answer = 1;
        int a = 1;
        for(int i = 1 ; i <= 10 ; i++){
            a *= i;
            if(a > n) return i-1;
        }
        return 10;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/206976781-8633e5c1-8b8f-4843-ba7f-bef046fdf26c.png)
* 반목분을 i=0부터 my_string의 길이미만으로 돌려 a변수에 my_string.substirng(시작인덱스,끝인덱스)을 이용해 하나씩 담습니다.
* a변수가 모음이 아닌경우만 조건문으로 answer에 더해줍니다.
```java
class Solution {
    public String solution(String my_string) {
        String answer = "";
        for(int i=0; i<my_string.length();i++){
            String a = my_string.substring(i, i+1);
            if(!(a.equals("a") || a.equals("e") || a.equals("i") || a.equals("o") || a.equals("u"))){
                answer += a;
            }
        }
        return answer;
    }
}
```

</pre>
</details>


<details>
  <summary> 0 Lv (8) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/207226723-f9f3f642-0a13-47c5-b4e1-4ff7df6a4c06.png)
* my_string에 글자를 하나하나 s배열에 .split("")메소드를 활용해 넣어줍니다.
* ArrayList<string> l을 선언해줍니다.
* 반복문을 s배열 길이 미만으로 돌려(인덱스) s배열에 포함된 숫자만 l 리스트에 넣어줍니다.
* Collection.sort(l)을 이용해 string 리스트를 오름차순 정렬해줍니다.
* 반복문을 l길이 미만으로 돌려서 answer배열에 Integer.parseInt로 string을 int로 형변환하여 하나씩 넣어줍니다.
```java
import java.util.*;
class Solution {
    public int[] solution(String my_string) {
        List<String> l = new ArrayList<>();
        String[] s = my_string.split("");
        for(int i = 0 ; i < s.length ; i++){
            if(s[i].equals("0") || s[i].equals("1") || s[i].equals("2") || s[i].equals("3") || 
              s[i].equals("4") || s[i].equals("5") || s[i].equals("6") || s[i].equals("7") || 
              s[i].equals("8") || s[i].equals("9")) l.add(s[i]);            
        }
        Collections.sort(l);
        int[] answer = new int[l.size()];
        for(int i = 0 ; i < l.size() ; i++){
            answer[i] = Integer.parseInt(l.get(i));            
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/207227330-120ec77c-37de-4c40-b26d-6b3e172f7a80.png)
* ArrayList<string> l을 선언해줍니다.
* 배열 s에 my_string의 문자를 하나하나 split을 활용하여 넣어줍니다.
* 반복문을 돌려 배열 s에 포함된 숫자만 l 리스트에 하나씩 넣어줍니다.
* 반복문을 l의 길이 미만으로 돌려 l에 들어있는 숫자를 int로 형변환하여 answer에 하나씩 더해줍니다.
```java
import java.util.*;
class Solution {
    public int solution(String my_string) {
        int answer = 0;
        List<String> l = new ArrayList<>();
        String[] s = my_string.split("");
        for(int i = 0 ; i < s.length ; i++){
            if(s[i].equals("0") || s[i].equals("1") || s[i].equals("2") || s[i].equals("3") || 
              s[i].equals("4") || s[i].equals("5") || s[i].equals("6") || s[i].equals("7") || 
              s[i].equals("8") || s[i].equals("9")) l.add(s[i]);            
        }
        for(int i = 0 ; i < l.size() ; i++){
            answer += Integer.parseInt(l.get(i));
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/207227915-78ef2301-9562-439c-97d5-1fb50939bbf4.png)
* 문자열 s를 .split(" ")을 활용해 공백으로 구분하여 하나씩 String 배열 srr에 넣어줍니다.
* 반복문을 i = 0 부터 srr길이 미만으로 돌려 srr[i]가 Z가 아니라면 answer에 srr[i]를 int로 형변환하여 계속 더해주고
Z 라면 그 전 인덱스인 srr[i-1]를 answer에서 빼줍니다.
```java
class Solution {
    public int solution(String s) {
        int answer = 0;
        String[] srr = s.split(" ");
        for(int i = 0 ; i < srr.length ; i++){
            if(!srr[i].equals("Z")) answer += Integer.parseInt(srr[i]);
            else answer -= Integer.parseInt(srr[i-1]);
        }
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (9) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/207514241-accbcf7c-9847-4da7-9c3c-4db44db784ee.png)
* answer배열의 크기를 strlist의 길이만큼 선언해줍니다.
* 반복문을 strlist배열의 길이 미만으로 돌려 answer배열에 strlist[i]의 길이를 하나씩 넣어줍니다.
```java
class Solution {
    public int[] solution(String[] strlist) {
        int[] answer = new int[strlist.length];
        for(int i = 0 ; i < strlist.length ; i++){
            answer[i] = strlist[i].length();
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/207514555-93ed4d0f-8c7e-4ab0-a5c7-d1761092006c.png)
* x변수에 배열 첫 번째 x좌표를 넣어줍니다.
* y변수에 배열 첫 번째 y좌료를 넣어줍니다.
* 가로와 세로의 길이를 담을 변수를 선언, 초기화해줍니다.
* 반복문을 dots배열 행의 길이만큼 돌리고 조건문으로 x가 다른 좌표의 x값과 다르면 Math.abs()를 활용해
 x변수의 다른 x좌표를 빼준 값의 절대값을 구해줍니다(가로).
* 마찬가지로 y의 절대값을 구해줍니다.(높이)
* 가로와 세로를 곱해줍니다.
```java
class Solution {
    public int solution(int[][] dots) {
        int x = dots[0][0];
        int y = dots[0][1];
        int width = 0;
        int height = 0;
        for(int i = 0 ; i < dots.length ; i++){
            if(x != dots[i][0]){
                width = Math.abs(x - dots[i][0]);
            }
            if(y != dots[i][1]){
                height = Math.abs(y - dots[i][1]);
            }
        }
        return width * height;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/207515561-73920cbf-d23b-41d7-b127-6a06b9102bc5.png)
* x 변수에 board[0](맵의 가로 크기)를 2로 나눈 값(0, 0 기준 현재 맵의 가로 최대, 최소길이)을 넣어줍니다.
* y 변수에 맵의 새로 크기를 2로 나눈 값(0, 0 기준 현재 맵의 세로 최대, 최소길이)을 넣어줍니다.
* 반복문을 keyinput배열 길이미만으로 돌려 keyinput[i]가 left 라면 answer[0](캐릭터의 현재 x좌표)가 -x와 같지 않을 때만 -1을 해줍니다.
* right는 캐릭터의 현재 x좌표가 x와 같지 않을 때만 +1을 해줍니다.
* up과 down은 각각 y, -y 와 같지 않을 때만 answer[1](케릭터의 현재 y좌표)에 +1, -1을 해줍니다.
```java
class Solution {
    public int[] solution(String[] keyinput, int[] board) {
        int[] answer = {0, 0};
        int x = board[0]/2;
        int y = board[1]/2;
        for(int i = 0 ; i < keyinput.length ; i++){
            if(keyinput[i].equals("left")){
                if(answer[0] != -x) answer[0] -= 1;
            }
            if(keyinput[i].equals("right")){
                if(answer[0] != x) answer[0] += 1;
            }
            if(keyinput[i].equals("up")){
                if(answer[1] != y) answer[1] += 1;
            }
            if(keyinput[i].equals("down")){
                if(answer[1] != -y) answer[1] -= 1;
            }
        }
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (10) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/207783222-35e32229-7f8f-4207-ba90-5da4531f0513.png)
* Arrays.sort로 numbers배열을 오름차순 정렬해 줍니다.
* 변수 x에는 가장 작은 수 두 개의 곱을 넣어주고 y에는 가장 큰 수 두 개의 곱을 넣어줍니다.
* Math.max(비교할 수1, 비교할 수2)를 사용해 둘중 큰 수를  answer에 넣어줍니다.
```java
import java.util.Arrays;
class Solution {
    public int solution(int[] numbers) {
        int answer = 0;
        Arrays.sort(numbers);
        int x = numbers[0] * numbers[1];
        int y = numbers[numbers.length-1] * numbers[numbers.length-2];
        answer = Math.max(x, y);
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/207784088-81e841af-ade1-4827-8908-8fc4e423e65d.png)
* 정수 x와 n변수를 선언, 초기화 해줍니다.
* String배열 srr에 문자열 polynomial " + "를 기준으로 잘라 넣어줍니다.
* 반복문을 돌려 srr[i]가 x를 포함하고 길이가 1이라면(x) 1을, 아니라면 srr[i]에 x를 뺀 값을 정수형으로 변환하여 x에 더해줍니다.
* x를 포함하지 않는다면(정수) n에 srr[i]를 형변환하여 더해줍니다.
* ?연산자를 활용해 answer에 x가 0이면 공백, 0이면 x, 0보다 크면 x + "x" 그리고 정수자리에는 x가 0이면 n x와 n이 0이면 공백,
x가 0이 아니면 앞에 "+" + n을 해줍니다.

```java
class Solution {
    public String solution(String polynomial) {
        String answer = "";
        int x = 0;
        int n = 0;
        String[] srr = polynomial.split(" \\+ ");
        for(int i = 0 ; i < srr.length ; i++){
            if(srr[i].contains("x")){
                x += srr[i].length() == 1 ? 1 : Integer.parseInt(srr[i].replace("x",""));
            }else n += Integer.parseInt(srr[i]);
        }
        return (x != 0 ? x > 1 ? x + "x" : "x" : "") + (n != 0 ? (x != 0 ? " + " : "") + n : x == 0 ? "0" : "");
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/208594971-0f686af8-fda7-4661-81f9-2289ccec373a.png)
* String배열 srr에 my_string에서 replaceAll(변환하고싶은 값, 변환할 값)으로 정규식을 이용해 a~z,A~Z를 공백으로 변환합니다.
* 반복문을 돌려 srr[i]가 공백이 아닌 경우(숫자) int로 형변환하여 answer에 하나씩 더해줍니다.
```java
class Solution {
    public int solution(String my_string) {
        int answer = 0;
        String[] srr = my_string.replaceAll("[a-zA-Z]" , " ").split(" ");
        for(int i = 0 ; i < srr.length ; i++){
            if(!srr[i].equals("")) answer += Integer.valueOf(srr[i]);
        }
        return answer;
    }
}
```


</pre>
</details>


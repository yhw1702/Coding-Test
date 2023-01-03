# Coding Test

<details>
  <summary> 0 Lv(1) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/208013284-95c148be-a808-432e-878e-b4a964200d81.png)
* String배열 srr에 my_string.replaceAll을 사용해 a~z,A~Z를 공백으로 바꿔 공백을 기준으로 하나씩 담아줍니다.
* 반복문을 사용해 srr[i]가 ""이 아닌경우(숫자인 경우) answer에 srr[i]를 형변환하여 하나씩 더해줍니다.
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
---
![image](https://user-images.githubusercontent.com/105253684/208825408-2734b951-c207-4c16-8c8e-2229b4d92037.png)
* 반복문을 dic길이만큼 돌리고 cnt변수를 선언, 초기화해줍니다.
* 중첩으로 반복문을 돌려 dic[i]에 spell[j]가 포함되어있다면 cnt를 1증가(같은 단어 개수)하고 
cnt가 spell의 길이와 같다면(같은 단어 개수와 spell의 길이) 1을 리턴해줍니다.
* 아니라면 2를 리턴합니다.
```java
class Solution {
    public int solution(String[] spell, String[] dic) {
        for(int i =0; i<dic.length; i++){
            int cnt =0;
            for(int j=0; j<spell.length; j++){
                if(dic[i].contains(spell[j])) cnt++;
                if(cnt==spell.length) return 1;
            }
        }
        return 2;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/209298288-aa8b822e-e615-42ed-9612-9405f41e3a7a.png)
* a와 b중 작은 수를 min에 넣어줍니다.
* 최대공약수를 담을 gcd변수를 선언 초기화합니다.
* 반복문을 i = 1부터 min까지 돌려 a와 b가 모두 나누어 떨어지는 수를 gcd에 담아줍니다.
* 분모를 최대공약수에 나누어 num변수에 넣어줍니다.
* while 반복문을 num != 1인 동안 돌려 num이 2로 나누어 떨어지면 2로 나눠주고 5로 나누어 떨어지면 5로 나눠주고, 나눠지지 않는다면(무한소수) 2를 리턴합니다.
* num이 1이된다면 반복문이 종료되고(유한소수) 1을 리턴합니다.
```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        int min = Math.min(a, b);
        int gcd = 0;
        for(int i=1; i<= min; i++){
            if( a % i == 0 && b % i ==0) gcd = i;
        }
        int num = b/gcd;
        while(num!=1){
            if(num % 2 == 0) num /= 2;
            else if (num % 5 ==0) num /= 5;
            else return 2;
        }
        return 1;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/209906746-b84a312d-df8c-49aa-8de7-f63d17c36b14.png)
* float배열(평균점수) arr, arr2를 score.length만큼 선언해줍니다.
* <평균, 등수>를 담을 HashMap m 을 선언해줍니다.
* 반복문을 돌려 각 점수의 평균을 arr과 arr2에 담아줍니다.
* arr배열을 오름차순 정렬해줍니다.
* 반복문으로 Map m에(오름차순 정렬된 평균점수, 등수)를 담아줍니다.
* 반복문을 i = 0 부터 score.length만큼 돌려 answer[i]에 m.get(키)를 활용해 arr2배열에 담긴 평균점수를 등수로 바꿔 넣어줍니다.
```java
import java.util.*;
class Solution {
    public int[] solution(int[][] score) {
        int[] answer = new int[score.length];
        float[] arr = new float[score.length];
        float[] arr2 = new float[score.length];
        Map<Float, Integer> m = new HashMap<>();
        for(int i = 0 ; i < score.length ; i++){
            arr[i] = (float)(score[i][0]+score[i][1]) / 2;
            arr2[i] = (float)(score[i][0]+score[i][1]) / 2;
        }
        Arrays.sort(arr);
        for(int i = 0, j = score.length ; i < score.length ; i++){
            m.put(arr[i], j);
            j--;
        }
        for(int i = 0 ; i < score.length ; i++){
            answer[i] = m.get(arr2[i]);
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/209907438-cac33c0a-b572-4168-b97c-c818dfe535c0.png)
* 반복문을 i = 0 부터 db의 길이만큼 돌려 db[i][0](db에 있는 아이디)가 id_pw[1](아이디)와 일치하고, 비밀번호가 일치하지 
않으면 "wrong pw"를 일치하면 "login" 아이디와 비밀번호가 모두 일치하지 않다면 "fail"을 리턴합니다.
```java
class Solution {
    public String solution(String[] id_pw, String[][] db) {
        for(int i = 0 ; i < db.length ; i++){
            if(db[i][0].equals(id_pw[0])){
                if(!db[i][1].equals(id_pw[1])) return "wrong pw";
                else return "login";
            }
        }
        return "fail";
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (2) </summary>
<pre>

![image](https://user-images.githubusercontent.com/105253684/210039269-3fcbba80-1e33-4436-8489-2b1e47f1d8e4.png)
* 변수 x와 y에 Integer.parseInt(2진수(String), 2(int))를 활용해 2진수를 10진수로 바꿔 넣어줍니다.
* answer에 x+y값을 Integer.toBinaryString()을 활용해 10진수(int)를 2진수(String)으로 바꿔 넣어줍니다.
```java
class Solution {
    public String solution(String bin1, String bin2) {
        String answer = "";
        int x = Integer.parseInt(bin1, 2);
        int y = Integer.parseInt(bin2, 2);
        answer = Integer.toBinaryString(x+y);
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/210039677-8684d8e3-9658-4326-b92f-f62d81385797.png)
* String 배열 arr1, arr2에 각각 before와 after를 split("")으로 잘라서 하나씩 넣어줍니다.
* Map1, Map2를 선언해줍니다.
* 반복문을 before의 길이만큼 돌려 map1 키에는 arr1(before)[i] 값에는 1을 넣어주고 키가 존재한다면 값에 +1을 해줍니다.
* after도 같은 방식으로 map2에 담아줍니다.
* map1과 map2가 같다면(map1.equals(map2)) return 1; 아니면 0을 리턴합니다.
```java
import java.util.*;

class Solution {
    public int solution(String before, String after) {
        int answer = 0;
        String[] arr1 = before.split("");
        String[] arr2 = after.split("");
        Map<String, Integer> map1 = new HashMap<>();
        Map<String, Integer> map2 = new HashMap<>();
        for(int i =0; i<before.length(); i++){
            if(!map1.containsKey(arr1[i])) map1.put(arr1[i], 1);
            else map1.put(arr1[i], map1.get(arr1[i]) +1);
            if(!map2.containsKey(arr2[i])) map2.put(arr2[i], 1);
            else map2.put(arr2[i], map2.get(arr2[i]) +1);
        }
        if(map1.equals(map2)) return 1;  
        return 0;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/210039974-78f71a72-0f77-4fef-a877-a04cdf95583f.png)
* 문자열 s에 int i부터 j값을 반복문으로 공백없이 담아줍니다.
* 문자열 s를 split("")으로 하나씩 잘라 srr배열에 담아줍니다.
* 반복문을 x = 0부터 srr길이만큼 돌려 srr[x]에 k를 toString으로 형변환한 값과 같다면 answer++해줍니다.
```java
class Solution {
    public int solution(int i, int j, int k) {
        int answer = 0;
        String s = "";
        for(int x = i ; x <=j ; x++){
            s += x;
        }
        String[] srr = s.split("");
        for(int x = 0 ; x < srr.length ; x++){
            if(srr[x].equals(Integer.toString(k))) answer++;
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/210208327-3fa86049-cdf9-4363-a2b9-e2c98635ab22.png)
* 반복문을 my_string 길이미만으로 돌려 indexOf를 활용해 my_string.charAt(i)의 인덱스 값(앞에서부터 처음 발견되는 인덱스)이 i와 같다면(중복x)
answer에 my_string의 i번째 인덱스 값을 넣어줍니다.
```java
class Solution {
    public String solution(String my_string) {
        String answer = "";
        for(int i = 0 ; i < my_string.length() ; i++){
            if(my_string.indexOf(my_string.charAt(i)) == i) answer += my_string.charAt(i);
        }
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/210208700-0fe2e1b2-9f54-495d-8a3c-59a38c816e07.png)
* 변수 answer에 1을 넣어줍니다.
* 가장 긴 변의 길이가 다른 두 변의 길이의 합보다 작아야 하므로 sides배열을 Arrays.sort로 오름차순 정렬해줍니다.
* if문을 활용해 sides[2](가장 긴 변)가 sides[0]과 sides[1]의 합보다 크거나 같다면 answer에 2를(삼각형x) 넣어줍니다.
```java
import java.util.*;
class Solution {
    public int solution(int[] sides) {
        int answer = 1;
        Arrays.sort(sides);
        if(sides[2] >= sides[0] + sides[1]) answer = 2;
        return answer;
    }
}
```
---
![image](https://user-images.githubusercontent.com/105253684/210333399-4e2f7e06-3886-4348-930d-f0fad224b1d2.png)
* arr배열에서 n을 뺀 절댓값을 담을 min변수를 100으로 초기화합니다.
* arr배열을 오름차순 정렬합니다. 
* 반복문을 돌려 정수배열값 - n의 절댓값(n과 가장 가까운 수)을 abs에 담고 가장 작은값의 배열 값을 answer에 넣어줍니다.
```java
import java.util.*;
class Solution {
    public int solution(int[] arr, int n) {
        int answer = 0;
        int min = 100;
        Arrays.sort(arr);
        for(int i = 0 ; i<arr.length; i++){
            int abs = Math.abs(arr[i] - n);
            if(abs < min){
                min = abs;
                answer = arr[i];
            }
        }
        return answer;
    }
}
```

</pre>
</details>

<details>
  <summary> 0 Lv (3) </summary>
<pre>

</pre>
</details>

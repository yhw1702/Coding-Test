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

</pre>
</details>

<details>
  <summary> 0 Lv (2) </summary>
<pre>

</pre>
</details>

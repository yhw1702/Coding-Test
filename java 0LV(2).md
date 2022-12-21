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
cnt가 spell의 길이와 같다면(같은 단어와 spell의 길이) 1을 리턴해줍니다.
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

</pre>
</details>

<details>
  <summary> 0 Lv (2) </summary>
<pre>

</pre>
</details>

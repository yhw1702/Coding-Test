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


</pre>
</details>

<details>
  <summary> 0 Lv (2) </summary>
<pre>

</pre>
</details>

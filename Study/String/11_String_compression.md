# 문자열 압축

## 설명

알파벳 대문자로 이루어진 문자열을 입력받아 같은 문자가 연속으로 반복되는 경우 반복되는 문자 바로 오른쪽에 반복 횟수를 표기하는 방법으로 문자열을 압축하는 프로그램을 작성하시오.  
단 반복횟수가 1인 경우 생략합니다.

## 입력

첫 줄에 문자열이 주어진다. 문자열의 길이는 100을 넘지 않는다.

## 출력

첫 줄에 압축된 문자열을 출력한다.

## 예시 입력 1

```
KKHSSSSSSSE

```

## 예시 출력 1

```
K2HS7E

```

## 예시 입력 2

```
KSTTTSEEKFKKKDJJGG
```

## 예시 출력 2

```
KST3SE2KFK3DJ2G2
```

## 풀이 (통과)

```java
import java.util.Scanner;

public class Main {
    public String solution(String s) {
        String answer = "" + s.charAt(0);
        s = s + " ";
        int count = 1;

        char[] charArray = s.toCharArray();

        for (int i = 1; i < charArray.length; i++) {
            if (charArray[i] != charArray[i - 1]) {
                if (count != 1) answer += count;
                answer += charArray[i];
                count = 1;
            }
            if (charArray[i] == charArray[i - 1]) count++;
        }

        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        String str = kb.next();

        System.out.println(T.solution(str));
    }
}
```

## 배운점

- **뒤에 공백 붙히기**

인덱스를 가지고 놀 때 필요하다면 뒤에 공백을 붙혀주어도 된다는 사실.
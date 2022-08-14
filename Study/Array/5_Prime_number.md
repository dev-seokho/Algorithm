# 소수(에라토스테네스 체)

## 설명

자연수 N이 입력되면 1부터 N까지의 소수의 개수를 출력하는 프로그램을 작성하세요.  
만약 20이 입력되면 1부터 20까지의 소수는 2, 3, 5, 7, 11, 13, 17, 19로 총 8개입니다.

## 입력

첫 줄에 자연수의 개수 N(2<=N<=200,000)이 주어집니다.

## 출력

첫 줄에 소수의 개수를 출력합니다.

## 예시 입력 1

```
20
```

## 예시 출력 1

```
8
```

## 풀이(시간 초과)

```java
import java.util.Scanner;

public class Main {
    public int solution(int n) {
        int answer = 0;

        for (int i = 2; i <= n; i++) {

            int cnt = 0;
            for (int j = 2; j < i; j++) {
                if (cnt == 1) break;
                if (i % j == 0) cnt++;
            }
            if (cnt == 0) answer++;
        }

        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        int n = kb.nextInt();
        System.out.print(T.solution(n));
    }
}
```

## 풀이(에라토스테네스 체 사용)

```java
import java.util.Scanner;

public class Main {
    public int solution(int n) {
        int answer = 0;

        int[] ch = new int[n + 1];

        for (int i = 2; i <= n; i++) {
            if (ch[i] == 0) {
                answer++;
                for (int j = i; j <= n; j = j + i) ch[j] = 1;
            }
        }

        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        int n = kb.nextInt();
        System.out.print(T.solution(n));
    }
}
```

## 배운점

- 에라토스테네스 체

[https://namu.wiki/w/에라토스테네스의 체](https://namu.wiki/w/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98%20%EC%B2%B4)
# 격자판 최대합

## 설명

5*5 격자판에 아래롸 같이 숫자가 적혀있습니다.

![Grid_max_sum.png](./img/Grid_max_sum/png);

N*N의 격자판이 주어지면 각 행의 합, 각 열의 합, 두 대각선의 합 중 가 장 큰 합을 출력합니다.

## 입력

첫 줄에 자연수 N이 주어진다.(2<=N<=50)  
두 번째 줄부터 N줄에 걸쳐 각 줄에 N개의 자연수가 주어진다. 각 자연수는 100을 넘지 않는다.

## 출력

최대합을 출력합니다.

## 예시 입력 1

```
5
10 13 10 12 15
12 39 30 23 11
11 25 50 53 15
19 27 29 37 27
19 13 30 13 19

```

## 예시 출력 1

```
155
```

## 풀이(통과)

```java
import java.util.Scanner;

public class Main {
    public int solution(int n, int[][] arr) {
        int answer = 0;

        int sumA = 0, sumB = 0;

        for (int i = 0; i < n; i++) {
            int sumC = 0, sumD = 0;

            sumA += arr[i][i];
            sumB += arr[i][n - i - 1];

            for (int j = 0; j < n; j++) {

                sumC += arr[i][j];
                sumD += arr[j][i];
            }

            answer = Math.max(answer, sumC);
            answer = Math.max(answer, sumD);
        }
        answer = Math.max(answer, sumA);
        answer = Math.max(answer, sumB);

        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        int n = kb.nextInt();
        int[][] arr = new int[n][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                arr[i][j] = kb.nextInt();
            }
        }

        System.out.print(T.solution(n, arr));
    }
}
```
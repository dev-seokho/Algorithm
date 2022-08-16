# 등수 구하기

## 설명
 
N명의 학생의 국어점수가 입력되면 각 학생의 등수를 입력된 순서대로 출력하는 프로그램을 작성하세요.  
같은 점수가 입력될 경우 높은 등수로 동일 처리한다.  
즉 가장 높은 점수가 92점인데 92점이 3명 존재하면 1등이 3명이고 그 다음 학생은 4등이 된다.  

## 입력

첫 줄에 N(3<=N<=100)이 입력되고, 두 번째 줄에 국어점수를 의미하는 N개의 정수가 입력된다.

## 출력

입력된 순서대로 등수를 출력한다.

## 예시 입력 1

```
5
87 89 92 100 76

```

## 예시 출력 1

```
4 3 2 1 5
```

## 풀이 (통과)

```java
import java.util.Collections;
import java.util.Scanner;
import java.util.Arrays;

public class Main {
    public int[] solution(int n, Integer[] arr) {
        int[] answer = new int[n];
        Integer[] tmp = arr.clone();
        Arrays.sort(tmp, Collections.reverseOrder());

        for (int i = 0; i < arr.length; i++) {
            answer[i] = Arrays.asList(tmp).indexOf(arr[i]) + 1;
        }

        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        int n = kb.nextInt();
        Integer[] arr = new Integer[n];

        for (int i = 0; i < n; i++) {
            arr[i] = kb.nextInt();
        }

        for (int i : T.solution(n, arr)) {
            System.out.print(i + " ");
        }
    }
}
```

## 다른 풀이 (내장함수를 최대한 사용하지 않고 2중 for문 사용)

```java
import java.util.Scanner;

public class Main {
    public int[] solution(int n, Integer[] arr) {
        int[] answer = new int[n];
        
        for(int i=0; i<n; i++){
            int cnt=1;
            for(int j=0; j<n; j++){
                if(arr[j]>arr[i]) cnt++;
            }
            
            answer[i] = cnt;
        }
        
        return answer;
    }

    public static void main(String[] args) {
        Main T = new Main();
        Scanner kb = new Scanner(System.in);

        int n = kb.nextInt();
        Integer[] arr = new Integer[n];

        for (int i = 0; i < n; i++) {
            arr[i] = kb.nextInt();
        }

        for (int i : T.solution(n, arr)) {
            System.out.print(i + " ");
        }
    }
}
```

## 배운점

- Deep Copy의 사용

clone() 을 사용해서 Deep Copy를 구현해보았다.

- Array의 정렬

`Arrays.sort(tmp, Collections.reverseOrder());` 과 같은 방식으로 정렬을 해야하는데, 주의할 점은 tmp가 기본형 타입인 int[] 가 아니라 tmp가 Wrapper class 인 Integer[] 여야만 동작한다는 것이다. 

- java.util.Arrays를 사용하면서 느낀점

기본형 타입 `int[]` 를 매개변수로 필요로 하는지, Wrapper class인 `Integer[]` 와 같은 방식을 매개변수로 필요로 하는지에 따라서 코드의 동작 유무가 갈리고 이 때문에 혼동을 많이 줘서 시간을 오래 쓴 것 같다. 이를 의도적으로 인지하는 것이 중요한 것 같다.
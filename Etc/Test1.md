# Test 1

## 설명
문자열 리스트 words 를 입력받으면, 문자열의 공백과 대소문자 구분은 하지 않은채로, 각 단어의 빈도수 를 리턴하는 함수를 작성해주세요.

## 예시
input : [“apple”, “book”, “Apple “]
output : mapOf(“apple”,2 , “book”, 1)
(apple 이라는 key 의 value 가 2 이고,  book 이라는 key 의 value 가 1 인 Map)

## 풀이

```java
import java.util.*;

public class Main {
Map<String, Integer> solution(List<String> words) {
        Map<String, Integer> answer = new HashMap<>();

        for (String word : words) {
            word = word.toLowerCase();

            if (!answer.containsKey(word)) {
                answer.put(word, 0);
            }
            answer.put(word, answer.get(word) + 1);
        }

        return answer;
    }
    public static void main(String[] args) {
        Main T = new Main();

        List<String> words =
                new ArrayList<>() {
                    {
                        add("apple");
                        add("book");
                        add("Apple");
                    }
                };

        System.out.print(T.solution(words));
    }
}

// output
// {apple=2, book=1}
```

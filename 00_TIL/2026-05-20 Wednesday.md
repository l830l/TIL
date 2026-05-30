# 📘 오늘 학습한 내용들

##### 📌 한 일 적기

## 코딩테스트

### 코딩 테스트 완전 정복
#### 06 스택
##### 스택 개념
- 스택
	- 먼저 입력한 데이터를 제일 나중에 꺼낼 수 있는 자료 구조
	- 선입후출
	- LIFO(Last In First Out)
	- 푸시(Push): 스택에 삽입하는 연산
	- 팝(Pop): 꺼내는 연산
- 그 이외의 내용은 생략함
##### 몸풀기 문제
###### 문제 08 올바른 괄호
- [문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12909)
- 푼 코드(스택으로 안푼거)
	- 의사코드
		1. 괄호에 따라 더하고 뺄 숫자를 선언하여 1로 선언한다.
		2. s 가 2보다 작거나 짝수가 아니면 이것은 올바른 괄호가 아니다(예외처리)
		3. s 의 문자에 따라 ‘(’이면 +1 로 ‘)’이면 -1 로 해준다.
		4. 만약 이것이 올바른 괄호라면 0 이되는 순간이 없으므로 0이 되는 순간이 있다면 바로 올바르지 않은 괄호로 처리한다.
``` java
class Solution {
    boolean solution(String s) {
        int count = 1;
        int stringLength = s.length();
        if(stringLength < 2 || stringLength % 2 != 0) return false;

        for(int i = 0; i < stringLength; i++) {
            char ch = s.charAt(i);
            count = ch == '('? count + 1 : count - 1;
            if(count < 1) return false;
        }

        return count == 1;
    }
}
```
- 스택으로 푼거
	- 의사코드
		1. s의 문자 길이가 2보다 작거나 홀수이면 올바른 괄호가 아니다.(예외 처리)
	    2. 만약 s의 문자가 ‘(’이면 집어넣고 ‘)’이면 뺀다
	    3. 그런데 스택이 비어있는데 빼려고 하면 올바른 괄호가 아니다
``` java
import java.util.*;

class Solution {
    boolean solution(String s) {
        int stringLength = s.length();
        if(stringLength < 2 || stringLength % 2 != 0) return false;
        Stack<Character> stack = new Stack<>();

        for(int i = 0; i < stringLength; i++) {
            char ch = s.charAt(i);
            if(ch == '('){
                stack.push(ch);
            }else{
                if(stack.empty()) return false;
                stack.pop();
            }
        }
        return stack.empty();
    }
}
```

###### 문제 09. 10진수를 2진수로 변환하기
- 문제
	- 10진수를 입력받아 2진수로 변환해 반환하는 solution() 함수를 구현하세요.
- 제약 조건
	- `decimal`은 1 이상 10억 미만의 자연수입니다.
- 입출력 예

| decimal | 반환값            |
| ------- | -------------- |
| 10      | 1010           |
| 27      | 11011          |
| 12345   | 11000000111001 |
- 의사코드
    1. 결과를 문자열로 뱉을걸 정한다.
    2. 2로 나눈 나머지가 1이면 결과를 앞에 붙인다.
    3. decimal 을 2로 나눈다
    4. decimal 이 1이하가 될 때까지 반복한다.
    5. 마지막의 나머지를 앞에 붙이고 리턴한다.
- 푼 코드 (스택 안쓴거)

```java
class Solution {
    String solution(int decimal) {
        StringBuilder result = new StringBuilder();
        while (decimal > 1){
            result.insert(0, decimal % 2 + "");
            decimal /= 2;
        }
        result.insert(0, decimal + "");
        return result.toString();
    }
}
```

- 의사 코드
    1. decimal 이 1 이하가 될 때까지 2로 나눈 나머지를 스택에 넣고 2로 나눈다.
    2. 마지막으로 decimal 을 스택에 넣는다.
    3. 스택을 문자열로 뱉고 반환한다.
-  푼 코드 (스택 쓴거)
``` java
class Solution {
    String solution(int decimal) {
        Stack<String> result = new Stack<>();
        while (decimal > 1){
            result.push(decimal % 2 + "");
            decimal /= 2;
        }
        result.push(decimal + "");
        return result.toString().join("", result);
    }
}
```

##### 합격자가 되는 모의 테스트
###### 문제 10 괄호 회전하기
- [문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/76502)
- 의사 코드
	1. 예외처리
		1. 해당 문자열이 2보다 작거나 짝수가 아니거나, 여는 괄호와 닫는 괄호의 갯수가 같지 않으면 해당 문자열은 많이 회전해도 올바른 괄호가 될 수 없으므로 바로 0을 리턴한다.
	2. 주어진 문자열이 올바른 괄호 문자인지 확인한다.
		1. StringBuilder 를 이용하여 순서나 갯수를 체크한다.
		2. 여는 괄호일 경우 같은 모양의 닫는 괄호를 넣는다
		3. 닫는 괄호일 경우에서
			1. StringBuilder 가 비어있거나 마지막 문자와 현재의 문자가 다를 경우 잘못된 문자열이라 판단한다
			2. 마지막 것을 삭제한다
			3. 마지막 것을 삭제하고 StringBuilder 가 비어있거나, 여는 괄호일 경우 괄호 갯수를 증가시킨다.
	3. 올바르지 않은 문자열일 경우 회전시킨다.
	4. 문자열 길이만큼 회전 시켰는데도 올바르지 않은 문자열이 계속되면, 0을 리턴한다.
	5. 올바른 문자열이 되면 괄호 수를 리턴한다.
-  푼 코드
``` java
class Solution {
    int parenthesesCount = 0;

    public int solution(String s) {
        int length = s.length();

        // 1. 예외처리
        if(!isSimpleValidString(s, length)) return 0;

        int rotateCount = 0;
        StringBuilder sb = new StringBuilder(s);

        // 2. 주어진 문자열이 올바른 괄호 문자인지 확인한다.
        // 4. 문자열 길이만큼 회전 시켰는데도 올바르지 않은 문자열이 계속되면, 0을 리턴한다.
        while(!isValidString(s, length) && rotateCount < length){
            // 3. 올바르지 않은 문자열일 경우 회전시킨다.
            sb.append(sb.charAt(0));
            sb.deleteCharAt(0);
            s = sb.toString();
            rotateCount++;
        }

        // 5. 올바른 문자열이 되면 괄호 수를 리턴한다.
        return parenthesesCount;
    }


    // 해당 문자열이 2보다 작거나 짝수가 아니거나, 여는 괄호와 닫는 괄호의 갯수가 같지 않으면 
    // 해당 문자열은 많이 회전해도 올바른 괄호가 될 수 없으므로 바로 0을 리턴한다.
    private boolean isSimpleValidString(String s, int length){
        int check = 0;
        if(length < 2 || length % 2 != 0) return false;
        for(int i = 0; i < length; i++) {
            if(s.charAt(i) == '(' || s.charAt(i) == '[' || s.charAt(i) == '{') {
                check++;
            } else {
                check--;
            }
        }
        return check == 0;
    }

    // 해당 문자열이 올바른 괄호 문자열인지 제대로 체크한다.
    private boolean isValidString(String s, int length){
        // 1. StringBuilder 를 이용하여 순서나 갯수를 체크한다.
        StringBuilder sb = new StringBuilder();

        for(int i = 0; i < length; i++) {
            char ch = s.charAt(i);

            switch (ch){
                // 2. 여는 괄호일 경우 같은 모양의 닫는 괄호를 넣는다
                case '(' -> sb.append(')');
                case '[' -> sb.append(']');
                case '{' -> sb.append('}');

                // 3. 닫는 괄호일 경우에서
                default -> {
                    // 1. StringBuilder 가 비어있거나 마지막 문자와 현재의 문자가 다를 경우 잘못된 문자열이라 판단한다
                    if(sb.length() == 0 || sb.charAt(sb.length() - 1) != ch) {
                        parenthesesCount = 0;
                        return false;
                    };

                    // 2. 마지막 것을 삭제한다
                    sb.deleteCharAt(sb.length() - 1);

                    // 3. 마지막 것을 삭제하고 StringBuilder 가 비어있거나, 여는 괄호일 경우 괄호 갯수를 증가시킨다.
                    if(sb.length() == 0){
                        parenthesesCount++;
                    }else{
                        char lastChar = sb.charAt(sb.length() - 1);
                        if(lastChar == '(' || lastChar == '[' || lastChar == '{') parenthesesCount++;
                    }
                }
            }
        }

        // 올바른 문자라고 판단한다.
        return sb.length() == 0;
    }
}
```
- 시간 복잡도 : O(N²)

###### 문제 11 짝지어 제거하기
- [문제 코드](https://school.programmers.co.kr/learn/courses/30/lessons/12973)
- 의사코드
	1. 문자열을 하나씩 넣는데 넣는것과 맨 위에 것이 같으면 제거한다.
	2. 스택이 모두 비면 1을 반환한다.
	3. 스택이 비어있지 않으면 0을 반환한다.
- 푼 코드
``` java
class Solution
{
    public int solution(String s)
    {
        int answer = 0;

        // 문자열을 하나씩 넣는데 넣는것과 맨 위에 것이 같으면 제거한다.
        Stack<Character> stack = new Stack<>();
        int sLength = s.length();
        for(int i = 0; i < sLength; i++){
            char ch = s.charAt(i);
            char last = stack.isEmpty() ? '#' : stack.peek();
            if(ch == last) stack.pop();
            else stack.push(ch);
        }

        // 스택이 모두 비면 1을 반환한다. 스택이 비어있지 않으면 0을 반환한다.
        return stack.isEmpty() ? 1 : 0;
    }
}
```
- 시간 복잡도 : O(n)

###### 문제 12 주식가격 ★
- [문제 코드 ](https://school.programmers.co.kr/learn/courses/30/lessons/42584)
- 의사 코드
	1. price 배열을 받으면, return 할 배열도 만든다
	2. price 만큼 반복한다.
	3. price 에서 다음 인덱스 부터 차례로 넣되, 넣다가 현재 price 보다 작은 가격이 있으면 stack size 를 넣어주고 스택쌓기 그만 하고 다음으로 넘어간다.
- 푼 코드
``` java
import java.util.*;

class Solution {
    public int[] solution(int[] prices) {
        // price 배열을 받으면, return 할 배열도 만든다
        int length = prices.length;
        int[] answer = new int[length];

        // price 만큼 반복한다.
        for(int i = 0; i < length - 1; i++) {
            Stack<Integer> stack = new Stack<>();
            int current = prices[i];
            for(int j = i + 1; j < length; j++){
                int compare = prices[j];
                stack.push(compare);
                if(current > compare){
                    answer[i] = stack.size();
                    break;
                }
                answer[i] = stack.size();
            }
        }

        return answer;
    }
}
```
- 시간 복잡도 : O(n^2)
- 개선 필요
	1. 반복적으로 다음것들을 내부에서 검사하면서 N번 반복되고 이것을 price  만큼 반복하므로 x N 번 걸림
	2. 반복적인 검사를 줄여야 함



___

# 🧠 마인드맵 작성 체크
> 31일치 복습 시작 전 **반드시** 작성할 것!

---
# 🔁 복습 체크리스트
##### 그냥 꼼꼼히 읽기
- [x] [D-1] 2025-05-21
- [x] [D-3] 2026-05-23
- [x] [D-7] 2026-05-27
##### 옵시디언에 정리
- [ ] [D-17]
- [ ] [D-31]
- [ ] [D-51]

##### 마인드 맵에 정리
- [ ] [D-79]
- [ ] [D-107]
- [ ] [D-143]

##### 전체 마인드 맵에 넣기
- [ ] [D-181]
gemini
## 10년 경력 C/C++ 개발자 코딩 테스트 문제 (포인터 활용)

**문제:**

문자열을 입력받아, 문자열 내의 각 단어를 역순으로 뒤집어 출력하는 프로그램을 작성하세요. 단어는 공백 문자(` `)를 기준으로 구분됩니다.

**입력:**

```
The quick brown fox jumps over the lazy dog
```

**출력:**

```
ehT kciuq nworb xof spmuj revo eht yzal god
```

**요구사항:**

1. 포인터를 사용하여 문자열을 조작해야 합니다.
2. 동적 메모리 할당을 사용하지 않아야 합니다.
3. 표준 라이브러리의 문자열 관련 함수 (`strlen`, `strcpy` 등) 사용은 제한됩니다.

**예시 코드 (참고):**

```c++
#include <iostream>

using namespace std;

void reverseString(char* str) {
    char* start = str;
    char* end = str;

    while (*end) { // 문자열 끝까지 이동
        end++;
    }
    end--; // 마지막 null 문자 앞으로

    while (start < end) { // 시작과 끝 포인터가 만날 때까지
        char temp = *start;
        *start = *end;
        *end = temp;
        start++;
        end--;
    }
}

void reverseWords(char* str) {
    char* wordStart = str;

    while (*str) {
        if (*str == ' ') { // 공백을 만나면
            *str = '\0'; // 단어 끝 표시
            reverseString(wordStart); // 단어 뒤집기
            wordStart = str + 1; // 다음 단어 시작
        }
        str++;
    }
    reverseString(wordStart); // 마지막 단어 뒤집기
}

int main() {
    char input[] = "The quick brown fox jumps over the lazy dog";
    reverseWords(input);
    cout << input << endl;

    return 0;
}
```

**코드 설명:**

1. `reverseString` 함수: 주어진 문자열을 포인터를 이용해 뒤집습니다.
2. `reverseWords` 함수: 문자열을 순회하며 공백을 기준으로 단어를 구분하고 `reverseString` 함수를 호출하여 각 단어를 뒤집습니다.
3. `main` 함수: 입력 문자열을 `reverseWords` 함수에 전달하고 결과를 출력합니다.

**평가:**

* 포인터 사용 숙련도
* 문자열 조작 능력
* 문제 해결 능력
* 코드 효율성

**추가 질문 (선택):**

* 시간 복잡도와 공간 복잡도를 분석해보세요.
* 동적 메모리 할당을 사용하여 문제를 해결해보세요.
* 이 문제를 해결하는 다른 알고리즘을 제시해보세요.

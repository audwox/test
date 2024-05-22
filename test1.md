gemini
## 10년 경력 C/C++ 개발자 코딩 테스트 문제

**문제:**

**동적 메모리 할당을 이용하여 2차원 배열을 구현하고, 행렬 곱셈을 수행하는 프로그램을 작성하세요.**

**요구사항:**

1. **동적 메모리 할당:** 사용자로부터 행렬의 크기를 입력 받아 동적 메모리를 할당하여 2차원 배열을 생성합니다.
2. **행렬 입력:** 사용자로부터 행렬의 값을 입력 받아 2차원 배열에 저장합니다.
3. **행렬 곱셈:** 입력 받은 두 행렬의 곱셈을 수행합니다.
4. **결과 출력:** 곱셈 결과를 2차원 배열로 출력합니다.
5. **메모리 해제:** 사용한 동적 메모리를 해제합니다.

**포인터 활용:**

* 2차원 배열을 동적 메모리 할당할 때 포인터를 사용합니다.
* 행렬 곱셈 연산을 수행할 때 포인터를 이용하여 효율적으로 배열 요소에 접근합니다.

**추가 고려 사항:**

* 입력 받은 행렬의 크기가 올바른지 검증합니다. (예: 행렬 곱셈을 수행하기 위해 첫 번째 행렬의 열 수와 두 번째 행렬의 행 수가 같아야 합니다.)
* 메모리 누수를 방지하기 위해 동적 메모리를 적절히 해제합니다.
* 코드 가독성과 유지보수성을 위해 주석을 명확하게 작성합니다.

**예시:**

```c++
#include <iostream>

using namespace std;

int main() {
    // 행렬 크기 입력
    int row1, col1, row2, col2;
    cout << "첫 번째 행렬의 행과 열을 입력하세요: ";
    cin >> row1 >> col1;
    cout << "두 번째 행렬의 행과 열을 입력하세요: ";
    cin >> row2 >> col2;

    // 행렬 곱셈을 수행할 수 있는지 확인
    if (col1 != row2) {
        cout << "행렬 곱셈을 수행할 수 없습니다." << endl;
        return 1;
    }

    // 동적 메모리 할당
    int **matrix1 = new int*[row1];
    int **matrix2 = new int*[row2];
    int **result = new int*[row1];
    for (int i = 0; i < row1; i++) {
        matrix1[i] = new int[col1];
    }
    for (int i = 0; i < row2; i++) {
        matrix2[i] = new int[col2];
    }
    for (int i = 0; i < row1; i++) {
        result[i] = new int[col2];
    }

    // 행렬 값 입력
    cout << "첫 번째 행렬의 값을 입력하세요:" << endl;
    for (int i = 0; i < row1; i++) {
        for (int j = 0; j < col1; j++) {
            cin >> matrix1[i][j];
        }
    }
    cout << "두 번째 행렬의 값을 입력하세요:" << endl;
    for (int i = 0; i < row2; i++) {
        for (int j = 0; j < col2; j++) {
            cin >> matrix2[i][j];
        }
    }

    // 행렬 곱셈 수행
    for (int i = 0; i < row1; i++) {
        for (int j = 0; j < col2; j++) {
            result[i][j] = 0;
            for (int k = 0; k < col1; k++) {
                result[i][j] += matrix1[i][k] * matrix2[k][j];
            }
        }
    }

    // 결과 출력
    cout << "곱셈 결과 행렬:" << endl;
    for (int i = 0; i < row1; i++) {
        for (int j = 0; j < col2; j++) {
            cout << result[i][j] << " ";
        }
        cout << endl;
    }

    // 동적 메모리 해제
    for (int i = 0; i < row1; i++) {
        delete[] matrix1[i];
    }
    delete[] matrix1;
    for (int i = 0; i < row2; i++) {
        delete[] matrix2[i];
    }
    delete[] matrix2;
    for (int i = 0; i < row1; i++) {
        delete[] result[i];
    }
    delete[] result;

    return 0;
}
```

**평가 기준:**

* 동적 메모리 할당 및 해제의 정확성
* 행렬 곱셈 연산의 정확성
* 코드 가독성 및 유지보수성
* 오류 처리 및 예외 처리

**참고:**

* 위 문제는 예시이며, 난이도를 조절하여 다양한 문제를 출제할 수 있습니다.
* 10년 경력 개발자에게는 더 복잡하고 실무적인 문제를 출제하는 것이 좋습니다. (예: 다중 스레드, 네트워크 통신, 데이터베이스 연동 등)

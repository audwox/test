이 문제는 포인터와 관련된 내용을 포함합니다.

### 문제: Linked List Cycle Detection

#### 문제 설명
단일 연결 리스트(singly linked list)에서 사이클(cycle)이 존재하는지 여부를 확인하는 함수를 작성하세요. 연결 리스트에 사이클이 존재한다면, 그것은 한 노드가 리스트 내의 이전 노드 중 하나로 다시 연결된 경우를 말합니다.

#### 함수 시그니처
```c++
struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(nullptr) {}
};

bool hasCycle(ListNode *head);
```

#### 입력
- `ListNode* head`: 연결 리스트의 첫 번째 노드에 대한 포인터.

#### 출력
- 연결 리스트에 사이클이 있으면 `true`, 없으면 `false`를 반환합니다.

#### 예제
1. 입력: `head = [3, 2, 0, -4]` (pos = 1, where pos is the position of the node (0-indexed) that the tail connects to, forming a cycle)
   출력: `true`

2. 입력: `head = [1, 2]` (pos = 0)
   출력: `true`

3. 입력: `head = [1]` (no cycle)
   출력: `false`

#### 힌트
- 포인터를 이용하여 사이클을 탐지하기 위해 "토끼와 거북이" 알고리즘(플로이드의 사이클 탐지 알고리즘)을 사용할 수 있습니다.
- 두 개의 포인터를 사용합니다: 하나는 한 번에 한 단계씩 이동하고, 다른 하나는 두 단계씩 이동합니다. 만약 두 포인터가 만난다면, 사이클이 존재하는 것입니다.

#### 솔루션
```c++
#include <iostream>

struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(nullptr) {}
};

bool hasCycle(ListNode *head) {
    if (head == nullptr || head->next == nullptr) {
        return false;
    }
    
    ListNode *slow = head;
    ListNode *fast = head->next;
    
    while (slow != fast) {
        if (fast == nullptr || fast->next == nullptr) {
            return false;
        }
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return true;
}

int main() {
    // Test case 1
    ListNode* head1 = new ListNode(3);
    head1->next = new ListNode(2);
    head1->next->next = new ListNode(0);
    head1->next->next->next = new ListNode(-4);
    head1->next->next->next->next = head1->next; // Creating a cycle

    std::cout << "Test case 1: " << (hasCycle(head1) ? "Cycle detected" : "No cycle") << std::endl;

    // Test case 2
    ListNode* head2 = new ListNode(1);
    head2->next = new ListNode(2);
    head2->next->next = head2; // Creating a cycle

    std::cout << "Test case 2: " << (hasCycle(head2) ? "Cycle detected" : "No cycle") << std::endl;

    // Test case 3
    ListNode* head3 = new ListNode(1);

    std::cout << "Test case 3: " << (hasCycle(head3) ? "Cycle detected" : "No cycle") << std::endl;

    return 0;
}
```

이 문제는 포인터를 사용하는 고급 개념을 포함하고 있으며, 링크드 리스트와 사이클 탐지와 같은 복잡한 자료 구조와 알고리즘을 테스트하는 데 적합합니다.

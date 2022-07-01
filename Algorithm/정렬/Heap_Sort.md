### 힙 정렬
선택정렬과 힙 정렬은 유사하다. 선택 정렬을 떠올려보자. 오름차순으로 정렬할때, 전체 배열을 순회하고 가장 작은 값을 선택하여 첫번째 원소에 넣는 방식으로 진행했다. 그렇다면
반대로 가장 큰 값을 맨 뒤로 보내는 방식으로 구현한다고 했을때, 단순히 순회를 통해 가장 큰 값을 찾는 경우 시간 복잡도는 O(N^2)이다. 하지만 만약 가장 큰 값을 찾는데에 logN의
시간이 걸린다면 O(N*logN)이 될 것이다. 실제로 logN만에 가장 큰 값을 찾는 방법이 존재하며 그것은 heap 자료구조를 이용하는 것이다.

### Heap
Max Heap을 예로 들면 이진트리 중 모든 노드에 대하여 부모노드가 자식노드보다 큰 값을 가지면 Max Heap이라고 한다. 여기서 루트노드는 트리 전체중 최대값을 의미한다. 
또한 heap은 일차원 배열로 나타낼 수 있는데, 배열 중 부모노드 index를 i라고 할때, 이 노드의 왼쪽 자식 노드 번호는 i*2가 되고, 오른쪽 자식 노드는 i*2+1이 된다. 따라서
임의로 주어진 일차원 배열을 heap으로 만드는 방법은 n개의 노드가 있을 때, n/2부터 거꾸로 1번째 노드까지 heap의 특성에 맞게 현재 노드를 밑으로 계속 내려주는 작업을 해주면 된다. <br>

예를들면 max heap을 만든다고 하고 7개의 노드가 있을 때, n/2 = 3 이므로 3번과 그의 자식 노드끼리 비교하여 3번이 자식보다 작다면 두 자식 중 가장 큰 자식과 3번을 교환해준다.
그리고 교환한 자식이 7번이라면 7번에 대하여 같은 작업을 재귀적으로 수행해준다. 이때 7번 노드는 자식이 없으므로 과정은 종료되고 2번째, 1번째 노드에 대해서도 각각 작업을 해준다.
이 과정을 간단하게 heapify라고 하자. 이때 n/2부터 heapify를 수행하는 이유는 가장 밑에 있는 노드를 제외한 모든 노드에 대해 heapify를 수행하면 원하는 heap 구조를 얻기 때문이다. <br>

### 힙 정렬 방법
그렇다면 heap 정렬은 어떻게 진행 될까? 오름차순 정렬이라고 할때 다음 과 같이 진행된다.<br>
1. 배열을 max heap구조로 만든다.
2. 루트 노드가 최대 값이므로 루트노드와 맨 끝에 있는 노드를 바꿔준다.
3. 바꿔준 노드에 대해 heapify를 진행해준다 이때, 맨 마지막 노드는 heap에서 제외한다. (중요)
4. 2번 3번 과정을 n-1번 진행한다. <br>

코드는 다음과 같다.
```c
#include <iostream>
#include <vector>

using namespace std;

void heapfy(vector<int> &arr, int i, int n){
    int L = i*2;
    int R = i*2 + 1;
    int largest = i;

    if(L<=n && (arr[largest] < arr[L])){
        largest = L;
     }

    if(R<=n && (arr[largest] < arr[R])){
        largest = R;
     }

    if(largest != i){
        int temp = arr[i];
        arr[i] = arr[largest];
        arr[largest] = temp;
        heapfy(arr, largest, n);
    }
}

void heap_sort(vector<int> &arr, int n){
    for(int i=n/2; i>0; i--)
        heapfy(arr, i, n);

    for(int i=n; i>1; i--){
        int temp = arr[1];
        arr[1] = arr[i];
        arr[i] = temp;

        heapfy(arr, 1, i-1);
    }
}

int main(){
    int n;
    cin>>n;
    vector<int> arr(n+1);

    for(int i=1; i<=n; i++)
        cin>>arr[i];

    heap_sort(arr, n);

    for(int i=1; i<=n; i++){
        cout<<arr[i]<<' ';
    }

    return 0;
}
```


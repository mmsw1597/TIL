### Heap
힙이라 불리는 특별한 이진트리를 알아보자. 종류로는 Max heap, Min heap이 있고 노드가 삽입되거나 삭제되었을 때, heap 구조를 유지하는데 O(logN)의 시간이 걸리며
트리에서 최대 최소 값을 구하는데는 O(1)의 시간이 걸리는 특징이 있다. 

### 완전 이진 트리
이진 트리에서 무조건 왼쪽에서부터 차례대로 채워져 있는 트리를 의미한다.<br>
![image](https://user-images.githubusercontent.com/55936770/178145680-addf1930-f472-4974-b0e9-40b297aea076.png)<br>
heap은 완전 이진 트리 형태를 띄워야 한다.

### Heap이 유용할 때
heap 자체를 만드는 데에는 O(N)이 걸리며 특정 노드를 삽입/삭제할때는 O(logN)이 걸리고 최대 최소를 구할땐 O(1)이 걸린다. 이때 삭제는 루트노드에서만 가능함에 유의하자<br><br>
위 사실을 알때, Heap은 오로지 최대, 최소값을 찾는데에만 유용하며 최대, 최소를 제외한 나머지 값의 위치는 알려주지 않는다. 또한 만약 최대값을 단 한번만 찾는다면
heap을 사용해서 찾는것 보단, 단순히 완전 탐색을 통해 O(N)만에 찾는 것이 더 좋다. 그러나 빈번하게 최대, 최소를 찾는다면 Heap은 굉장히 유용하다.

### Heap 만들기
n/2번째 원소(자식이 리프노드인 원소)부터 heapify라는 과정을 거친다. heapify는 다음과 같은 과정을 말한다.
1. 현재 노드를 i라고 할때 i, i*2와 i*2+1중 가장 큰 노드가 무엇인지 판별한다.
2. 만약 가장 큰 것이 i가 아닐 경우 현재 노드와 가장 큰 노드를 교환한다.
3. 교환 이후 교환된 위치에서 다시 heapfy를 반복한다.
4. 현재 i 노드가 가장 크다면 반복을 종료한다.

```c
function heapify(arr[], n, i)
  set largest = i                     // 최대 노드가 i번이라고 가정합니다.
  set l = i * 2                       // 왼쪽 자식 노드 번호입니다.
  set r = i * 2 + 1                   // 오른쪽 자식 노드 번호입니다.

  if l <= n && arr[l] > arr[largest]  // 왼쪽 자식이 크다면, 최대 번호를 수정합니다.
    largest = l

  if r <= n && arr[r] > arr[largest] // 오른쪽 자식이 크다면, 최대 번호를 수정합니다.
    largest = r

  if largest != i                   // 최대 노드가 자식 노드라면
    swap(arr[i], arr[largest])      // 해당 자식과 현재 노드를 교환해준 뒤
    heapify(arr, n, largest)        // 내려간 위치에서 다시 heapify를 진행합니다.
```

```c
function build_heap(arr[], n)
  for i = n / 2 ... i >= 1       // n / 2번째 원소부터 1번째 원소까지 돌며
    heapify(arr, n, i)             // heapify 과정을 진행하여 max-heap을 만들어줍니다.
```
heapify과정은 한번에 최대 logN번 일어나고 n/2개의 원소에 대해 heapify를 진행하므로 총 O(N)이 소요된다.

### 삽입
Heap 구조에서 무작정 삽입하면 heap 구조가 망가지므로 추가적인 처리가 필요하다. n개의 노드가 있는 트리에 삽입할때, n+1에 일단 삽입한 뒤, 부모와 비교하여
크면 교환하고 크지 않으면 멈춘다. 결국 시간복잡도는 높이와 관련있게 되고 O(logN)이 걸린다.
```c
function insert(arr[], n, x)
  arr.append(x)                          // 가장 끝에 노드 x를 추가합니다.

  set i = n + 1                          // 마지막 노드에서 시작합니다.
  while i > 1 and arr[i / 2] < arr[i]    // 부모가 자식보다 값이 작은 경우라면
                                         // max-heap 조건에 어긋나므로
    swap(arr[i], arr[i / 2])             // 두 값을 교환하고
    i = i / 2                            // 부모 위치로 올라갑니다.
```

### 삭제
Heap에서 특정 값의 위치는 정확히 모른다. 다만 루트 노드의 값만을 확신할 수 있을 뿐이다. 따라서 삭제는 루트에서만 이루어진다. 루트 노드를 삭제한 뒤, 맨 끝값과 교환해주고
heap 구조가 망가졌으므로 다시 heap 구조를 맞추기 위해 heapify를 진행한다. 따라서 시간복잡도는 O(logN)이 된다.
```c
function heapify(arr[], n, i)
  set largest = i                     // 최대 노드가 i번이라고 가정합니다.
  set l = i * 2                       // 왼쪽 자식 노드 번호입니다.
  set r = i * 2 + 1                   // 오른쪽 자식 노드 번호입니다.

  if l < n && arr[l] > arr[largest]  // 왼쪽 자식이 크다면, 최대 번호를 수정합니다.
    largest = l

  if r < n && arr[r] > arr[largest] // 오른쪽 자식이 크다면, 최대 번호를 수정합니다.
    largest = r

  if largest != i                   // 최대 노드가 자식 노드라면
    swap(arr[i], arr[largest])      // 해당 자식과 현재 노드를 교환해준 뒤
    heapify(arr, n, largest)        // 내려간 위치에서 다시 heapify를 진행합니다.

function remove(arr[], n)
  arr[1] = arr[n]                   // 가장 끝에 있는 노드를 첫 번째 노드에 옮겨주고
  delete arr[n]                     // 가장 마지막 노드를 삭제합니다.
  heapify(arr, n - 1, 1)            // 직후에 1번 노드를 기준으로 heapify를 진행하여
                                    // max-heap 상태를 계속 유지해줍니다. 
```





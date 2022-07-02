### 이진탐색
업다운 게임과 비슷한방식이다. 한 사람이 수를 생각하고 그 수를 맞추는 게임인데, 맞추는 사람은 특정 값을 부르고 나머지 사람은 그 숫자가 생각한 숫자보다 큰지, 작은지를 알려준다.
보통 이 게임에서 빠르게 답을 찾으려면 범위의 가운데에 해당하는 숫자를 불러야 빠르게 맞출 수 있다. 이런 방식으로 배열내에 특정 숫자를 찾을때 가운데 값 기준으로 그 숫자가
가운데 값보다 큰지 작은지에 따라 범위를 반으로 좁혀나가며 숫자를 탐색하는 방법을 이진탐색이라고 한다. 전제 조건은 배열이 정렬이 되어있어야 한다는 점이다.

### 수도코드
```c
function binary_search(arr, target)
  int left = 0;
  int right = arr.size - 1;
  while(left <= right) //범위 내에 숫자가 하나일때까지 진행한다. 등호 필수
      int mid = (left + right) / 2;
      if(arr[mid] == target) //타겟을 찾았을 때
         return mid;
      if(arr[mid]>target)
         right = mid - 1; //mid가 아닌 mid -1을 대입하는 것에 유의
      else
        left = mid + 1;
  return -1;
```
arr[mid]값또한 범위내에서 탐색했으므로 다음 탐색에서 mid도 범위에서 제외해야하는 것을 유의하자.

### 이진탐색 vs 순차탐색
이진탐색은 시간복잡도가 O(logN)이다. 하지만 조건이 따르는데 배열이 정렬이 되어있어야한다는 점이다. 만약 배열이 정렬되어있지 않다면 이진탐색은 O(N^2)또는 O(NlogN)의 
시간복잡도를 갖게 된다. 이에 반해 순차탐색은 시간복잡도가 O(N)이며 정렬이 필요없다. O(logN)과 O(N)의 시간복잡도 차이는 어마어마하다. 약 40억개의 데이터를 O(N)으로
탐색할 경우 40억회의 탐색을 거쳐야하는 반면 O(logN)은 약 30번의 탐색만 거쳐도 그 수를 찾을 수 있다. 그렇다면 어느상황에서 이진탐색을 사용해야할까? <br>
우선 배열이 정렬이 되어있다면 무조건 이진탐색이 더 빠르다. 하지만 배열이 정렬이 되어있지 않고 탐색해야할 수가 적다면 순차탐색이 빠르다. 하지만 만약 탐색해야할 수가 많다면
정렬을 한뒤 이진탐색을 진행하는 것이 빠를 것이다.

### Lower Bound
하한이라는 단어로 원하는 값 target이상의 값이 최초로 나오는 위치를 의미한다. 즉 target이상의 값중 가장 작은 index를 갖는 원소를 의미한다. 하한은 어떻게 찾아야할까? 답은
이진탐색으로 찾을 수 있다.
```c
function lower_bound(arr, target)
  int left = 0;
  int right = arr.size - 1;
  int min_idx = arr.size; //가능한 값중 최소를 찾아야 하므로 절대 나올 수 없는 최대값을 삽입
  while(left <= right) //범위 내에 숫자가 하나일때까지 진행한다. 등호 필수
      int mid = (left + right) / 2;
      if(arr[mid] >= target) //하한의 조건은 일단 target이상이어야 하므로 해당 조건에서 하한을 찾는다.
         min_idx = min(min_idx, mid);
         right = mid -1; //왼쪽에 조건을 만족하는 최소값이 있을 가능성이 있다.
      else
        left = mid + 1;
  return -1;
```
### Upper Bound
상한이라는 단어로 원하는 값 target 초과의 값이 최초로 나오는 위치를 의미한다. 즉 target 초과의 값중 최솟값을 의미한다. 
```c
function lower_bound(arr, target)
  int left = 0;
  int right = arr.size - 1;
  int min_idx = arr.size; //가능한 값중 최소를 찾아야 하므로 절대 나올 수 없는 최대값을 삽입
  while(left <= right) //범위 내에 숫자가 하나일때까지 진행한다. 등호 필수
      int mid = (left + right) / 2;
      if(arr[mid] > target) //상한의 조건은 target과 같지않고 더 커야하므로 등호를 빼준다.
         min_idx = min(min_idx, mid);
         right = mid -1; //왼쪽에 조건을 만족하는 최소값이 있을 가능성이 있다.
      else
        left = mid + 1;
  return -1;
```
### 상한과 하한
상한과 하한을 어떻게 활용할까? 상한과 하한의 차이는 target의 개수를 의미한다. 만약 상한과 하한이 같다면 target이 배열내에 없다는 것을 의미한다.




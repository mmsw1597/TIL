### 퀵 정렬
N개의 값 중 기준 값을 잡고 기준 값 이상, 미만으로 분류하는 방법의 정렬이다. 특정 값 기준으로 나누고 나면 두 개의 그룹으로 나뉘게 되는데 각각에 대해서 또 퀵 정렬을
재귀적으로 수행하여 정렬한다. 이러한 방식을 나누게 되면 정확히 2등분을 나누는 것이 아니기 때문에 매번 logN번 수행된다고 말할 수는 없다. 최악의 경우 N번 분할하게 되어
최종 시간복잡도가 O(N^2)가 나올 수 있다. 하지만 최악의 경우가 나오지 않도록 하는 방법이 여러가지 있고, 그 중 하나가 적절한 기준 값을 잡는 것이다. <br><br>

적절한 기준값을 갖는 피벗 탐지 알고리즘으로 최악의 경우를 피하면 평균적으로 O(N*logN)의 시간복잡도가 나오고 이름에서 알 수 있듯이 일반적인 상황에서 퀵 정렬은 다른 정렬보다 
월등히 빠르다. 피벗 탐지 알고리즘 중 하나의 예로 들면 배열의 맨 왼쪽, 중간, 오른쪽 중 크기 기준 중간값을 피벗으로 잡는 방법이 있다. 간단한 수도코드로 나타내면 다음과 같다.

```c
function quick_sort(){
  if(low < high){
   int pos = partition(arr, low, high); //피벗 기준으로 구간 나누기
   quick_sort(arr, low, pos -1) //왼쪽 구간에 대해 퀵 정렬
   quick_sort(arr, pos+1, high) //오른쪽 구간에 대해 퀵 정렬
   }
}
```

실제 코드는 다음과 같다.
```c
#include <iostream>
#include <vector>

using namespace std;

int partition(vector<int> &arr, int low, int high){
    int j = low - 1;
    int pivot = arr[high];
    
    for(int i=low; i<high; i++){
        if(arr[i] < arr[high]){
            j++;

            int temp = arr[j];
            arr[j] = arr[i];
            arr[i] = temp;
        }
    }

    int temp = arr[j+1];
    arr[j+1] = arr[high];
    arr[high] = temp;

    return j+1;
}

void quick_sort(vector<int> &arr, int low, int high){
    if(low < high){
        int pos = partition(arr, low, high);

        quick_sort(arr, low, pos - 1);
        quick_sort(arr, pos+1, high);
    }
}

int main(){
    int n;
    vector<int> arr;

    cin>>n;

    for(int i=0; i<n; i++){
        int c; 
        cin>>c;
        arr.push_back(c);
    }

    quick_sort(arr, 0, n-1);
    
    for(int i=0; i<n; i++){
        cout<<arr[i]<<' ';
    }
    return 0;  
}
```

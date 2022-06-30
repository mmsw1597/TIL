### 병합정렬
병합정렬은 오름차 순으로 정렬한다고 할 때, 정렬된 두 배열이 있다고 가정하고 두 정렬된 배열 중 첫번째 원소부터 차례대로 더 작은 원소를 최종 배열에 넣는 식으로 정렬하는 방법이다.
문제는 일반적인 상황에서 하나의 배열을 정렬하게 되는데 이때는 임의로 배열을 두 개로 나눠야 한다. 각 배열을 원소가 1개가 될 때까지 2등분하고 재귀적으로 정렬된 배열들을 하나로 합치는
식으로 전개된다. 이때 시간복잡도는 O(NlogN)이 된다. 간단한 수도코드로 나타내면 다음과 같다.
```c
function merge_sort(){
  if(low < high) {
    int mid = (low + high) /2
    merge_sort(arr, low, mid) //배열 2등분 왼쪽
    merge_sort(arr, mid+1, high) //배열 2등분 오른쪽
    merge(arr, low, mid, high) //두 배열 합치기
  }
}
```
실제 코드는 다음과 같다.
```
#include <iostream>
#include <vector>

using namespace std;

void merge_sort(vector<int> &arr, int low, int mid, int high){
    int i = low;
    int j = mid + 1;

    vector<int> merge_arr;

    while(i <= mid && j <= high){
        if(arr[i] <= arr[j]){
            merge_arr.push_back(arr[i]);
            i++;
        }
        else{
            merge_arr.push_back(arr[j]);
            j++;
        }
    }

    while(i <= mid){
        merge_arr.push_back(arr[i++]);
    }

    while(j <= high){
        merge_arr.push_back(arr[j++]);
    }

    int idx = 0;

    for(int k=low; k<=high; k++)
        arr[k] = merge_arr[idx++];
}

void merge(vector<int> &arr, int low, int high){
    if(low < high){
        int mid = (high + low) / 2;
        merge(arr, low, mid);
        merge(arr, mid+1, high);
        merge_sort(arr, low, mid, high);
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

    merge(arr, 0, n-1);
    for(int i=0; i<n; i++){
        cout<<arr[i]<<' ';
    }

    return 0;
}
```

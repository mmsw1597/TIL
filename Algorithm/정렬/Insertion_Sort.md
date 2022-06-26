### 삽입정렬
앞에서 부터 순서대로 보면서 앞에 있는 모든 원소가 정렬이 되어 있다는 가정 하에 현재 원소의 위치를 적절히 삽입하는 정렬 알고리즘이다. 시간 복잡도는 O(N^2)이다. <br>
예를들어 2, 3, 8, 9, 7, 1, 6, 5의 배열이 있다고 하자. 오름차순으로 정렬해야 할때 이때 기준 값인 key를 7로 잡는다. key와 9를 비교하고 key가 더 작으면 9를 key가 있던 위치로 바꾼다. 
key index값을 1 낮추고 8과 비교한다. 마찬가지로 key가 더 작으므로 8의 위치를 key가 있던 위치로 옮긴다. 이 반복을 앞에 있는 원소가 key보다 작을 때 까지 반복한다. <br>
위 과정의 하나의 반복이 끝나면 이번엔 key를 1로 잡고 반복한다. 이를 n번째 원소까지 반복한다.
```c
#include <iostream>
#include <vector>

using namespace std;

int main(){
    int n;
    vector<int> v;

    cin>>n;

    for(int i=0; i<n; i++){
        int e;
        cin >> e;
        v.push_back(e);
    }

    for(int i=1; i<n; i++){
        int key = v[i];
        int j = i - 1;
        while(j >= 0 && v[j] > key){
            v[j+1] = v[j];
            j--;
        }

        v[j+1] = key;
    }
    
    for(int i=0; i<n; i++)
        cout<<v[i]<<' ';


    return 0;
}
```


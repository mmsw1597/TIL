### 버블 정렬
가장 단순한 정렬 알고리즘으로 첫번째와 두번째를 비교, 두번째와 세번째를 비교 ... n-1번째와 n번째를 비교하여 값을 정렬하는 알고리즘이다.
코드는 간단하게 작성할 수 있지만 성능은 비효율적이다. 시간복잡도는 O(N^2)이다.<br>

```c
#include <iostream>
#include <vector>

using namespace std;

int main(){
    int n;
    cin>>n;
    vector<int> v;

    for(int i=0; i<n; i++){
        int e;
        cin>>e;
        v.push_back(e);
    }

    for(int i=0; i<n - 1; i++){
        for(int j=0; j<n - 1; j++){
            if(v[j] > v[j+1]){
                int temp = v[j];
                v[j] = v[j+1];
                v[j+1] = temp;
            }
        }
    }

    for(int i=0; i<n; i++)
        cout<<v[i]<<' ';

    return 0;
}
```

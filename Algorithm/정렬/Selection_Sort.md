### 선택정렬
일상적인 방법의 정렬 알고리즘으로 알려진 선택정렬이다. 시간 복잡도는 O(N^2)이며 오름차순 정렬 방법은 다음과 같다.<br>

1. 전체 값 중 가장 작은 값을 찾는다.
2. 해당 값을 맨 첫번째에 배치한다.
3. 첫번째 값을 제외한 가장 작은 값을 찾아서 두번째에 배치한다.
4. n-1번째까지 반복한다.
<br>

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
        int min = i;

        for(int j=i+1; j<n; j++){
            if(v[j] < v[min])
                min = j;
        }

        int temp = v[i];
        v[i] = v[min];
        v[min] = temp;
    }

    for(int i=0; i<n; i++)
        cout<<v[i]<<' ';
    
    return 0;
}
```

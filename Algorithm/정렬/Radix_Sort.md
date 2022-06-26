### 기수 정렬
조금 독특한 알고리즘 정렬으로 원소의 각 자릿수를 비교하여 정렬하는 알고리즘 기법이다. <br>
![image](https://user-images.githubusercontent.com/55936770/175822861-21e8b0ba-eca4-4eef-ad85-6a8ed0d64659.png) <br>

예를들어 보자 배열에는 세 자릿수의 정수가 나열되어 있는 상태이고 가장 낮은 자릿수 기준으로 숫자들을 정렬한다. 그 다음엔 2번째 자릿수를 기준으로 정렬하고 마지막엔 첫번째
자릿수를 기준으로 정렬하면 모든 원소가 정렬되는 것을 볼 수 있다.<br>
해당 알고리즘은 어느 상황에서 유용할까? 대답은 문자열로 이루어진 원소들을 사전 순으로 정렬하거나 전체 숫자 크기가 아닌 특정 자릿수를 기준으로 정렬할때 유용할 것이다.<br>
또한 원소의 개수보다 각 원소의 길이가 더 작다면 O(N^2)인 알고리즘보다 더 효율적이다. <br>
해당 알고리즘은 시간복잡도도 특이한데, 원소의 개수가 N개가 있고 원소중 가장 길이가 긴 원소의 길이를 k라고 하면 시간 복잡도는 O(kN)이 된다. 
```c
#include <iostream>
#include <vector>

using namespace std;

int get_degit(int num, int pos){
    for(int i=0; i<pos; i++)
        num/=10;

    return num % 10;
}

vector<int> solution(vector<int> v, int k){
    for(int pos = 0; pos<k; pos++){
        vector<vector<int>> arr(10);

        for(int i=0; i<v.size(); i++){
            int degit = get_degit(v[i], pos);
            arr[degit].push_back(v[i]); 
        }

        vector<int> new_v;

        for(int i=0; i<=9; i++){
            for(int j=0; j<arr[i].size(); j++)
                new_v.push_back(arr[i][j]);           
        }

        v = new_v;
    }

    return v;
}

int main(){
    int n;
    cin>>n;

    vector<int> v;
    int k = 1;

    for(int i=0; i<n; i++){
        int e, temp, o = 0;
        cin >> e;
        temp = e;

        while(temp > 0){
            temp /= 10;
            o++;
        }
        if(k < o)
            k = o;
        v.push_back(e);
    }

    v = solution(v, k);
    for(int i=0; i<n; i++)
        cout<<v[i]<<' ';

    return 0;
}
```

### 큐
대기줄을 떠올리면 된다. 선입 선출구조이며 FIFO라고 알려진다. 삽입은 맨 앞에서, 삭제는 맨 뒤에서 하는 구조이다. push, pop, empty, size, top 5가지 함수가 사용가능하다.

### 배열과 큐
큐의 경우 배열 맨 앞에서 삽입하고 맨뒤에서 삭제를 하면 맨 앞에서 삽입은 O(N)이 걸린다. 따라서 배열로는 큐를 구현하기에는 무리가 있다. 그러나 연결리스트를 사용하면
큐와 같이 O(1)안에 삽입/삭제가 가능하다.

### 요세푸스
원형 큐의 대표적인 예이다. 원형 큐란 맨 뒤의 요소와 맨 앞의 요소가 이어지는 구조다. 요세푸스는 N명이 원형으로 모여서 3번째 사람을 죽이는 방식의 예이고
3번째 원소를 pop하고 N번째 원소 다음은 1번째 원소로 돌아오는 방식이라고 보면 된다.

### C++ 큐 STL
```c
#include <queue>
#include <iostream>
#include <string>

using namespace std;

int main(){
    int n;
    cin>>n;

    queue<int> q;

    for(int i=0; i<n; i++){
        string str;
        cin>>str;

        if(str == "push"){
            int c;
            cin>>c;
            q.push(c);
        }
        else if(str=="pop"){
            cout<<q.front()<<'\n';
            q.pop();
        }
        else if(str=="size")
            cout<<q.size()<<'\n';
        else if(str == "empty")
            cout<<q.empty()<<'\n';
        else if(str == "front")
            cout<<q.front()<<'\n';
    }

    return 0;
}
```



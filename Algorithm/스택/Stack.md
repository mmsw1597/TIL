### 스택
데이터를 넣는 곳과 빠지는 곳의 위치가 같은 자료구조로서 LIFO 구조를 띄고 있다. push, pop, empty, size, top 5가지 함수를 사용가능하다.

### 활용
가장 대표적인 스택 활용 예로서 괄호의 배치가 올바른지 확인하는 알고리즘을 구현할 때 쓰인다. 열린 괄호가 들어오면 push를 하고 닫힌 괄호가 들어오면 pop을 해준다.
만약 닫힌 괄호가 입력되었는데 스택이 비어있거나, 모든 괄호를 처리했는데 스택이 비어있다면 올바르지 않은 괄호이다.<br>
다른 예로서는 재귀함수의 콜백 스택이 있다.

### 배열로 구현
배열에서 삽입/삭제는 O(N)의 시간이 걸린다. 배열을 만약 맨뒤에서 삽입과 삭제를 한다면 O(1)안에 수행이 가능하다. 이때 배열은 스택과 동일한 구조가 된다.

### C++ 스택 STL
```c
#include <stack>
#include <iostream>
#include <string>

using namespace std;

int main(){
    int n;
    cin>>n;
    stack<int> s;

    for(int i=0; i<n; i++){
        string str;
        cin>>str;

        if(str == "push"){
            int c;
            cin>>c;
            s.push(c);
        }
        else if(str == "pop"){
            cout<<s.top()<<'\n';
            s.pop();
        }
        else if(str == "size")
            cout<<s.size()<<'\n';
        else if(str == "empty")
            cout<<s.empty()<<'\n';
        else if(str == "top")
            cout<<s.top()<<'\n';
    }
}
```


### 덱
스택과 큐의 성질을 합친 자료구조로서 맨앞, 맨뒤에서 모두 삽입 삭제가 가능한 자료구조이다. 기능은 pop back, pop front, push back, push front, back, front, size, empty가 있다.

### C++ 덱 STL
```c
#include <deque>
#include <iostream>
#include <string>

using namespace std;

int main(){
    int n;
    cin>>n;

    deque<int> d;

    for(int i=0; i<n; i++){
        string str;
        cin>>str;

        if(str == "push_front"){
            int c;
            cin>>c;
            d.push_front(c);
        }
        else if(str == "push_back"){
            int c;
            cin>>c;
            d.push_back(c);
        }
        else if(str == "pop_front"){
            cout<<d.front()<<'\n';
            d.pop_front();
        }
        else if(str == "pop_back"){
            cout<<d.back()<<'\n';
            d.pop_back();
        }
        else if(str == "size"){
            cout<<d.size()<<'\n';
        }
        else if(str == "empty"){
            cout<<d.empty()<<'\n';
        }
        else if(str == "front"){
            cout<<d.front()<<'\n';
        }
        else if(str == "back"){
            cout<<d.back()<<'\n';
        }
    }

    return 0;
}
```

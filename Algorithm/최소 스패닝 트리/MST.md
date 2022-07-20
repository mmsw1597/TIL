### MST
MST란 그래프 내에서 최소한의 간선만을 사용하여 모든 정점을 이어준 트리이다. 트리라는 용어에 집중하자. 따라서 N개의 노드가 있다면 N-1개의 간선이 존재하고 사이클은 존재하면 안된다.
가중치가 없는 그래프에서는 최소한의 간선만 활용하면 되지만 가중치가 있다면 N-1개의 간선을 사용하되 비용도 최소가 되어야만 한다. 

### Union-Find
여러개의 원소가 있고, 여러개의 집합이 있다고 할 때, 특정 원소가 어떤 집합에 속해있는지 확인하고 특정 집합을 합쳐야 하는 일이 있다면 유용한 Union-Find 자료구조다. 
먼저 모든 노드가 연결되어 있지 않는 상황에서 시작하고 UF배열이 있다고 할 때 UF는 그룹번호를 뜻한다. 따라서 UF배열의 초기 값은 자기 자신이다. 즉 처음에는 모든 노드가 전부 다른
그룹에 속하게 된다. <br>
두 노드를 하나의 그룹으로 합치는 union()연산이 있다고 가정하자. 1->3 으로 연결한다면 UF[1]=3 을 실행하면 된다. 즉 union(1,3)은 1번이 3번에 연결되게 하는 연산이라고 가정하자.
이렇게 하고나면 그룹으로서의 의미보다 실제 노드가 현재 가리키고 있는 부모 노드의 번호의 의미가 된다. <br>
![image](https://user-images.githubusercontent.com/55936770/179969741-182c7f8c-fee7-4277-b008-259931f067b2.png)<br>
위 사진은 union(1,3), union(5,6)을 실행한 결과이다 이때 union(5,1)을 진행하면 어떻게 될까? 먼저 두 노드 모두 부모노드를 따라 올라 갈 수 있을 때 까지 계속 올라간다. 즉 루트노드까지
이동한다. 이 과정을 find()라고 하자. 위 예시에서 find(5) = 6이 나와야 하고 find(1)은 3이 나와야한다. 당연하지만 find(3)=3이다. 이렇게 되면 union(5,1)은 union(6,3)과 같아지게 되고
UF[6]=3을 연산한다. <br>
![image](https://user-images.githubusercontent.com/55936770/179970262-a3429384-83ea-485b-a254-338f392153ba.png)<br>
즉 위 예시에서 1, 3, 5, 6의 대표 번호는 모두 3번이 된다. 

### 유니온 파인드 의사코드
+ Find()
```c
function find(x)
  if uf[x] == x        // x가 루트 노드라면
    return x           // x 값을 반환합니다.
  return find(uf[x])   // x가 루트 노드가 아니라면, x의 부모인 uf[x]에서 더 탐색을 진행합니다.
  ```
+ union()
```c
function union(x, y)
  set X = find(x), Y = find(y)
  uf[X] = Y 
```

### union-find 개선
![image](https://user-images.githubusercontent.com/55936770/179970878-caf231a2-95fc-4e4e-aae5-9a2d8a6cc8d2.png)<br>
위와 같은 형식이면 9번에 대해 find호출 시 O(N)이라는 시간복잡도가 걸린다. 이렇게 되면 굳이 union-find를 쓸 필요없이 배열을 사용해도 시간복잡도가 같다. 이를 해결하기 위해서
find연산을 수행할 때마다 만약 조상노드를 찾는다면 후손의 부모노드를 모두 조상으로 바꾸는 방법이 있다.<br>
![image](https://user-images.githubusercontent.com/55936770/179971261-7bdd7ae3-c1cc-45a4-8104-7da142d37800.png)<br>
예를 들어 위와 같은 상황이라면 find(5)를 수행했을 때<br>
![image](https://user-images.githubusercontent.com/55936770/179971321-370f31bc-6582-4f29-9baf-8fe2336abec7.png)<br>
이렇게 바꾼다는 것이다. 이렇게 되면 union, find 함수 모두 O(lonN)시간 복잡도를 보장한다. 이 기법을 경로 압축이라고 부르며 해당 기법을 find함수에 적용한 것은 다음과 같다.
```c
function find(x)
  if uf[x] == x                 // x가 루트 노드라면
    return x                    // x 값을 반환합니다.
  set root_node = find(uf[x])   // x가 루트 노드가 아니라면, x의 부모인 uf[x]에서 더 탐색을 진행합니다.
  uf[x] = root_node             // 노드 x에 부모를 루트 노드로 설정해줍니다.
  return root_node              // 찾아낸 루트 노드를 반환합니다.
```









  
  





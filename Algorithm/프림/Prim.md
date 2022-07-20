### 프림 알고리즘
MST를 만드는 알고리즘 중 하나로 크루스컬과 다르게 프림 알고리즘은 한 지점에서 시작하여 확장을 진행하는 방법이다. 프림 알고리즘은 아무데서나 시작해도 상관없다. 한 정점에서 시작하여
간선 중 가중치가 가장 작은 간선을 고른다. 그러면 그 간선이 MST에 들어가게 되는 것이다. 이는 다익스트라 알고리즘과 매우 유사한데, 차이점이라면 prim은 단순히 당장 연결된 간선만 고려하면
된다는 것이다. 즉 다익스트라가 dist[v] 와 dist[u] + length(u,v)를 비교한다면 프림은 dist[v]와 length(u,v)만 비교하면 된다. <br>
![image](https://user-images.githubusercontent.com/55936770/179974856-8194538c-3d7b-494a-83c5-46327794c54e.png)<br>
가령 이런 그래프다 있다면<br>
![image](https://user-images.githubusercontent.com/55936770/179974910-13a80ace-4ee8-4396-9efc-baf76f5468fe.png)<br>
최종 MST는 초록색으로 칠해진 것이다.<br>

### 시간 복잡도
프림도 다익스트라와 유사하므로 시간복잡도는 우선순위 큐를 사용한다면 O(ElogV)가 되고 단순 for문을 사용한다면 O(V^2)이 된다.

### 의사코드
```c
function prim(graph)                          // 그래프와 시작점 정보가 주어집니다.
    set Q = Queue()                           // 우선순위 큐를 만들어줍니다.

    for each vertex in graph                  // 그래프에 있는 모든 노드들에 대해
        set dist[v] = INF                     // 초기값을 전부 아주 큰 값으로 설정해주고 
        Q.push(v)                             // 우선순위큐에 각 노드를 넣어줍니다.
    set source = |V|                          // 시작점을 임의로 마지막 노드로 설정합니다.
    set dist[source] = 0                      // 시작점 대해서만 dist 값을 0으로 초기화해줍니다.
    while Q is not empty                      // 우선순위 큐가 비어있지 않을 때까지 반복합니다.
        set u = vertex in Q with min dist     // 우선순위 큐에서 dist값이 가장 작은 노드를 선택합니다.
        Q.remove(u)                           // 우선순위 큐에서 해당 노드를 제거해줍니다.

        for each neighbor v of u              // u번 노드와 연결된 노드들을 전부 살펴보면서
            set alt = length(u, v)            // 간선 가중치를 살펴봅니다.
            if alt < dist[v]                  // 기존 dist값보다 더 alt값이 작다면
                set dist[v] = alt             // dist값을 갱신해줍니다.
```




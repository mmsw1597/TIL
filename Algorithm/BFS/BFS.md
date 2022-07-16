### 너비 우선 탐색
DFS와는 달리 이웃한 노드를 모두 방문하고 이후에 이웃 노드에서 부터 다시 이웃 노드를 순차적으로 방문하는 방식이다. 큐 자료구조를 통해 구현이 가능하다. DFS와 성능 차이는
크게 없으나 DFS가 재귀함수를 사용한다면 재귀함수로 인한 오버헤드로 인해 약간의 차이로 DFS가 느리다. 

### 의사코드
```c
function bfs(pos)
  seq Q = Queue
  Q.push(pos)
  visit(pos)
  while Q is not empty
    set node = Q.pop()
    for children of node
      if visited[child] == false
        visit(child) 
        Q.push(child)
```

### 최단거리
BFS는 그래프가 만약 간선의 가중치가 모두 동일하다면 한 정점에서 다른 정점으로의 최단거리를 구할 수 있는 확실한 알고리즘이다. 

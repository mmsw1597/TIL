### 깊이 우선 탐색
그래프의 모든 노드를 탐색 하는 방법 중 하나로 최대한 깊게 탐색한 후 더이상 깊이 도달할 수 없으면 되돌아가는 방식이다. 재귀함수를 이용하여 구현이 가능하다.
한번 방문한 노드는 다시 방문하지 않아야 하고 방문을 한 노드는 따로 저장을 해야 한다. 

### 의사 코드
```c
function dfs(pos)
  visit(pos)
  for children of pos
    if visited[pos] == false
      dfs(child)
```

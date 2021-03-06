### 플로이드 워셜 알고리즘
다익스트라는 특정 한 지점에서 다른 지점까지의 최단경로를 구했다. 그러나 모든 지점에서의 최단 경로를 구하려면 각 지점마다 다익스트라를 돌려야만 한다. 이 번거로움을 해결하는
알고리즘이 플로이드 워셜 알고리즘이다. 정점의 수를 V, 간선의 수를 E라고 할때, 다익스트라가 O(V^2) 또는 O(ElogV)가 걸렸고 이를 모든 지점에대해서 돌리면 O(V^3), O(EVlogV)가 된다.
간선의 수가 매우 많다면 E=V^2이 되고 이렇게 되면 O(V^3)알고리즘이 더 효율적이다. 이때 O(V^3) 시간복잡도를 갖는 알고리즘이 플로이드 워셜 알고리즘이다. <br>

플로이드 알고리즘은 다익스트라 알고리즘과 유사하다. 먼저 2차원 배열 V^2 크기의 배열을 선언하고 모두 매우 큰 값 INF로 초기화한다. 그리고 출발하여 제자리로 가는 값은 0으로 초기화한다.
그러고나서 그래프의 간선에 적혀있는 숫자를 배열내에 적어준다. 이렇게 한 뒤, 1번부터 N번까지 모든 쌍 i, j에 대해서 dp[i][j] > dp[i][N] + dp[N][j]를 만족한다면 dp[i][j]를 dp[i][N] + dp[N][j]
로 변경한다. 따라서 플로이드 알고리즘은 3중 for문을 사용하게 되는데, 정점의 수에 시간복잡도가 크게 좌우된다. 그러므로 정점의 수가 많거나, 특정 지점에 대해서만 최단 경로를 알고싶다면
다익스트라 알고리즘을, 정점의 수가 적거나, 모든 쌍에 대한 최단거리를 구해야 할때는 플로이드를 사용하자.

### 수도코드
``` c
function floyd(graph)
    set dist = |V| * |V| array initialized to INF  // 처음 dist 배열을 아주 큰 값인 INF로 초기화합니다.
    for each edge(u, v)                            // 주어진 그래프의 모든 간선에 대해
        dist[u][v] = length(u, v)                  // 각 간선의 가중치를 dist 배열에 적어줍니다.
    for k = 1 ... |V|                              // 확실하게 거쳐갈 정점을 1번부터 V번까지 순서대로 정의합니다.
        for i = 1 ... |V|                          // 고정된 k에 대해 모든 쌍 (i, j)를 살펴봅니다.
            for j = 1 ... |V|
                if dist[i][j] > dist[i][k] + dist[k][j]     // i에서 j로 가는 거리가 k를 경유해 가는 것이 더 좋다면
                    dist[i][j] = dist[i][k] + dist[k][j]    // dist[i][j]값을 갱신해줍니다.
    return dist
```

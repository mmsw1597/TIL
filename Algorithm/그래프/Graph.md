### 그래프
트리를 확장한 자료구조로 부모 관계가 없고 사이클이 존재해도 되는 자료구조다. 간선과 노드로 구성되며 간선에는 가중치가 존재할 수도 있다. 또한 모든 길을 양방향으로 이동할 수 있는
무방향 그래프와 한 쪽으로만 이어져 있는 방향 그래프가 존재한다. 특정 정점에 연결된 간선의 수를 차수라고 하며 방향 그래프에서는 진입, 진출 차수가 존재한다.

### 인접 행렬로 그래프 구현
2차원 배열로 그래프를 표현할 수 있는데, 정점의 수를 V라고 할때 V*V 2차원 배열을 만들어서 1번에서 2번으로 가는 간선이 존재하면 V[1][2]에 가중치를 삽입하는 방식이다.
공간복잡도는 V*V이고 특정 정점과 연결되어 있는 모든 정점을 확인하는 데에는 O(V)의 시간이 걸린다. 특정 I, J의 연결 유무를 확인하는 데에는 O(1)시간이 걸린다.

### 인접 리스트로 그래프 구현
연결리스트로 그래프를 표현하는 방법이다. 정점의 개수만큼 리스트를 만들고 1번에서 2번으로 가는 간선이 존재한다면 1번 리스트에 2번을 삽입하는 방식이다. 노드 개수를 V, 
간선 개수를 E라고 하면 공간복잡도는 O(V+E)이고 특정 정점과 연결되어있는 모든 정점을 확인하는 데에는 O(V의 차수)만큼 걸리고 특정 I, J의 연결 유무를 확인하는 데에는
O(min(I의 차수, J의 차수))이다. 일반적으로 행렬보다 공간복잡도는 적지만 특정 2개의 노드가 연결되어 있는지 확인하는 데에는 행렬보다 오래 걸린다.


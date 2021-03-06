### 이진트리
트리에서 자식의 수를 최대 2개로 제한한 트리를 이진 트리라고 한다.<br>
![image](https://user-images.githubusercontent.com/55936770/178144178-815c6cf9-70f1-4664-a8df-645ab30277e0.png)<br>
위 트리가 이진트리다. 이를 배열로 구현이 가능한데, i번째 노드의 왼쪽 자식은 i*2번째, 오른쪽 자식은 i*2+1번째 노드다. 부모노드는 i/2로 정의된다. 중간에 노드가 비어있다면
배열에도 비워놔야 한다.

### 탐색
이진트리는 재귀를 통해 크게 3가지로 탐색이 가능하다. 전위 탐색(Preorder Traversal), 중위 탐색(Inorder Traversal), 후위 탐색(Postorder Traversal)가 있다.<br>
![image](https://user-images.githubusercontent.com/55936770/178144306-ad8813f9-d018-48a1-80ff-5e28b7f91b1e.png)<br>
위 그래프를 각 3가지 방법으로 탐색해보자.

### 전위 탐색
부모-왼쪽 자식- 오른쪽 자식 순으로 탐색한다. 위 트리를 전위 탐색으로 방문하면 12543687순으로 방문한다.

### 중위 탐색
왼쪽 자식- 부모- 오른쪽 자식 순으로 탐색한다. 위 트리를 중위 탐색으로 방문하면 24516837순으로 방문한다.

### 후위 탐색
왼쪽 자식- 오른쪽 자식- 부모 순으로 탐색한다. 위 트리를 후위 탐색으로 방문하면 45286731순으로 방문한다.

### 트리 모양 유추
위 3가지 방법중 2가지만 알면 다른 하나의 탐색 순서를 알 수 있고, 트리 모양을 알아낼 수 있다. 예를 들어보자
+ 중위탐색: 1 8 7 5 4 2 3 6
+ 후위탐색: 1 7 8 5 2 6 3 4<br><br>
먼저 후위 탐색은 부모를 맨 후순위로 탐색하므로 맨 끝에 있는 4가 루트노드임을 알 수 있다. 4가 루트노드임을 아는 상태로 중위 탐색을 보면 4를 기준으로 왼쪽, 오른쪽 노드가
어떻게 나뉘는지 알아챌 수 있다. (1, 8, 7, 5 는 루트 기준 왼쪽, 2, 3, 6은 루트 기준 오른쪽) <br><br>
이제 왼쪽 서브 트리, 오른쪽 서브 트리 기준 루트 노드를 찾아보자. 후위탐색은 오른쪽을 왼쪽보다 후순위로 탐색하므로 4이전에 3이 오른쪽 서브 트리의 루트노드이다.
이를 인지한채로 중위 탐색으로 가면 2가 3의 왼쪽자식, 6이 3의 오른쪽 자식임을 알 수 있다.<br><br>
오른쪽 서브 트리를 분석하자. 2, 6, 3, 4를 제외한 가장 오른쪽에 있는 수 5가 왼쪽 서브 트리의 루트 노드이다. 이를 인지한채로 중위 탐색을 살펴보자 5를 기준으로 오른쪽에
이미 분석한 4가 있다. 따라서 5의 오른쪽 자식은 없다는 것을 알 수 있다.<br><br>
5의  서브트리에서 루트노드를 찾자. 5이전에 8이므로 8이 루트노드이다. 다시 중위 탐색으로 가면 1, 8, 7순으로 되어있고, 8의 왼쪽은 1, 오른쪽 자식은 7임을 알 수 있다.<br><br>
![image](https://user-images.githubusercontent.com/55936770/178144665-8b6df381-6baf-420f-b9b1-68131b794ac3.png)<br>
위 그래프가 트리의 전체 모습이다.






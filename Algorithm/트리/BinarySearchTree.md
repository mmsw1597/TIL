### 이진 탐색 트리
이진 트리에서 조건을 하나 더 추가하자. 왼쪽에 있는 노드들은 모두 부모보다 값이 작고, 오른쪽에 있는 노드는 모두 부모보다 값이 커야만 하는 조건을 추가하면
이진 탐색 트리가 된다. <br>
![image](https://user-images.githubusercontent.com/55936770/178144871-e1cd0f77-befc-43c9-8f8f-1b55ba1003c7.png)<br>
이진 탐색 트리의 예이다. 중요한점은 루트로 부터 왼쪽에 있는 서브 트리의 모든 노드는 루트보다 작아야 한다. (오른쪽도 마찬가지) 이진 탐색 트리를 간단하게 BST라고 하겠다.

### 탐색
BST에서 x값을 탐색한다고 가정하자. 루트에서 부터 시작하여 현재 노드가 x보다 크면 왼쪽으로, 작으면 오른쪽으로 이동하면 된다. 만약 x가 트리에 없다면 null 위치로 이동하게 된다.
```c
function bst_search(x){
  set node = bst.root;
  while(node != null && node.value != x){
    if(node.value > x)
      node = node.left;
    else
      node = node.right;
  }
  return node;
}
```
### 삽입
탐색 과정과 유사하게 null에 도달할 때 까지 계속 x를 아래로 이동시키며 null에 도달하면 그자리에 노드를 삽입한다. 이동하면서 지점의 부모 노드를 기억해야 하며
최종적으로 null위치의 부모를 알아야 한다. null에 도달했을 때, 3가지 방법으로 BST 구조를 완성한다.<br>
1. 트리에 노드가 전혀 없는 경우: 루트 노드에 삽입
2. 부모 노드보다 x가 더 작은 경우: 부모의 왼쪽에 삽입
3. 부모 노드보다 x가 더 큰 경우: 부모의 오른쪽에 삽입<br>
```c
function bst.insert(x)
    set node = bst.root          // root에서 시작합니다.
    set parent = bst.root        // parent도 root로 설정하고 시작합니다.

    while node != null           // node가 null이 되기 전까지 반복합니다.
        parent = node            // parent는 항상 node가 움직이기 직전의 위치로 갱신해줍니다. 
        if node.value > x        // node에 적혀있는 값이 x보다 크다면
            node = node.left     // 왼쪽 자식으로 이동해야 합니다. 
        else                     // node에 적혀있는 값이 x보다 작다면
            node = node.right    // 오른쪽 자식으로 이동해야 합니다.
    
    if parent == null            // Case 1. 비어있는 tree라면
        bst.root = node(x)       // root를 node(x)로 설정해줍니다.
    else if parent.value > x     // Case 2. parent에 적혀있는 값이 추가하려는 값 x보다 크다면
        parent.left = node(x)    // parent의 왼쪽에 node(x)를 넣어줍니다.
    else                         // Case 3. parent에 적혀있는 값이 추가하려는 값 x보다 작다면
        parent.right = node(x)   // parent의 오른쪽에 node(x)를 넣어줍니다.
```

### 삭제
삭제할 x값을 먼저 탐색한다. 탐색 후 3가지 경우의 수로 나뉜다.<br>
1. 값을 찾았을 때, 왼쪽 노드가 비어 있다면 오른쪽 서브트리를 위로 올려준다.
2. 값을 찾았을 때, 오른쪽 노드가 비어 있다면 왼쪽 서브트리를 위로 올려준다.
3. 값을 찾았을 때, 오른쪽, 왼쪽 모두 채워져 있다면 successor를 찾는다. 이때 successor는 현재 노드보다 더 크면서 가장 작은 값을 갖는 노드를 말한다. (상한) 이때 successor는
현재 노드의 오른쪽으로 한번 이동하고 왼쪽으로 null에 도달할 때 까지 내려가는 방식으로 이동하면 successor를 찾을 수 있다. successor를 찾고나서 successor와 x의 위치에
옮겨주고, successor의 오른쪽 자식을 원래 successor가 있던 위치로 올려주면 된다. 단, 이때 succssor가 x의 오른쪽 자식이라면 1번 case처럼 단순히 x의 오른쪽 노드를 위로
올려주면 된다.
```c
function bst.search(x)
    set node = bst.root                     
    while node != null and node.value != x 
        if node.value > x                
            node = node.left           
        else                               
            node = node.right           
    
    return node            

function bst.minimum(node)                  // node 하위 트리에서 최솟값을 구합니다.
    while node.left != null                 // node의 left가 null이 아니면 계속 내려갑니다.
        node = node.left
    return node                             // 최종 node의 위치를 반환합니다.

function bst.delete(x)                      // x를 찾아 삭제하는 함수입니다.
    set node = bst.search(x)                // x 값을 찾습니다.
    
    if node.left == null                    // Case 1. node의 왼쪽 자식이 비어있다면
        move(node.right, node)              // 오른쪽 자식을 위로 올려줍니다.
    else if node.right == null              // Case 2. node의 오른쪽 자식이 비어있다면
        move(node.left, node)               // 왼쪽 자식을 위로 올려줍니다.
    else                                    // Case 3. 왼쪽 오른쪽 자식이 모두 채워져있다면
        set succ = bst.minimum(node.right)  // 해당 노드의 successor를 구합니다.
                                            // 이는 현재 노드의 오른쪽 자식에서 시작하여 계속 왼쪽으로 내려가는 것을
                                            // 반복하면 가능합니다.
        if succ == node.right               // 만약 successor가 현재 노드의 오른쪽 자식이라면 
            move(node.right, node)          // 오른쪽 자식을 위로 올려줍니다.
        else                                // 그렇지 않은 일반적인 경우라면
            node.value = succ.value         // node의 값을 successor의 값으로 대체시켜준 뒤,
            move(succ.right, succ)          // successor의 오른쪽 자식을 위로 끌어올려줍니다.
```
### 균형 잡힌 이진 탐색 트리
BST에서 탐색, 삽입, 삭제의 시간 복잡도는 일반적으론 O(logN)이지만 최악의 경우는 O(N)이 걸린다. 이는 노드 N개가 있을 때, 높이가 N인 트리를 만들었을때 발생하며
이를 해결하기 위해 균형잡힌 BST를 만들어서 O(logN)시간을 보장하는 것이다. Red Black tree, AVL Tree가 예시이며 N개의 노드가 있을 때, 높이를 logN 으로 보장하는 트리임을 기억하자


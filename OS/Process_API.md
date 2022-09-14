## Process Creation
1. Parent process는 child process를 생성. 결과적으로 트리 형태의 프로세스를 형성한다.
2. child process는 자원이 필요하다. 이때 자원은 OS가 주거나 parent의 자원을 공유한다.
3. 부모와 자원을 모두 공유하거나, 일부분만 공유하거나, 공유하지 않을 수도 있다.
4. 실행은 부모와 병렬적으로 실행되거나 부모가 자식의 종료를 기다릴 수 도 있다.
5. fork를 하게되면 자식은 부모의 address space를 공유하고, exec를 하게되면 자식은 새로운 프로그램을 갖게된다.

## Process creation summary
1. OS 커널 내부에 PCB를 생성
2. 메모리 스페이스를 할당.
3. binary program을 로드
4. 프로그램 초기화.

## Fork vs execve
1. fork : 부모의 PCB를 복제, 메모리 스페이스 할당.
2. execve : fork 이후에 호출됨. disk로부터 프로그램을 load하고 초기화 작업 실행

## Process Termination
1. 일반적으로 마지막 명령문이 수행되면 OS에게 자기자신을 삭제해달라고 요청한다.
2. 종료되고 나면 부모 process에게 상태 값을 return한다.
3. 자식의 자원은 OS에 의해 반납된다.
4. 부모가 강제로 자식을 종료시킬수도 있다. (abort)

## fork
1. fork를 하게되고 따로 부가적인 처리를 하지 않으면 부모와 자식의 실행 순서는 불규칙적이다.
2. 이때 부모가 wait을 호출하면 무조건 자식의 종료를 기다리게 되고 실행 순서는 자식보다 늦다.
3. exec를 하게되면 새로운 프로그램을 실행하고 이때 exec를 실행한 process는 exec로 실행한 프로그램을 수행한 뒤 종료된다. 즉 exec 이후의 코드는 수행하지 않는다.

## redirection
결과를 파일 형태로 저장한다는 의미.

## 자투리
1. fork의 반환값은 0보다 작으면 에러, 0이면 자식 process, 자식 process의 pid면 부모이다.
2. wait 함수의 반환값은 자식의 pid이다.

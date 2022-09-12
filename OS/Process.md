## 가상화
하나의 CPU에 process는 여러 개일 수 있다. 각 process는 실행 할때 CPU가 필요하고 이때 각 프로세스마다 한 개의 CPU를 독점하여 사용하는 것처럼 환상을 심어주는 것이 가상화이다.

## 가상화를 구현하기위한 2가지 측면
1. 도구적 측면 : 가상화를 구현하기 위해 실제 구현하는 방법 ex) context switching
2. 지능적 측면 : 결정을 내릴 때 사용되는 알고리즘 ex) scheduling policy

## process란?
메모리에 있는 프로그램을 실행한 개념. 즉, 실행중인 프로그램

## process 구성요소
1. Memory (address space, codem data, stack, heap)
2. Registers (PC, Stack pointer)

## Time Sharing
특정 프로세스를 일정기간 실행하다가 다음 process로 옮기는 방법으로 다수의 process를 실행하는 방법. 가상화의 방법중 하나.

## Time slice
time sharing에서 일정기간의 시간을 말한다. 너무 길면 동시에 다수의 process가 실행되는 느낌이 들지 않게 되고 너무 짧으면 동시성은 확보되나 over head가 커지게 된다.

## Process 실행 과정
1. disk에 있는 program을 메모리에 적재한다.
2. 1번 과정을 load라고 부르고 이때 lazily하게 load한다. 즉, 실행 시, 필요한 파일을 모두 memory에 적재하는게 아닌, 그 순간 필요한 파일만 적재한다는 뜻.
3. 프로그램의 stack을 할당한다. stack엔 지역변수, 함수 매개변수, 반환 주소값이 포함된다.
4. 프로그램의 heap을 할당한다. 이는 동적 데이터를 저장하기 위해 사용된다. 동적이라는 뜻은 실행 도중에 메모리를 새로 할당한 것을 의미한다.
5. 기타 다른 초기화 작업을 수행한다. 예를들어 I/O setup의 경우 표준 입력(0), 출력(1), 에러(2)를 생성.
6. 프로그램 시작. CPU를 할당받게 된다.

## Process state
1. Running : CPU를 점유하고 있는 상태
2. Ready : CPU를 점유받기 위해 대기하는 상태. Queue에서 대기하고 있다.
3. Blocked : 잠시 다른 프로세스를 위해 block된 상태. 예를들어 I/O작업의 경우 CPU가 필요하지 않기 때문에 해당 시간동안 다른 process에게 CPU를 양보한다.

## Data Structure
OS는 다양한 정보를 저장(process list, register context)하기 위해 특별한 데이터 구조를 갖게된다. 대표적으로 PCB(process control block)가 있다.

## PCB
PCB는 각 process마다 존재하며 다양한 정보를 담고있다. CPU register, PID, PPID, Credentials(uid, gid) 등등을 포함한다.

## Context Switch
Process의 register값을 스위칭. 즉, 현재 process에서 실행할 process를 바꾼다는 의미. 바꾸기 위해서 반드시 이전 프로세스의 상태를 저장해야하고, 새로운 프로세스의 상태를 
불러와야 한다.

## Context Switch time
process를 변경하기 위해선 앞서 2가지 일을 수행해야 하고, 이 2가지 일을 할 때는 의미있는 일을 할 수 없다. 따라서 overhead라고 불린다. 이 시간은 하드웨어에 따라 좌우된다.







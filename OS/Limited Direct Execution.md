## 가상화를 효율적으로
1. Performance : 추가적인 overhead없이 가상화를 어떻게 수행할 수 있는지
2. Control : CPU 컨트롤을 유지하면서 프로세스를 어떻게 효율적으로 구동가능한지

## Direct Execution 문제점
1. 단순히 OS는 준비, 회수과정만 하고 개입을 안한다면 OS는 단지 library와 같다.
2. 하드웨어 접근이나, 추가적인 자원 접근에 대해 제한이 없음
3. 프로세스 수행 도중 switching을 할 수 없음. 

## Restricted Operation
1. 프로세스가 하드웨어를 직접 다르는 경우 제한이 필요.
2. 프로세스가 더 많은 자원에 대해 접근하려 할때 제한이 필요.
3. 이를 제한하기 위해 user mode와 kernel mode로 나누어 process를 제한한다.

## User mode
App이 하드웨어 자원에 대해 full access를 할 수 없는 상태.

## Kernel mode
OS가 machine에 대해 full access를 할 수 있는 상태.

## System Call
1. 자원에 대해 kernel을 통해 간접적으로 접근
2. file system 접근, process를 만들거나, 제거하거나, 다른 process와 소통하거나, 메모리를 할당하는 경우 system call이 필요.
3. System call 마다 번호가 할당되어 있음.
4. user의 코드는 register에 System call에 맞는 번호를 저장할 필요가 있음.

## Trap instruction
kernel mode로 전환하는 명령어.

## Return-from-trap instruction
user mode로 전환하는 명령어

## Trap
1. OS 내에 어떤 코드를 수행할지 trap이 어떻게 알 수 있을까?
2. trap table, 다른 말로 interrupt descriptor table이 존재함.
3. 발생한 interrupt에 대해 각각 실행할 코드를 저장함.
4. trap handler는 trap 명령어가 실행되면 OS 내의 코드가 실행되게 한다.

## Limited Direction Execution Protocol
1. OS : trap table 초기화
2. OS : user stack에는 매개변수 등을, kernel stack에는 reg/PC값을 저장. 
3. OS : return-from-trap
4. HW : kernel stack으로부터 register 불러오기, usremode로 jump
5. Program : System call (trap)
6. HW : kernel stack에 user code 어느위치에서 멈췄는지 저장.
7. OS: system call 수행. return-from-trap
8. HW : 아까 register에 저장한 값을 불러와서 그곳으로 jump
9. Program : return, trap
10. OS: Free memory of process

## Switching Process
1. Cooperative Approach : OS가 단순히 system call을 기다린다.
2. Non-Cooperative Approach : OS가 제어를 가지게 된다.

## Cooperative Approach
1. 일정 주기마다 process가 system call을 호출하여 자발적으로 CPU를 포기하게끔 만드는 방법.
2. illegal한 행동을 할 경우에도 CPU를 넘기는 것이 가능.
3. 만약 process가 무한 루프에 걸린다면 CPU를 받아올 방법이 없음. 강제 reboot 요구.

## Non-Cooperative Approach
1. timer interrupt를 쓰는 방법이 있음. OS가 자체적으로 타이머를 설정함.
2. 매 주기마다 timer가 process에게 interrupt를 걸게됨.
3. interrupt가 걸릴 경우 processs는 강제 중단되고, state를 저장하고, 사전에 정의된 OS내의 interrupt handler가 실행됨.
4. 결국 timer는 OS가 CPU를 받아올 수 있게 해준다.

## Context Switch
1. scheduler는 타이머가 만료됐을때 현재 processs를 계속 수행할지, 다른 process를 수행할지 결정을 내려야함.
2. 결정이 내려졌다면 OS는 context switch를 실행함.
3. Switch하기전 register 값들을 저장함. (PC, kernel stack pointer 등등)
4. 실행 예정인 process의 register 값들을 kernel stack으로 부터 불러옴
5. Switch kernel stack

## Concurrency 문제는?
1. interrupt/trap handling을 하다가 다른 interrupt가 발생한다면?
2. OS는 새로운 interrupt를 무시하거나 현재 처리중인 자원에 대해서 lock을 하고 다른 interrupt를 처리할 수 있다.
3. 추후 다른 페이지에서 다룰 예정.


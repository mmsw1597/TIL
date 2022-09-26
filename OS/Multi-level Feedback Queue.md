## CPU scheduler의 목표
1. turnaround time 최적화 : SJF, STCF (프로세스 당 걸리는 시간 예측이 필요)
2. Minimize response time for interactive work : RR (turnaround time은 안좋게 됨)
3. 위 두가지 목표를 달성하려면 프로세스의 prior knowledge가 필요하다.
4. 보통 이전의 결과를 저장하여 미래를 예측한다.

## MLFQ
1. 하나의 queue가 아닌 여려 개의 queue를 갖는 것을 말함.
2. 각 queue는 스케줄링 알고리즘, time slice값이 서로 다르다.
3. 보통 가장 먼저 마주하게 되는 queue가 우선순위가 높다.

## MLFQ: basic rule
1. 각 queue는 서로 다른 우선순위를 가짐.
2. 같은 queue 내에서는 RR 알고리즘으로 프로세스를 할당시킴.
3. 프로세스의 관찰된 경향으로 우선순위를 결정함.
4. 보통 대화식 프로세스, 즉 CPU를 짧게 점유하고 빠른 response time을 필요로 하는 process는 높은 우선순위를 가진다. (I/O intensive)
5. CPU intensive, 즉 CPU를 길게 점유하고 response time은 중요치 않은 process는 낮은 우선순위를 가진다.

## MLFQ : Change priority
1. 실행 도중에 우선순위를 바꿀 필요가 생긴다.
2. 기본적으로 process가 맨 처음 system에 들어왔을때 최고 우선순위를 갖게 한다. (정보를 모르기때문에 일단 높은 우선순위)
3. 만약 한 process가 time slice를 모두 소모한다면 우선순위를 낮추어 낮은 queue로 들어가게 한다.
4. 만약 time slice가 끝나기전에 I/O 작업 때문에 CPU를 양보한다면 해당 process는 우선순위를 그대로 유지한다. 

## MLFQ : 문제점
1. Starvation : 너무 많은 대화식 프로세스가 system상에 있다면 CPU intensive process는 CPU를 오랜시간 점유받지 못하게 되는 현상.
2. Game the scheduler : 예를들어 99%의 time slice를 소모한다음 I/O 작업으로 CPU를 양보한다면 해당 process는 우선순위가 그대로이므로 오랜시간 CPU를 잡아먹는다.
3. Change behavior : CPU가 본인으 특성을 CPU bound -> I/O bound로 도중에 바꿀수 있음.

## MLFQ : 해결법
1. 일정 주기가 지난뒤 모든 process를 최상위 queue로 이동시킨다.
2. I/O 작업에 time slice가 끝나기전 진입할 경우, 일정 할당량을 미리 정해두고 해당 할당량을 다 쓰게되면 우선순위를 낮춘다.

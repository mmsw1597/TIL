## CPU burst / I/O burst
1. CPU burst: process가 실행되는 상태.
2. I/O burst: I/O 작업이 실행되는 상태.
3. 일반적으로 I/O 위주의 process는 호출되는 빈도는 크지만 CPU burst time은 짧고, CPU 위주 process는 빈도수는 낮지만 burst time은 길다.

## CPU Scheduler
1. 실행 준비가 된 process 중 하나를 선택하는 기능. 이때 선택 기준은 알고리즘에 달렸다.
2. process가 running -> waiting (I/O request) 상태로 변할때 스케줄러는 결정을 내린다. 이때 process는 CPU를 자발적으로 반납.
3. process가 running -> ready (time slice expiration) 상태로 변할때 스케줄러는 결정을 내린다. 이때 process는 CPU를 강제로 반납.
4. process가 waiting -> ready (I/O complete) 상태로 변할때 스케줄러는 결정을 내린다. 이때 process는 강제로 상태 변환.
5. process가 terminate 될 때 스케줄러는 결정을내린다. 이때 process는 자발적으로 자원을 반납.

## Scheduing Criteria
1. Utilization : CPU를 가능하면 최대로 바쁘게. 노는 시간이 없도록.
2. Throughput : CPU가 단위시간당 가능한 많은 process를 처리하게.
3. Turnaround time : process 요청후 완료까지 걸리는 시간. 즉, 완료된 시간 - 도착 시간.
4. Waiting time : process가 queue에서 기다린 시간.
5. Response time : process가 요청 되고 실행까지 걸린 시간. 즉, 실행된 시간 - 도착 시간.
6. time에 대한 기준은 낮을 수록, 나머지는 높을 수록 좋다.
7. response time에 있어서 평균값보다는 편차를 줄이는것이 유리하다.

## Turnaround time
1. performance의 지표이다.
2. performance와 반비례하는 성향을 보이는 것은 공평성이다.

## FIFO
1. 먼저 들어온 process가 먼저 처리된다.
2. 문제점은 여러 process 중, 유독 오래걸리는 process가 가장 먼저 요청되면 전체적인 turnaround time이 급격하게 증가한다.
3. 이를 convoy effect (앞에 있는 process가 뒤의 process에게 영향을 주는 효과) 라고 한다.

## SJF
1. 짧게 걸리는 일을 먼저 처리하는 알고리즘.
2. FIFO의 문제점을 보완. 단, 미리 process가 각각 얼마나 걸리는지 알고 있어야함. (예측이 필요)
3. 문제점은 non-preemptive scheduler인 경우 오래 걸리는 process가 먼저 요청되고 이후 시간이 지난뒤에 다른 process가 요청되면 도중에 CPU를 뺏을 방법이 없음.

## STCF
1. SJF에 preemption을 더한 형태 즉, 도중에 CPU를 회수가 가능함.
2. 하나의 process가 실행되는 도중에 새로운 process가 도착하면 남아있는 일의 시간과 새로 들어온 일의 시간을 비교.
3. 이후 짧게 걸리는 일을 먼저 실행.

## 실행시간 예측.
1. 앞선 알고리즘들은 프로세스 실행 시간을 안다는 전제 하에 설계됨. 실제로는 정확하게 알 수 없으며 예측이 필요함.
2. 일반적으로 exponential averaging에 의해 예측됨.
3. 한 process가 과거에 소비했던 CPU burst time(t) 과 당시에 예측했던 값(e)을 토대로 현재 예측값을 결정. 
4. e(n+1) = at(n) + (1-a)e(n)
5. 위 식에서 a가 0이라는 것은 실제 측정 값을 고려하지 않는다는 것. 반대로 a가 1이라는 것은 오로지 실제 측정 값만 고려한다는 것.

## Response time
위에서 Turaround time을 위해 설계된 알고리즘들은 Response time에는 특별히 좋은 알고리즘은 아니다.

## Round Robin Scheduling
1. 각 process마다 우선순위를 두지 않고, 일정 시간만 CPU를 갖게하도록 하는 스케줄링 기법.
2. 그 일정시간을 time slice / time quantum 이라고 한다.
3. 물론 time slice의 길이는 timer-interrurpt period 길이보다 몇배는 더 커야한다.
4. 공평성을 지향하는 알고리즘. 그러나 performance와는 거리가 멀다.

## Time slice가 짧으면?
1. Time slice가 짧을수록 Response time은 짧아진다.
2. 대신 context switching 에 대한 비용이 매우 커진다.

## Time slice가 길면?
1. Time slice가 길수록 response time은 길어진다.
2. 대신 context switching에 대한 비용의 부담은 작아진다.

## I/O 작업에 대해
1. A라는 process가 완료까지 50의 시간이 걸리고 10마다 I/O 작업을 한다고 가정. 이후 I/O 작업이 없는 50이 걸리는 B가 요청됐다고 가정.
2. I/O 작업에는 CPU가 필요하지 않다.
3. I/O 작업에 CPU를 양보하지 않으면 response time, turnaround time 모두 손해를 본다.
4. 이때 I/O 작업에 들어가면 OS는 해당 process를 blocked 상태로 만들고, I/O 작업이 끝나면 ready 상태로 만든다.

## Media Access Control
1. 3명 이상의 사용자가 media를 사용할때 제어 방법.
2. Layer 2에서의 이야기.
3. 충돌 방지에 중점.

## 3가지 접근 방법.
1. Random Access : 랜덤, 경쟁 기반.
2. Controlled Access : 제어를 받아서 접근.
3. Channelization : 채널을 구분지어 접근.

## Random Access
1. 경쟁 기반. 즉, 어떤 station도 우선순위를 갖지 않고, control 받지 않는다.
2. 데이터를 전송할 station은 데이터를 보낼지 말지 결정하기 위해 protocol에 의해 정의된 절차를 사용한다.
3. 이때 결정은 medium의 상태에 의해 결정된다.

## ALOHA
1. 가장 오래된 Random access method.
2. wireless LAN 즉, radio를 위해 설계되었지만 유선 매체도 가능하다.
3. medium은 공유상태이기 때문에 잠재적인 충돌은 반드시 존재한다.
4. 충돌은 여러 station이 동시에 data를 보내려 할때 발생한다.

## ALOHA protocol
1. station이 보낼 데이터가 있으면 전송하는 것은 기본.
2. 단 하나의 channel만이 존재. 충돌 가능성이 다분.
3. 따라서 ALOHA protocol은 수신자로부터 acknowledgment에 의존하게 됨. 줄여서 ACK라고도 하는데, ACK는 데이터를 잘 받았을때 수신자가 발신자에게 보내는 신호.
4. 일정 시간동안 ACK가 도착하지 않으면 발신자는 보낸 data가 손실되었다고 가정하고 재전송을 하게됨.
5. (★)이때 일정 주기가 지나고 난 뒤, 바로 재전송하는 것이 아니라 random한 시간 이후에 재전송을 하게됨.
6. 왜냐하면 모든 station이 같은 주기를 가지면 한번 충돌이 일어나고 재전송을 동시에 하기 때문에 충돌이 반복되게됨.
7. 이때 random한 시간을 backoff time이라고 함.

## ALOHA protocol 절차
1. station이 frame을 전송. 이때 K(시도 횟수) = 0.
2. 전송후 Maximum propagation time의 2배(왕복시간)를 기다림. 즉 위에서 말한 일정 주기에 해당.
3. 해당 시간안에 ACK가 도착했다면 성공, 도착하지 않았다면 실패로 간주하고 재전송을 준비.
4. 이때 실패했다면 K에 1을 더함. 즉 K는 실패 횟수라고 봐도 됨.
5. K가 일정 횟수를 넘었는지 확인함. 일정 횟수를 넘었다면 중단하고 재전송을 포기. 그렇지 않다면 재전송.
6. 재전송을 한다면 난수 R를 선택함. 이때 R은 (0 ~ 2^K-1)중 정수 값을 고른다고 가정.
7. R x Maximum propagation time 또는 R x Average tranmission time 을 기다리고 이후 재전송.

## ALOHA protocol 부가 설명
1. time-out period는 maximum possible round-trip propagation delay임. 즉, 가장 멀리 떨어진 두 station 간의 왕복 신호 전파 시간.
2. backoff time은 난수이고 K에 의존함.
3. 실제 기다리는 시간의 공식은 binary exponential backoff에 의존. (2^K-1)
4. 충돌할때마다 난수의 범위는 커지게 됨.

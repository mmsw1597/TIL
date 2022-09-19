## NetWork Type 구분
1. 때때로 하나의 network를 다른 network로부터 구분하기는 혼란스럽고 어렵다.
2. 따라서 몇가지 기준이 필요하다. 대표적으로 size, 지리적 범위, 소유권 등이 있다.

## LAN
1. privately owned
2. 규모는 하나의 회사안에 host를 연결하는 정도.
3. LAN내에 있는 host는 id를 갖고 있음. (MAC 주소) 하나의 네트워크 안의 host를 구분짓는 것임 따라서 layer 2.
4. host끼리 주고받는 packet header 안에는 수신, 발신 host의 주소가 담겨있음.

## WAN
1. LAN에 비해 규모가 마을, 도시, 주, 전세계까지 가능할 정도로 훨씬 큼.
2. LAN은 host를 연결한다면 WAN은 connecting device(router, switch, modem)을 서로 연결함.
3. LAN은 조직에 의해 사적으로 소유됨. 반면 WAN은 일반적으로 통신사에 의해 구동되고 조직은 그것을 임대받음.
4. connecting device를 연결하므로 layer 3에 해당하고 IP address를 사용.

## circuit-switching
1. 전송기능은 있지만 저장기능은 없는 형태.
2. 매순간 full capacity로 전송한다는 보장이 없음. 따라서 비효율적.
3. 예를들어 4개의 host를 지원할때 host가 동시에 통신한다면 4개를 모두 지원해야하기 때문에 4개를 지원할 만큼 용량은 갖춰야함.
4. 그러나 4개의 host가 항상 동시에 통신하는 것은 아니기 때문에 이는 낭비라고 볼 수 있음.
5. 연속적인 통신을 제공함.

## packet-switching
1. 전송기능, 저장기능 모두 있는 형태.
2. 불연속적인 각각의 data packet을 교환하는 형태.
3. packet은 저장되었다가 나중에 보내질 수 도 있음.
4. packet을 저장할 queue, buffer가 필요함.
5. 항상 full capacity로 동작함.
6. queue가 꽉찼다면 이후 도착하는 packet은 폐기됨.

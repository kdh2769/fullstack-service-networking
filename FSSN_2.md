# 풀스택서비스네트워킹 2강 

## 기본적인 단어의 이해 

1. Message 

   Sender -> Receiver 사이에 정보를 주고받는다. 이 정보를 Message, Packet 이라 한다. 

2. Sender 

   Message를 보내는 프로그래밍이 가능한 컴퓨터 이다. 

3. Receiver 

   Message를 받는 프로그래밍이 가능한 컴퓨터 이다. 

4. Medium 

   Message 같은 정보들이 타고가는 물리적인 줄을 말한다. 

5. Protocol 

   Message를 보내고, 보내는 중, 받았을 때 해야하는 규약이다. 

## MAC 계층 (L2)

2계층엔 다양한 기술이 있다. 이중 Random-access protocols 를 살펴본다. 

- CSMA/CD (이더넷, 초고속 인터넷, 광랜 , IEEE 802.3)

  전통적으로 2계층에서 가장 많이 쓰는 유선 기술이다. (현재 HTTP 3, udp를 사용하는 경우, 한 Medium에 하나의 컴퓨터를 연결하는 경우는 해당 없다.)

  한 Medium엔 여러 컴퓨터가 연결되어 있다. A  컴퓨터에서 정보를 쐈고, 이 정보가 C 컴퓨터에 아직 도착하지 않았을때 C 컴퓨터가 정보를 쏘면 Collision 이 발생한다.  CSMA/CD 는 Carrier sense로 Collision이 감지되면 정보를 송출하는 행위를 멈춘다. 이때 Jamming signal을 송출해 확실하게 통신 Error 상태로 만든다. 그리고 함수를 돌려 Random 한 시간 이후 다시 정보를 송출한다. 

- CSMA/CA (무선랜, WIFI, IEEE 802.11)

  무선은 Collision Detect 하는 것이 어렵기 때문에 Collision Avoidance 하는 것이다.  

  데이터 송출을 희망하는 컴퓨터에서 RTS를 데이터를 수신받길 희망하는 컴퓨터를 비롯한 다른 컴퓨터에게 뿌린다. 수신받은 컴퓨터는 CTS 를 다른 컴퓨터에게 송출해서 두 컴퓨터간 데이터 전송에 참여할 수 없게 한다. 정보 교환이 끝나면 ACK를 송출해서 데이터 교환을 끝낸다. 

  무선랜은 사용자가 많으면 불능상태가 된다. 

- Flow and Error Control in MAC Layer 

  2계층은 Flow Control 과 Error Control을 담당한다 했다. 

  -> 통신은 Best-Effort 철학이다. Error 상황에서 최선을 다해보고 안되면 버린다. 

-  QoS 저하 

  이동통신을 이동하면서 사용하는 경우, 전자레인지 근처의 BT, WIFI, 천재지변, 케이블 손상등의 이유로 유/무선랜이 제속도를 내지 못할 수 있다.  

## Network 계층 (L3)

- Packetizing 

  데이터를 Source address, Destination address를 실어서 쪼갠다. 이를 Packet  이라 한다. 

- Routing and Fowarding 

  Sender -> Receiver 사이에서 줄잡이 역할을 수행한다. 이때 정보는 Packet 화 해서 보낸다. Router 내부에는 버퍼가 있지만 트래픽이 많이 오거나, Router 소프트웨어에 문제가 생긴다면 데이터 손실이 발생할 수 있다. 

  IP (Internet) Network Layer를 사용한다면 Router 마다 Packet 을 어디로 보낼지 결정한다. 이때 Packet 도착 순서가 바뀔 수 있다. 이는 4계층에서 바로 잡아준다. 

  만약 Error 검출 복구가 필요 없다면 ? TCP 말고 UDP 를 쓸 수 도 있다. 

- Forwarding process in a router 

  Router 는 Port 구멍으로 Packet을 송수신한다. 이때 Packet 의 Destination address를 어떤 Port 번호로 송신했는지 기록한 것을 Forwarding table 이라 한다. 

- IPv4 Address

  IP의 4번째 버전으로 주소를 32bit 로 만들었다. 

  Binary ,Dotted decimanl, Hexadecimal 주소를 사용한다. 

- Domain Name

  우리는 어떤 웹사이트에 접속할때 https://www.domain-name.com  이렇게 친다. IP 주소를 검색하지 않는다. 

- Domain Name System (DNS)

  Domain name 을 IP 주소로 바꿔주는 시스템이 DNS이다.  DNS resolver 가 DNS 서버에 접속해서 도메인을 주소로 바꿔준다.  

  하지만 DNS서버 접속 시간이 오래 걸리기 때문에 미리 불러올 수도 있다. 

  DNS 까진 아니더라도 간단하게 Name System을 만들어서  서로 접속할 수 있다. 

- Dynamic Host Configuration Protocol (DHCP)

  IP는 한정된 자원이다. 

  그래서 한정된 IP주소를 나눠쓰기 위해 DHCP Server에서 이를 관리한다. 원래 Public IP를 관리했지만 Private IP를 관리할때도 사용한다. 

  1. NAT 

     Private IP를 Public IP로 매핑시켜야한다. 즉 네트웍 주소를 바꿔준다. 

  2. PAT

     4계층에서 해당하는 프로그램 주소로 바꿔준다. 

  3. Private IP

     특정 집단 내부에서만 의미가 있는 주소다. 

  4. Public IP 

     전세계 어느곳에서도 의미가 있는 주소다.

  내가 서버내에서 네트워킹하는지, NAT/PAT 밖의 컴퓨터와 통신해야하는지 보고 프로그래밍 해야한다. 

  또한 IP Addresss는 언제든 바뀔 수 있기 때문에 주소가지고 프로그래밍을 하는 것을 지양해야 한다 . 


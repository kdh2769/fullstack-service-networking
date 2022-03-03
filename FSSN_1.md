# 풀스택네트워킹 1강 

 ## 컴퓨터 네트워크 개요 

- What is Computer 

  논리적으로 구현한 소프트웨어가 동작할 수 있는 장치. 소프트웨어가 들어갈 수 없다면 컴퓨터가 아니다. 

  그래서 현재 컴퓨터의 정의에 해당한 장치는 무수히 많다. 외형은 상관없다. 장치가 있고 소프트웨어가 동작하면 된다. 

- Categoris of Networks

  추상적 의미에서 Network 의 범위로 구분한다. 

  1. Local Area Networks. (LAN)

     LAN은 유/무선 혹은 유선의 의미로 쓸 수 있다.  Peer - to - Peer 의 경우 LAN에 해당하고, HTTP 는 MAN, WAN 에 속한다. 

     LAN의 범위는 같은 방에 있는 여러 컴퓨터, 혹은 같은 건물의 여러 방을 연결한 경우, 혹은 **소유권자가 동일**한 캠퍼스 속의 여러 건물 안에 있는 컴퓨터를 연결한 경우다. 

  2. Metropolitan Area Network (MAN)

     다양한 LAN이 묶여 도시 단위의 규모가 되면 MAN 이 된다. 

  3. Wide Area Network (WAN)

     WAN은 의미가 사뭇 다르다. LAN, MAN은 다른 네트웍과 통신하기 위해서 줄이 필요할 것인데 이 줄의 명칭이 WAN 이다. 

## OSI 7 계층 개요 

1. Physical Layer 

   컴퓨터간 정보를 0과 1로 , 유/무선으로 전달하는 층이다. 

2. Data Link Layer 

   Physical Layer의 0과 1에서 발생한 에러 검출, Flow Control 담당하는 층이다. 

3. Network Layer

   Network Layer 컴퓨터간 정보가 이동할 때 그 속에는 수많은 컴퓨터와 줄들하게 되는데 이를 잘 관제하는 층이다. 이를 Routing 이라 한다. 

4. Transport Layer 

   멀리 떨어진 컴퓨터 사이에서 발생한 Error Control을 담당한다. 

   -> Data Link 층에선 0,1 정보 이동시에 발생한 그 에러에만 국한된 에러 컨트롤이다.  

   ---

   

5. Session Layer 

   Authentication, Permission, Session restoration. 

   -> Zoom 을 예시로 본다면 사용자에게 권한을 가진다 (Authentication), 이를 허가할 수 있고 (Permission), 영상 송수신간에 Session에 문제가 생기면 복구하는 기능을 하는 층이다. 인증을 담당한다고 생각하면 되겠다. 

6. Presentation Layer 

   사용하는 Application에 압축, 암호화가 사용된다면 이 층이 담당한다. 

7. Application Layer 

   서비스의 최종 인터페이스를 제공하는 층이다. 

2, 3, 4 층은 운영체제에 들어가기 때문에 개선에 어려움이 있다. 5, 6, 7 은 Application에서 이뤄지니 변경이 용이하다. Socket Programming 4계층에 해당하고 HTTP 는 Application 층에 해당하고 ZeroMQ 는 Application층, 필효시 4계층에서 동작할 수 있다. 

- Router 

  7계층이 전부 있는것이 아닌 3계층으로 구성된 장비다. 컴퓨터간 정보가 오고갈때 그 줄들에 붙어서 길잡이 역할을 한다. IP 기술을 사용한다. 

  -> TCP/UDP 기술은 4계층, IP 는 3계층 소프트웨어다. 

- Simplified Model for Internet Service and Network 

  사실 5, 6, 7 계층이란 Application 하나가 다 하고 있기에 이를 통합해서 볼 수 있는 것이다. 

- Summary 

  OSI는 Open Systems Interconnection model의 약자로 모든 개방형 컴퓨터의 통신을 하기 위한 표준이다. 

-  Layering Operation Concept 

  OSI 전체 층에서 Data는 위에서 아래로, 아래서 위로 올라간다.

  층마다 Data를 받았을때, 내보낼때 해야하는 Protocol 이 있다. 내 계층에서  이를 PDU라 하고 윗/밑 층에 이를 보낼땐 SDU라 한다.

## 패러다임의 변화 

하드웨어 중심인 전통적인 네트워크 입장에선 OSI 7 Layer가 잘 동작했지만 TCP / IP 에 한계가 들어났다. 

현재의 네트워킹은 Application 계층에서 운영체제에 상관없이 유연하게 만들어진다. 

즉 네트워크를 엮은 컴퓨터 자체에 관심이 있기 보단 **네트워킹** 이라는 소프트웨어를 필두로 관심이 변한다. 

##  Linux Foundation의 이해 

어마어마하게 많은 오픈소스 프로젝트를 담당한다. Linux는 그저 하나의 프로젝트일 뿐이다. 




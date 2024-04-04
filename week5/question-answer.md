# 📌 네트워크 레이어

## 📎 면접 예상 질문

### IP주소에 대해서 설명해주세요.

인터넷에 연결된 각 기기를 구별하기 위해 사용되는 고유한 번호이다.

### IPV4와 IPV6는 어떤 차이점이 있을까요?

IPv4: 32비트로 구성된 IP 주소로, 대략 43억 개의 고유한 주소를 생성할 수 있다. IPv4 주소는 4개의 0~255 사이의 숫자로 이루어져 있으며, 각 숫자는 점(.)으로 구분된다. 예) 192.168.0.1

IPv6: 128비트로 구성된 IP 주소로, 거의 무한한 수의 고유한 주소를 생성할 수 있다. IPv6 주소는 8개의 4자리 16진수로 이루어져 있으며, 각 16진수는 콜론(:)으로 구분된다. 예) 2001:0db8:85a3:0000:0000:8a2e:0370:7334

### 서브넷과 서브넷 마스크에 대해 설명해주세요.

서브넷 마스크의 형태는 IP주소와 똑같이 32bit의 2진수로 되어 있으며, `8bit(1byte)`마다 `.(dot)`으로 구분하고 있다. 즉, IP와 똑같은 OOO.OOO.OOO.OOO의 모습을 가지고 있다. 그러나 형태가 똑같다고 하여서 역할을 혼동하면 안 된다. **형태가 똑같은 이유는 IP주소와 서브넷 마스크를 AND 연산하기 해서 네트워크 주소를 만들기 위해서이다.**

**IP주소 뒤에 붙은 `/24` 같은 것들은 서브넷 마스크의 bit 수를 의미**한다.

> 왜 사용?
> 
> 
> IP 주소 클래스를 이용하여 IP 주소의 네트워크 영역과 호스트 영역을 나누는 것에는 한계점이 존재한다. **결론부터 말하자면 자원의 낭비가 심하다는 것이다**. **따라서 적절하게 IP 주소 영역을 나누는 기술이 필요하였다.**
> 

### 라우팅이 뭘까요?

라우팅: IP 주소는 네트워크 상에서 데이터 패킷의 경로를 결정하는 데 사용된다. 라우터는 IP 주소를 통해 패킷이 어느 기기로 가야 하는지를 판단하고, 최적의 경로를 찾아 전송한다.

### Public IP와 Private IP 차이는 뭘까요?

Public IP: **ISP(인터넷 서비스 공급자)가 제공하는 IP 주소, 전세계에서 유일한 IP 주소를 갖는다. 공인 IP 주소가 외부에 공개되어 있기에 인터넷에 연결된 다른 PC로부터의 접근이 가능하다.** 

Private IP: **일반 가정이나 회사 내 등에 할당된 네트워크**의 IP 주소, IPv4의 주소부족으로 인해 서브넷팅된 IP이기 때문에 라우터에 의해 로컬 네트워크상의 PC 나 장치에 할당된다.

`Public IP`는 인터넷 상에서 유일하고 공개되어 있기 때문에 인터넷에 연결된 다른 장치와 통신할 수 있습니다. `Private IP`는 인터넷 상에서 고유하지 않고 비공개되어 있기 때문에 인터넷에 연결된 다른 장치와 통신할 수 없습니다.

> **Public IP와 Private IP가 필요한 이유**
> 
> 
> `Public IP`
> 
> Public IP 는 인터넷 상에서 유일하고, 인터넷을 통해 액세스 할 수 있습니다. 예를 들어, 웹사이트를 운영하는 서버는 Public IP 를 가지고 있습니다. 이 주소를 통해 다른 장치가 웹사이트에 접속할 수 있게 됩니다.
> 
> `Private IP`
> 
> Private IP가 필요한 이유는 Public **IP가 부족하기 때문**입니다.
> 
> Public IP는 IPv4라는 체계로 만들어졌는데, 이 체계로는 약 43억 개의 주소만 생성할 수 있습니다. 그런데 전 세계적으로 네트워크 장치가 이보다 훨씬 많습니다. 그래서 **하나의 Public IP로 여러 개의 Private IP를 관리하는 방식을 사용**합니다. (라우터-1개의 Public IP, 라우터에 연결된 개인 PC-Private IP, 포트로 구분)
> 

### 라우팅 프로토콜에 대해서 설명해주세요.

**`정적라우팅(Static routing)`: 관리자에 의해 Routing Table이 유지/관리 되는 기법,** 라우팅 테이블을 교환하지 않고 라우팅이 가능하기 때문에 네트워크 대역폭을 절약할 수 있다. 또한 외부에 자신의 경로를 알리지 않기 때문에 보안에도 강하다. 하지만 경로에 문제가 생길 경우 대처하기 어렵다는 단점이 있다.

**`동적라우팅(Dynamic routing)`: 라우팅 프로토콜에 의해 자동으로 라우팅 테이블을 구성하는 기법,** 자동으로 경로가 결정되는 프로토콜이다. 라우터가 판단하여 가장 효율적인 방법으로 패킷을 전송시키는 방법이다.

- RIP: 최소 Hop count를 파악하여 라우팅하는 프로토콜이다. distance vector 알고리즘 사용, 소규모 네트워크에서 사용. 경로의 네트워크 속도는 판단하지 않는다.
- BGP:  외부 라우팅 프로토콜로(EGP) AS(관리 도메인)와 AS간에 사용되는 라우팅 프로토콜, distance vector 알고리즘 사용
    - **특정 AS에 존재하는 특정 IP 주소를 다른 AS들에게 소문내서 서로를 연결시키는 과정**
    - 특정 AS에 접근하기 위한 길이 여러개인 경우: **Hot Potato Routing** 방식을 채택,  무조건 Next-Hop이 짧은 link를 선택한다.
- OSRF: 최저 COST(최저 시간) 경로를 최적 라우팅 경로로 결정, 다익스트라 알고리즘 사용, RIP가 30초마다 업데이트 되어 정보를 전송시키는 반면, OSPF는 링크에 상태변화가 있을 시에 즉각적으로 Flooding을 해주어 컨버전스 타임이 매우 빠르다.

### IP는 어떻게 할당될까요?

**정적 할당**은 IP 주소를 고정적으로 사용하고 싶을 때 유용합니다. 예를 들어, 웹 서버나 프린터와 같이 항상 같은 IP 주소로 접속해야 하는 장치에는 정적 할당을 사용합니다.

**동적 할당**을 위해서는 `DHCP`라는 프로토콜을 사용합니다.

`DHCP 서버`는 네트워크에 연결된 장치들에게 IP 주소를 할당하고 관리하는 역할을 합니다. `DHCP 서버`는 일반적으로 공유기나 라우터에 내장되어 있습니다.

1. `Discover`: 장치가 부팅되면서 네트워크에 접속하면 IP 주소가 필요하다는 메시지를 전송합니다.
2. `Offer`: DHCP 서버가 장치에게 사용 가능한 IP 주소와 관련된 정보를 제안하는 메시지를 전송합니다.
3. `Request`: 장치가 DHCP 서버가 제안한 IP 주소와 관련된 정보를 수락하겠다는 메시지를 전송합니다.
4. `Acknowledge`: DHCP 서버가 장치에게 IP 주소와 관련된 정보를 확정하고 확인하는 메시지를 전송합니다.

이때 `DHCP 서버`는 장치에게 IP 주소뿐만 아니라 서브넷 마스크, 기본 게이트웨이, DNS 서버 등의 정보도 함께 제공합니다. 또한 `DHCP 서버`는 장치에게 IP 주소를 사용할 수 있는 기간인 임대 시간도 지정합니다. 임대 시간이 만료되기 전에 장치가 DHCP 서버와 통신하여 IP 주소를 갱신하거나 반납할 수 있습니다.

### NAT가 뭘까요?

Private IP --(NAT)--> Public IP

Private IP를 Public IP로 변환하는 기술이다.

### ICMP가 뭘까요?

인터넷 제어 메시지 프로토콜로 오류 메세지를 전송받는 데 주로 쓰인다. 예를 들어, 네트워크에 연결된 장치가 응답하지 않거나, 목적지에 도달할 수 없거나, 패킷이 손실되거나 지연되는 경우에 `ICMP 메시지`가 생성되고 전송된다.

 **ICMP 프로토콜은 Network 계층에 속하며 IP 프로토콜과 같이 사용한다**

## 참조

https://m.blog.naver.com/wjw1225/223099790901

[https://velog.io/@hidaehyunlee/공인Public-사설Private-IP의-차이점](https://velog.io/@hidaehyunlee/%EA%B3%B5%EC%9D%B8Public-%EC%82%AC%EC%84%A4Private-IP%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

[https://velog.io/@yoonuk/네트워크-Public-IP와-Private-IP](https://velog.io/@yoonuk/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-Public-IP%EC%99%80-Private-IP)

[https://velog.io/@jh8579/NginxMysql-설정에-private-IP-or-public-IP](https://velog.io/@jh8579/NginxMysql-%EC%84%A4%EC%A0%95%EC%97%90-private-IP-or-public-IP)

[https://velog.io/@yoonuk/네트워크-IP가-할당되는-방법](https://velog.io/@yoonuk/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-IP%EA%B0%80-%ED%95%A0%EB%8B%B9%EB%90%98%EB%8A%94-%EB%B0%A9%EB%B2%95)

https://ddongwon.tistory.com/97

[https://velog.io/@yoonuk/네트워크-ICMP](https://velog.io/@yoonuk/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-ICMP)

[https://velog.io/@hidaehyunlee/서브넷팅subnetting으로-네크워크를-효율적으로-관리하자](https://velog.io/@hidaehyunlee/%EC%84%9C%EB%B8%8C%EB%84%B7%ED%8C%85subnetting%EC%9C%BC%EB%A1%9C-%EB%84%A4%ED%81%AC%EC%9B%8C%ED%81%AC%EB%A5%BC-%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9C%BC%EB%A1%9C-%EA%B4%80%EB%A6%AC%ED%95%98%EC%9E%90)

[https://velog.io/@hidaehyunlee/IP-Subnet서브넷이란](https://velog.io/@hidaehyunlee/IP-Subnet%EC%84%9C%EB%B8%8C%EB%84%B7%EC%9D%B4%EB%9E%80)

[https://velog.io/@sangmin1998/네트워크-서브넷Subnet-개념](https://velog.io/@sangmin1998/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%84%9C%EB%B8%8C%EB%84%B7Subnet-%EA%B0%9C%EB%85%90)

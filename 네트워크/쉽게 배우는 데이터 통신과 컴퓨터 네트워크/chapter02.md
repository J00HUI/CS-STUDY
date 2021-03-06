### 🔆 Preview  
전화 시스템은 데이터 통신을 위한 프로토콜의 동작 원리를 이해하는 데 많은 도움이 된다.   
전화 시스템에서는 전화를 거는 사람(송신자)와 받는 사람(수신자)의 합의를 통해 연결을 설정한다.   
데이터 전송 단계인 통화 과정에서는 묵시적인 규칙에 따라 대화를 주고 받는 일련의 절차가 진행된다.   
양쪽이 동시에 말할 수 있는 양방향 통신 기능을 지원하지만, 실제로 두 사람이 동시에 말하는 경우는 거의 없고, 느낌이나 말의 내용 등에 따라 번갈아가며 대화한다.   
상대방이 한 말을 이해하지 못했거나 제대로 듣지 못한 경우에는 다시 묻는 방식을 통하여 오류를 바로 잡기도 한다.   

네트워크에서 데이터 전송 원리도 이와 비슷하다.   
통신 프로토콜에서 중점적으로 다루는 내용은 데이터 전송 오류와 속도 조절, 데이터의 전달 경로를 조절하는 라우팅 기능이다.   
전화 시스템에서 사람들이 무의식적으로 행하는 통화 기법이 통신 프로토콜 설계 과정에 그대로 반영되어 있다.   

인터넷의 동작 원리를 이해하려면, **계층 구조** 로 설계된 OSI 7계층 모델에 대한 학습이 선행되어야 한다.   
특히, 모듈화 설계 개념의 원리와 상하위 계층의 역할 분담에 대한 학습을 통하여, 각 프로토콜의 역할을 이해해야 한다.   
인터넷에서 사용하는 전송 프로토콜인 TCP, UDP, IP 프로토콜은 계층 구조 모델의 원리에 따라 설계되었으며, 기타 제어 프로토콜 및 전송 프로토콜의 관계도 동일한 원리에 따라 설계되었다.   

2장에서는 OSI 7계층 모델의 기본 원리인 **계층 구조의 개념** 에 대하여 설명한다.   
상하위 계층의 역할 분담에 따른 모듈화 설계는 복잡한 시스템을 단순하게 해준다.   
`7계층 모델은 이러한 원리에 따라 네트워크의 기능을 7개의 계층으로 나누어 설계한 표준안이다.`   
인터넷의 구조가 7계층 모델의 게층 구조와 어떤 관계가 있는지, 주요 프로토콜인 TCP/IP는 어떻게 구성되어 있는지 살펴본다.   
</br>

### 💎 01 계층 구조의 개념
네트워크에 연결된 시스템이 통신하려면, 정해진 규칙에 따라 데이터를 주고받아야 하는데, 이러한 일련의 규칙을 프로토콜(protocol)이라 한다.   
프로토콜의 동작 과정은 전송 오류율, 데이터 전달 경로, 전송 속도 등 다양한 외부 요인의 영향을 받는다.   
따라서 적절한 대응 방안을 마련해 효율적으로 관리해야 하는데, 프로토콜의 설계 과정은 모듈(module)화를 통하여 이루어진다.   
이렇게 함으로써 사용자에게 더 편리하고 간편한 통신 기능을 제공할 수 있다.   

### 1. 계층적 모듈 구조
일반적으로 복잡하고 큰 시스템의 기능은 특정 단위의 모듈로 나누어 설계한다.   
모듈은 독립적으로 동작하면서도 상호 유기적으로 통합될 수 있어야 한다.   
그러므로 모듈 사이에는 적절한 인터페이스가 필요하다.   

### 1.1 모듈화
컴퓨터 하드웨어는 CPU, 메모리, 하드디스크, LAN 카드(local area network card, 와이파이 수신기) 등과 같은 작은 부품들이 모여 하나의 시스템을 구성한다.   
복잡한 시스템을 기능별로 모듈화하면 시스템 구조가 단순해져서 전체 시스템을 이해하기 쉽다.   
또한 각 단위 모듈이 독립적인 기능을 수행하기 때문에, 고장이나 업그레이드 등의 상황에 손쉽게 대처할 수 있다.   

소프트웨어 측면에서 보면, 일반 프로그래밍 언어에서는 함수 개념을 사용해 전체 프로그램을 모듈화할 수 있다.   
함수별로 특정 기능을 독립적으로 수행하도록 함으로써, 각 함수가 개별적으로 설계되고 구현된다는 장점이 있다.   
함수 사이의 인터페이스는 함수의 매개변수에 의해서만 이루어지므로, 전체 시스템을 이해하기가 훨씬 쉽다.   

그림은 시스템 모듈화의 장점을 보여준다.   

<img src="https://user-images.githubusercontent.com/83942393/128332259-5f93af3a-750f-498c-adf7-856bdd6f64de.png" width="60%" height="60%"></img></br>

(a)처럼 전체 시스템을 기능에 따라 세 부분으로 나누어 설계할 수 있는데, 이때 각 모듈은 유기적으로 연결되어야 한다.   
```
B 모듈은 A 모듈과 곡선 모양의 인터페이스로 연결되고, C 모듈과는 톱니 모양의 인터페이스로 연결된다.
A와 C 모듈은 직접 연결되는 인터페이스가 없으며, B 모듈을 통해 간접적인 관계를 유지한다.
```
</br>

* 그림처럼 시스템을 모듈화하지 않았다면, 
* 한 부분만 고장 나도 전체 시스템을 교체해야 한다.
* 반면, 모듈화하면 (b)처럼 오류가 발생한 B 모듈만 교체해서 버전 2로 대체할 수 있다.
* (c)처럼 성능이나 기능을 개선해 버전 3으로 교체할 수도 있다.
* 이때 모듈 내부의 처리 과정은 임의의로 개선할 수 있으나, A와 C 모듈과의 인터페이스는 동일하게 유지해야 전체 시스템 동작에 영향을 주지 않는다.
</br>

### 1.2 계층 구조
분할된 모듈들은 협력 관계를 유지하면서 유기적으로 동작한다.   
대부분의 모듈 구조에서는 특정 모듈이 다른 모듈에 서비스를 제공하는 형식의 계층 구조를 이룬다.   
네트워크에서도 독립적인 고유 기능을 수행하는 모듈들이 상하위의 계층 구조로 연결되어 동작한다.   

<img src="https://user-images.githubusercontent.com/83942393/128333012-8b59e4d9-3715-4fd2-9bbd-8ced108e856d.png" width="25%" height="25%"></img></br>
(1) 계층 구조는 그림처럼 상위 계층이 하위 계층에 특정 서비스를 요청하는 방식으로 동작한다.   
(2) 요청을 받은 하위 계층은 해당 서비스를 실행하여 그 결과를 상위 계층에 돌려준다.   

하위 계층의 실행 결과는 상위 계층에 결과 값을 직접 전달하는 방식이 될 수도 있고, 주변 환경값을 변경하는 부수 효과(side effect) 방식일 수도 있다.   
```
자동차의 경우를 예로 들어보자.
운전자가 자동차의 속도를 줄이려면, 브레이크를 밟아야 하고, 브레이크를 누르는 정도에 따라 속도가 줄어든다. (부수 효과)
이 구조에서 운전자는 상위 계층에 해당되며, 자동차 내부에서 속도를 줄이는 기능은 하위 계층의 모듈이 된다.
운전자와 감속 모듈 사이에는 브레이크라는 인터페이스가 존재한다.
```
</br>

모듈화된 계층 구조 프로토콜은 다양한 장점이 있지만, 대표적인 장점 몇 가지 정리하면 다음과 같다.   
* 복잡하고 큰 시스템을 기능별로 작게 분류해서, 간단하고 작은 시스템으로 재구성할 수 있다.
  * 따라서 전체 시스템을 이해하기 쉽고, 시스템을 설계하고 구현하기도 편리하다.
* 상하 계층에 인접한 모듈 사이의 인터페이스를 포함하여, 분할된 모듈이 연동할 수 있는 표준 인터페이스를 제공한다.
  * 모듈 인터페이스는 가능한 단순하게 구현하여, 모듈들이 최대한 독립적으로 동작해야 한다.
  * 모듈의 독립성은 전체 시스템의 구조를 단순하게 만들어준다.
* 전송 매체 양단에 있는 호스트가 수행하는 프로토콜들은 좌우 대칭 구조이다.
  * 대칭 구조에서는 통신 양단에 위치하는 동일 계층 사이의 프로토콜을 단순할 수 있다.
* 각 계층의 기능 오류를 수정하거나 향상시켜야 하는 경우에 전체 시스템을 재작성하지 않고 해당 계층의 모듈만 교체하면 된다.
  * 즉, 상하 혹은 좌우 계층 간의 인터페이스를 유지하면, 특정 계층의 내부 변경이 다른 모듈의 동작에 영향을 미치지 않는다.
</br>

### 2. 프로토콜 설계 시 고려 사항
계층 구조의 통신 프로토콜을 설계할 때는 고려할 요소가 많다.   
대표적인 것이, 네트워크 호스트의 주소 표현 방법, 데이터 전송 과정에서의 오류 제어, 통신 양단 사이의 전송 속도를 제어하는 흐름 제어이다.   

주소 표현은 호스트를 유일하게 구분하는 용도로 사용한다.   
오류 제어는 전송 과정에서 데이터 분실, 데이터 변형 등의 오류가 발생했을 때, 데이터를 복구하는 데 사용한다.   
흐름 제어는 송신자가 데이터를 너무 빨리 보내어 수신자가 미처 처리하지 못하는 문제를 해결하기 위한 목적으로 사용한다.   
</br>

### 2.1 주소 표현
여러 호스트가 연결된 환경에서, 특정 호스트끼리 통신하려면, **상대방을 구분할 수 있는 방법** 이 필요하다.   
**시스템을 구분하여 지칭하기 위해서 이름을 부여** 하는 것을 **주소(address)체계** 라 한다. 주소 체계는 시스템의 설계 과정에서 맨 먼저 고려해야 하는 중요한 개념이다.  

```
예를 들어, 전화 시스템의 주소 표기 방법을 살펴보면, 전화번호 체계는 '국가 코드-지역 코드-번호' 형식으로 부여된다.
번호 체계가 국가라는 최상위 광역 코드에서 시작해, 영역을 점점 축소하는 방식으로 계층 구조에 따라 관리된다.
따라서 국가 코드와 지역 코드로 해당 전화기의 지리적 위치를 판단할 수 있다.(정보 함축성)

또 다른 주소 표현의 예로는 주민등록번호가 있다.
주민등록번호에는 다양한 정보가 포함되는데, yymmdd-abcdefg 형태에서 앞쪽의 yymmdd는 태어난 해의 연도, 월, 일을 의미한다. 뒤쪽의 a 는 성별을 구별
하는 용도로 사용되는데, 1이면 남자, 2이면 여자를 의미한다.
Y2K 문제로 인해 2000년 이후 출생자는 3이 남자, 4는 여자를 의미하도록 확장되었다. 즉, 1901년과 2001년에 태어난 사람은 yy로 구분하지 못하므로 a 값
으로 구분해야 한다. (유일성)
주소 체계를 결정할 때는 이와 같은 확장성을 반드시 고려해야 한다.(확장성)

+ 편리성
```
</br>

보통 호스트에도 주소를 하나씩 부여하지만, 다수의 호스트를 묶어 하나의 그룹 주소로 표기하기도 한다.   
이는 전통적인 환경이면서 현재도 가장 많이 사용하는 일대일(1:1) 통신과 더불어, 화상 회의 등을 지원하기 위한 일대다(1:n) 통신 환경도 필요하기 때문이다.    
일대다 통신의 대표적인 유형으로는 네트워크에 연결된 모든 호스트에 데이터를 전송할 수 있는 **브로드캐스팅(broadcasting)** 표기 방법과, 특정 사용자를 그룹으로 묶어 지칭하는 **멀티캐스팅(multicasting)** 표기 방법이 있다.   
</br>

### 2.2 오류 제어
네트워크에서는 데이터 송수신 과정에서 오류가 발생할 수 있다.   
전송 오류에는 데이터가 깨져서 도착하는 데이터 변형 오류와 데이터가 도착하지 못하는 데이터 분실 오류가 있다.   
전송 오류 문제를 해결하는 **오류 제어(error control)** 기능은 통신 프로토콜의 가장 기본적인 기능에 속한다.   

오류가 발생하는 1차 원인은 물리 계층의 전송 매체의 의한 물리적인 오류이다.   
이를 해결하기 위해서 데이터 링크 계층이 물리적은 전송 오류를 해결한다.   
그리고 상위 계층의 프로토콜이 수행될 때는 논리적인 전송 오류가 발생할 수 있으므로, 상위 계층에서도 전송 오류 문제를 다룬다.   

그림은 송신 호스트에서 보낸 데이터가 수신 호스트에 도착했을 때 발생할 수 있는 현상을 **세 가지 유형** 으로 설명한다.   

<img src="https://user-images.githubusercontent.com/83942393/128338471-7c94e956-3f4e-423c-a271-09c8f18e0d58.png" width="60%" height="60%"></img></br>

(a) 데이터가 오류 없이 도착하는 정상적인 경우   
(b) 데이터가 수신 호스트에 도착하지 못하는 데이터 분실 오류   
(c) 데이터의 내용이 변경되어 도착하는 데이터 변형 오류   

(b)처럼 데이터가 분실되는 원인은 매우 다양하다.   
전송 경로가 잘못되어 데이터가 엉뚱한 방향으로 전달될거나, 상위 계층의 논리적인 처리 과정에서 데이터를 분실할 수도 있다.    

데이터가 변형되거나 분실되는 오류가 발생되어 이를 해결하려면, 먼저 오류가 발생한 사실을 인지해야 한다.   
(b)의 경우에는 수신 호스트가 자신에게 데이터가 보내졌다는 사실을 인지하는 것이 쉽지 않기 때문에, 보통은 송신 호스트에서 오류를 감지하는 방법을 사용한다.   
(c)는 수신 호스트가 여러 방식의 오류 검출 기법을 이용해 오류를 검출할 수 있다.   
네트워크에서 전송 오류를 해결하는 일반적인 방법은 송신 호스트가 원래 데이터를 **재전송(retransmission)** 하는 것이다.   

물리적인 오류 외에도, 통신 프로토콜에서 사용하는 알고리즘의 성격에 의해 오류가 발생하기도 한다.    
예를 들어, 송신 호스트가 순차적으로 전송한 데이터의 순서가 뒤바뀌어 도착하는 경우이다.   
수신 호스트에서 도착 순서를 바로 잡으려면 데이터의 논리적인 순서를 의미하는 순서 번호 기능이 필요하다.   
</br>

### 2.3 흐름 제어
전송 매체에서 물리적인 오류가 없었는데도, 데이터를 분실하는 경우가 있는데, 이는 송수신 호스트 사이의 데이터 전송 처리 속도 차이 때문에 발생하기도 한다.   
```
수신 호스트에 데이터가 도착하면, 일단 내부 버퍼에 보관했다가 처리한다.   
그런데, 내부 버퍼에 보관할 공간을 확보하지 못하면 데이터를 논리적으로 분실하는 결과가 초래된다.   
```

일반적으로 수신 호스트의 버퍼 처리 속도보다 송신 호스트가 데이터를 전송하는 속도가 더 빠르면 논리적인 데이터 분실 오류가 발생할 수 있다.    
이 문제를 해결하려면 송신 호스트의 전송 속도를 조절하는 **흐름 제어(flow control)** 기능이 필요하다.   

그림은 가장 단순한 형태의 흐름 제어 기법을 보여준다.

<img src="https://user-images.githubusercontent.com/83942393/128341334-06082cb4-b182-4691-8da7-8fcbedf51f79.png" width="40%" height="40%"></img></br>

송신 호스트가 데이터를 전송하려면 반드시 수신 호스트로부터 명시적인 전송 허가를 받야아 한다.   

그림에서 보면, 송신 호스트가 i 번째 데이터를 보내고 수신 호스트가 이를 제대로 받는다. (1)   
이후에 송신 호스트가 i+1 번째 데이터를 보내려면 수신 호스트의 전송 허가가 필요하다.   
수신 호스트는 데이터를 수신할 이력이 있을 경우에만 전송 허가를 보낸다. (2)   
그림에서 전송 허가를 수신한 후에 송신 호스트가 다음 데이터인 i+1 을 전송하고 있다. (3)   

이와 같이 흐름 제어 기능은 보통 수신 호스트의 제어에 의해 이루어진다.   
</br>

### 2.4 데이터의 전달 방식
프로토콜 설계 시 고려해야 할 마지막 사항은 데이터 전달 방식이다. 

일대일 통신 환경에서, 데이터를 한쪽 방향으로만 전송하는 것을 **단방향(simplex)** 방식이라 하고, 양쪽에서 데이터를 동시에 전송하는 것을 **전이중(full duplex)** 방식이라 한다.   
일반적인 통신 프로토콜들은 모두 전이중 방식을 지원한다.    
이외에도 데이터가 양방향으로 전송되지만, 특정 시점에는 한쪽 방향으로만 전송할 수 있는 반이중(half duplex) 방식이 있다.   
반이중 방식에서는 양쪽에서 데이터를 동시에 전송할 수 없으므로, 데이터 전송 시점을 제어할 수 있어야 한다.   

데이터 전달 방식에는 데이터 사이의 전송 우선순위를 설정하는 방법이나 긴급 데이터를 처리하는 방법 등도 고려해야 한다.   
</br>

### 3 서비스 프리미티브
프로토콜은 계층 구조로 이루어져 있고, 하위 계층이 상위 계층에 서비스를 제공하는 방식으로 동작한다.   
이러한 서비스는 다음에 살펴볼 프리미티브(primitive) 형태로 구현된다.    
계층 구조 프로토콜에서 하위 계층이 상위 계층에 제공하는 서비스의 종류에는 연결형과 비연결형이 있다.   
</br>

> 연결형 서비스   

연결형(connected-oriented) 서비스를 이용하는 절차는 크게 3단계이다.   
먼저 데이터 전달 경로를 설정하는 연결 설정 단계가 필요하다.   
이 단계가 성공적으로 수행되어 연결이 설정되어야 다음 단계인 데이터 전송이 가능하다.   
모든 데이터의 전송이 완료되어 데이터 전송 단계를 끝내려면 연결을 끊는 연결 해제 단계가 필요하다.   

연결 서비스의 동작 원리는 전화 시스템을 이용한 통화 절차와 매우 유사하다.   
</br>

> 비연결형 서비스

비연결형(connectionless) 서비스는 우편 시스템의 동작 원리와 비슷하다.

연결을 설정하고 해제하는 단계가 필요 없다. 즉, 전송할 데이터가 있으면, 각 데이터를 독립적으로 목적지 호스트로 전송하면 된다.    
데이터는 독립적인 경로 선택 과정에 의해 전달되므로, 도착하는 순서가 보낸 순서와 일치하지 않을 수 있다.  
</br>

하위 계층이 상위 계층에 제공하는 서비스는 **프리미티브(primitive)** 형태로 구현된다.   
따라서, 프리미티브는 하위 계층을 사용하는 방법을 정형화한 것이다.   

연결형 서비스에서 자주 사용하는 서비스 프리미티브의 종류에는 \[표2-1]처럼 CONNECT, DATA, DISCONNECT가 있다.   

표 2-1 연결형 서비스의 프리미티브 종류   
| 종류 | 용도 |
|:----------|:----------|
| CONNECT | 연결 설정 |
| DATA | 데이터 전송 |
| DISCONNECT | 연결 해제 |
</br>

통신 프로토콜에서 프리미티브를 올바르게 수행하려면, 각 피리미티브를 \[표2-2]의 네 가지 기능을 포함하도록 설계해야 한다.   

표2-2 서비스 프리미티브의 기능
| 기능 | 설명 |
|:----------|:----------|
| Request | 클라이언트가 서버에 서비스를 요청함 |
| Indication | 서버에 서비스 요청이 도착했음을 통지함 |
| Response | 서버가 클라이언트에 서비스 응답을 회신함 |
| Confirm | 클라이언트에 응답이 도착했음을 통지함 |

```
표에는 설명의 편리함을 위하여 클라이언트와 서버라는 용어를 사용했으며, 그림에서는 왼쪽 호스트를 클라이언트, 오른쪽 호스트를 서버로 가정했다.   
```

클라이언트에서 서버로 전달되는 요청은 Request 와 Indication 으로 구현되고, 서버의 응답은 Response 와 Confirm으로 구현된다.   
</br>

그림은 클라이언트와 서버 사이에서 서비스 프리미티브가 처리되는 원리를 설명하고 있다.   
* 클라이언트로부터 Request가 발생하면 서버에 Indication 형태로 전달되어 서버가 인지한다.   
* 서버에서는 해당 프리미티브를 올바르게 수신하였음을 클라이언트에 통보하기 위하여 Response를 응답으로 보내고, 이는 클라이언트에 Confirm 형태로 도착한다.   
* 이와 같은 4단계 절차를 통해 하나의 서비스 프리미티브가 처리된다.   

<img src="https://user-images.githubusercontent.com/83942393/128346306-4056293d-aeae-4e88-85ac-de4bf9417fc6.png" width="60%" height="60%"></img></br>

그림의 4단계 절차를 전화 시스템의 연결 설정인 CONNECT에 적용하여 설명하면 다음과 같다.   
```
전화 거는 사람은 클라이언트, 전화 받는 사람을 서버로 가정한다.   
발신자가 전화번호를 누르면(Request) 전화망은 이 전화번호에 해당하는 전화기의 위치를 찾아 수신자의 전화벨(Indication)이 울리게 한다.   
수신자가 전화를 받기 위해 통화 버튼을 누르면(Response) 전화망은 이 사실을 바로 인지할 수 있다.   
수신자가 통화 버튼을 누름과 동시에 발신자 전화기의 발신음이 끊기면(Confirm) 통화 연결 상태가 되었음을 확인할 수 있다.   
```
</br>

네 가지 서비스 프리미티브의 기능을 요약하여 설명하면 다음과 같다.   
</br>

> Request
* Request는 클라이언트에서 발생하며, 서버가 프리미티브의 기능을 수행하도록 하위 프로토콜에 요청할 때 사용한다.
* 연결 설정 요청(CONNECT.request), 데이터 전송 요청(DATA.Request), 연결 해제 요청(DISCONNECT.Request) 등이 있다.
</br>

> Indication
* 클라이언트로부터 Request 요청을 수신한 서버의 하위 프로토콜은 Indication을 사용해서 프리미티브 요청이 발생했음을 알린다.
* 연결 설정, 데이터 전송, 연결 해제에 대해 CONNECT.Indication, DATA.Indication, DISCONNECT.Indication 순으로 사용한다.
</br>

> Response
* 클라이언트로부터 프리미티브를 받은 서버에서는 Reponse를 이용해 클라이언트에 응답한다.
* 연결 설정 요청은 CONNECT.Response를 사용해 연결 허용이나 거부로 응답하고, 데이터는 DATA.Reponse, 연결 해제는 DISCONNECT.Reponse로 전달한다.
</br>

> Confirm
* 서버에서 보낸 응답은 Confirm 형태로 클라이언트에 회신된다.
* 연결 설정은 CONNECT.Confirm, 데이터는 DATA.Confirm, 연결 해제는 DISCONNECT.Confirm 로 전달된다.
</br>

### 💎 02 OSI 참조 모델
네트워크에 연결된 컴퓨터들이 데이터를 주고 받으려면, 서로 연동할 수 있게 표준화된 인터페이스를 지원해야 한다.   
일반적으로 컴퓨터 네트워크에서는 계층 구조로 모듈화된 프로토콜 스택(stack)을 사용한다.   

국제 표준화 기구인 ISO가 확립한 OSI(Open System Interconnection) 7계층 모델은 개방(Open)화된 데이터 통신 환경에 적합한 계층적 구현 모델의 표준이다.   

### 1. OSI 7계층 모델
그림은 ISO(International Standard Organization)에서 제시한 OSI 7계층 모델(OSI 7 Layer Model)이다.   
연결된 두 호스트가 각각 7개 계층으로 구성된 모듈을 수행함으로써 데이터 송수신이 가능하다.   
전송 데이터는 송신 호스트의 응용 계층에서 시작해 하위 계층으로 순차적으로 전달되어, 최종적으로 물리 계층에서 수신 호스트에 전달된다.   
수신 호스트에서는 데이터를 상위 계층으로 순차적으로 이동시켜 응용 계층까지 보내준다.   

데이터가 하위 계층으로 내려갈 때는 각 계층의 프로토콜에서 정의한 헤더 정보가 추가된다.   
물리 계층을 제외한 모든 계층에서 헤더 정보가 추가되고, 데이터를 수신하는 호스트에서는 반대로 상위 계층으로 올라가며 순차적으로 헤더 정보를 제거하고 해석한다.   

### 1.1 용어 정의
임의의 호스트에서 실행되는 계층 n 모듈은 상대 호스트의 계층 n 모듈과 논리적으로 통신하는데, 이들이 사용하는 규칙을 계층 n **프로토콜** 이라 한다.  
프로토콜의 역할은 프로토콜에서 정의된 기능을 수행하면서 필요한 정보를 서로 교환하는 것이다.   
프로토콜 기능을 원활하게 수행하려면, 앞 절에서 언급한 주소 표현 방법, 오류 제어, 흐름 제어 등의 기능이 설계와 구현 과정에서 반영되어야 한다.   
</br>

<img src="https://user-images.githubusercontent.com/83942393/128349377-bbb4b8fb-5715-4077-b87f-3456d6159821.png" width="70%" height="70%"></img></br>
그림 2-6 OSI 7계층 모델의 동작

* 동일 계층에 위치한 통신 양단은 같은 프로토콜을 사용하여 통신하기 때문에 **동료 프로세스(peer process)** 라 한다.
* 한 호스트에서 상하로 이웃하는 계층에 위치한 모듈 사이에는 **인터페이스(Interface)** 가 정의되어 둘 사이의 접근 방법을 제한한다.
* 상위 계층에서는 하위 계층의 인터페이스를 통해 하위 계층의 **서비스(Service)** 를 이용할 수 있다.
* 송신 호스트에서 데이터를 전달할 때는, 동료 프로세스에 직접 전달하는 것이 아니라, 하위 계층을 통하여 간접적으로 서비스를 요청한다.
* 이 요청은 최하위 물리 계층까지 반복된다. 
* 수신 호스트에서는 반대로 상위 계층으로 데이터가 전달되면서 프로토콜 기능이 동작한다.
* 각 계층의 동료 프로세스가 직접 통신하는 형태를 보이지만, 실제로는 항상 물리 계층을 통해 데이터가 전송되는 것이다.
</br>

### 1.2 헤더 정보
* 프로토콜 스택의 맨 위에 위치한 일반 사용자는 전송 데이터가 있으면, 이를 응용 계층에 보내 전송을 요청한다.   
* 응용 계층에서는 데이터에 자신의 프로토콜에서 정의한 헤더 정보를 추가해 표현 계층에 보낸다.   
* 표현 계층도 표현 계층에서 사용하는 프로토콜의 헤더 정보를 추가해, 하위 계층으로 보낸다.   

이러한 일련의 과정은 물리 계층에서 데이터가 물리적으로 전송될 때 까지 반복된다.  

물리 계층에서 수신 호스트에 데이터를 실제로 전송하고, 이를 수신한 호스트에서는 송신 절차와 반대 방향으로 헤더를 제거하는 과정이 반복된다.   
즉, 계층별로 해당 계층의 헤더 정보를 해석하여 적절히 처리한 후에 상위 계층으로 올려준다.   
따라서 송신 호스트에서 계층별로 추가된 헤더 정보가 수신 호스트에서 해석 및 삭제되어 최상위 수신자는 원래의 전송 데이터만 받는다.   

이때, 각 계층의 프로토콜은 정해진 기능을 수행하여, 데이터 송신 과정에서 발생하는 문제점을 해결해준다.   
</br>

### 1.3 중개 기능
그림처럼 송신 호스트에서 수신 호스트로 데이터를 전달하려면, 중개 역할을 수행하는 중개 노드를 거쳐야 한다.   
중개 시스템은 데이터가 목적지까지 올바르게 전달되도록, 경로 배정 기능을 수행한다.   
중개 시스템에서 경로 배정 기능을 수행하는 네트워크 계층의 프로토콜이 동작하는데, 이와 같은 **경로 배정 기능** 을 **라우팅** (Routing)이라 한다.   

<img src="https://user-images.githubusercontent.com/83942393/128489183-f7d942d0-2b88-4ecc-8681-3829f9393641.jpg" width="55%" height="55%"></img></br>

중개 노드인 라우터(Router)는 자신에게 도착한 헤더 정보를 해석해서 적절한 경로로 전달하며, 다음 라우터로 보내기 전에 헤더 정보를 수정하는 작업도 진행한다.   
라우터 좌우에 위치한 네트워크는 종류가 다를 수도 있다.    
네트워크가 다르면 물리적인 특성뿐 아니라, 하위 계층의 헤더 정보도 다를 수 있다.   
따라서 헤더 정보의 값을 해석하여 변환하는 작업은 라우터의 중요 기능에 해당한다.  
</br>

### 2 계층별 기능
OSI 7계층 모델의 모든 계층이 중요하지만, 특히 전송 계층이 중요하다.   
전송 계층은 통신 양단에 있는 최종 사용자(프로세스) 사이의 종단 연결을 제공한다.   
호스트에서 실행되는 프로세스와 프로세스 사이의 연결을 설정하여, 데이터를 주고 받을 수 있게 해주는 것이 전송 계층이다.   
```
전화 시스템을 예로 들면, 통화자 사이에 통화 연결을 설정하는 것이 바로 전송 계층이다.
```

전송 계층의 하위에 있는 물리 계층, 데이터 링크 계층, 네트워크 계층은 전송 계층의 연결을 설정하고 지원하는 역할을 수행한다.   
상위에 있는 세션 계층, 표현 계층, 응용 계층은 전송 계층의 연결을 어떻게 활용할지에 대하여 다룬다.    

따라서 OSI 7 계층 모델은 전송 계층을 기준으로, 두 부분으로 나뉜다고 볼 수 있다.   
실제로 TCP/IP 모델에서는 운영체제 내부에 계층 4까지의 기능을 구현하고, 상위 계층의 기능은 사용자 프로그램으로 구현한다.   
</br>

### 2.1 물리 계층
* OSI 7 계층의 맨 밑에 위치하는 **물리 계층(physical Layer)** 은 전송 매체의 물리적 인터페이스에 관한 사항을 기술한다.
* 즉, 전송 매체에는 개별 정보의 비트(bit) 교환 문제를 다룬다.
* 물리 계층은 하드웨어 시스템으로 구현되고, 계층 2 이상의 프로토콜들은 소프트웨어적으로 구현된다.
* 물리 계층에서 다루는 전송 매체의 특성에는, 데이터 전송 속도, 송수신 호스트 사이의 클럭 동기화 방법, 물리적 형태 등이 있다.
</br>

### 2.2 데이터 링크 계층
* **데이터 링크 계층(Data Link Layer)** 은 물리 계층을 통해 전송되는 데이터의 물리적 전송 오류를 해결한다.
* 결과적으로 상위의 네트워크 계층에 신뢰성 있는 패킷 전송을 보장해주어 전송 오류에 대한 부담을 없애준다.
* 데이터 링크 계층은 갈림길에서 전송 경로를 선택할 수 없으므로 두 호스트가 일대일로 직접 연결된 환경에서만 데이터 전송을 지원한다.
* 데이터 링크 계층을 이용해 전송되는 데이터를 **프레임(Frame)** 이라 부른다.
* 프레임 헤더에 표시되는 송수신 호스트 정보에는 LAN 카드에 내장된 송수신 호스트의 MAC 주소가 기록된다.
* 데이터 링크 계층은 다른 상위 계층처럼 송신 호스트와 수신 호스트 사이의 전송 속도 차이를 고려한 흐름 제어 기능도 지원할 수 있다.
</br>

### 2.3 네트워크 계층
* 네트워크 계층(Network Layer)은 송신 호스트가 전송한 데이터가 **어떤 경로를 통해** 수신 호스트에 전달되는지를 결정하는 **라우팅 문제** 를 처리한다.
* 전달 경로 선택은 미리 정해지는 정적인(Static) 방식과 네트워크의 현재 부하 상태에 따라 결정되는 동적인(Dynamic) 방식으로 구분한다.
* 네트워크 계층에서는 전송 데이터를 **패킷(Packet)** 이라 부르며, 중개 과정에서 경로 선택의 기준이 되는 호스트 주소가 필요하다.
* 인터넷에서는 IP 프로토콜이 네트워크 계층의 기능을 수행하므로, 호스트의 IP 주소가 경로 선택에 중요한 기준이 된다.
* 인터넷에 연결된 호스트는 네트워크 계층의 주소와 데이터 링크 계층의 주소를 모두 가진다.
* 컴퓨터 네트워크를 이용해 전송되는 패킷이 지나치게 많으면 네트워크의 전송 속도가 떨어진다.
* 네트워크의 전송 속도가 감소하면 프로토콜 동작에 많은 영향을 미칠 수 있는데, 네트워크의 트래픽이 과도하게 증가하는 문제를 조절하는 **혼잡 제어(Congestion Control)** 기능도 네트워크 계층에서 담당한다.
</br>

### 2.4 전송 계층
* 전송 계층(Transport Layer)은 송신 프로세스와 수신 프로세스를 **직접 연결** 하는 **단대단(end-to-end)** 통신 기능을 제공한다.
* 전송 계층 아래에 있는 하위 계층은 호스트와 호스트 사이의 데이터 전송 과정에서 발생하는 문제들만 반영한다.
* 반면, 전송 계층은 컴퓨터 내부에서 논리적으로 구축되는 통신 당사자인 프로세스 사이의 통신 문제를 다룬다.
* 전송 계층에서는 전송 오류율, 전송 속도 등과 같은 일반 사용자의 서비스 요구 유형에 대한 고려와 흐름 제어 기능도 제공한다.
</br>

### 2.5 세션 계층
* 세션 계층(Session Layer)의 기능은 전송 계층과 거의 유사하다.
* 그러나 사용자에게 원격 파일 전송이나 원격 로그인 등과 같은 상위적 연결 개념인 세션 기능을 제공한다는 점이 다르다.
* 세션 계층에서는 송수신 호스트 사이의 대화 제어를 비롯해, 상호 배타적인 동작을 제어하기 위한 토큰 제어, 일시적인 전송 장애를 해결하기 위한 동기(Synchronization) 기능 등을 제공한다.
</br>

### 2.6 표현 계층
* 계층 5까지는 주로 데이터의 전송에 관한 내용을 다루지만 표현 계층(Presentation Layer)은 데이터의 의미(Semantic)와 표현 방법(Syntax)을 처리한다.
* 즉, 통신 양단에서 서로 이해할 수 있는 표준 방식으로 데이터를 코딩(Coding)하는 문제를 다룬다.
* 호스트의 데이터 표현 방법이 서로 다르면, 상대방의 데이터를 이해할 수 있도록 적절하게 변환하는 과정이 필요하다.
* 인터넷상에서 개인 정보의 유통과 상거래가 활발해지면서 보안의 중요성이 강조되고 있는데, 데이터를 암호화하는 기술도 표현 계층에서 다룬다.
* 또한 영상 정보 같은 대용량 데이터의 크기를 줄여주는 압축도 표현 계층의 주요 기능이다.
</br>

### 2.7 응용 계층
* 최상위의 응용 계층(Application Layer)에서는 다양하게 존재하는 응용 환경에서 공통으로 필요한 기능을 다룬다.
* 응용 환경은 매우 다양해 범위가 방대하지만, 인터넷에서 많이 사용하는 서비스는 FTP(File Transfer Protocol)로부터 시작된 파일 공유 서비스이다.
* 네트워크 파일을 이용할 때는 파일을 공유할 뿐 아니라, 허가된 사용자가 적절한 접근 권한에 따라 사용할 수 있게 해야 한다.
* 텔넷(Telnet)이 제공하는 가상 터미널, 전자 메일 등도 대표적인 인터넷 서비스이다.
</br>

### 💎 03 TCP/IP 모델

인터넷은 데이터의 중개 기능을 담당하는 네트워크 계층으로 IP 프로토콜을 사용하는 네트워크이다.   
따라서 인터넷에서 연결하고자 하는 호스트는 반드시 IP 프로토콜을 지원해야 하며, 전송 계층은 TCP(Transmission Conrol Protocol) 나 UDP(User Datagram Protocol) 를 사용한다.   
현재 인터넷에서 주로 사용하는 IP 프로토콜은 버전 4(IPv4)이다.   

### 1. 구현 환경
인터넷에 연결된 컴퓨터의 네트워크 구현 모델에서는 그림과 같이 전송 계층까지의 기능을 시스템 공간인 운영체제 내부에 구현한다.   
즉, 인터넷 환경에서 사용하는 TCP/IP 와 하위 계층의 기능을 담당하는 LAN 카드 드라이버 루틴(Driver Routine)은 운영체제 영역에 속한다.   

TCP/IP를 이용하려면 사용자 공간에서 ,네트워크 응용 기능을 지원하는 프로그램을 작성해야 한다.   

<img src="https://user-images.githubusercontent.com/83942393/128467900-ecf3a8ca-2c95-4f77-9d35-a7a4e4ab898a.png" width="80%" height="80%"></img></br>
</br>

### 1.1 시스템 공간
* TCP 와 UDP 는 시스템 운영체제인 커널(Kernel) 내부에 구현되므로 일반 사용자가 이 기능을 직접 이용할 수는 없다.
* 대신 **소켓(Socket)** 인터페이스라는 전송 계층의 프리미티브를 이용해야 하는데, 소켓은 운영체제의 시스템 콜 기능으로 구현되므로, 사용자 프로그램에서 이를 호출하는 방식으로 사용한다.
* TCP 는 연결형 서비스를 제공하고, UDP는 비연결형 서비스를 제공한다.
* 인터넷에서 네트워크 계층은 IP로 구현되며, 네트워크 계층은 전송 패킷의 올바른 경로 선택 기능을 제공한다.
* 네트워크 계층 아래의 계층들은 LAN 카드와 LAN 카드를 구동하는 드라이버 루틴에 의해 구현된다.
</br>

### 1.2 사용자 공간
* 세션 계층부터 응용 계층까지의 기능은 사용자 프로그램으로 구현된다.
* 프로그래밍 환경에서 전송 계층의 기능을 제공하는 소켓 시스템 콜을 호출해 TCP와 UDP 기능을 사용할 수 있다.
* 소켓 시스템은 유닉스(Unix), 리눅스(Linux), 윈도우즈 운영체제 등 인터넷에 접속 가능한 모든 호스트에서 제공한다.
* 프로그램에서 소켓을 사용할 때는 소켓마다 부여되는 고유 주소인 포트 번호를 관리해야 한다.
* 일반 네트워크 프로그램은 포트 하나를 할당해 사용하므로, 포트 번호와 사용자 프로그램이 일대일 대응된다.
* 응용 환경에 따라서는 포트 번호를 여러 개 할당할 수도 있다.
* 응용 프로그램을 설계할 떄는 포트 할당에 주의해야 하지만, 일반 사용자는 프로그램 하나에 포트 하나를 사용한다고 가정해도 큰 문제가 없다.
* 인터넷 응용 프로그램의 고유 주소는 IP 주소와 포트 번호의 조합으로 구성된다.
</br>

### 2. 프로토콜
앞서 설명한 것처럼 인터넷에서 데이터 전송은 계층 4의 TCP와 UDP, 계층 3의 IP 에 의해 이루어진다.   
TCP/IP 모델에서는 사용자 데이터의 전송이 TCP, UDP, IP 에 의해 이루어지지만, 이들이 올바르게 동작하려면 더 많은 프로토콜이 필요하다.   
특히, 주소 문제를 해결하기 위한 ARP, RARP 와 오류 문제를 해결하기 위한 ICMP는 TCP/IP 모델의 동작에서 매우 중요한 역할을 한다.   
</br>

### 2.1 TCP/IP 계층 구조 
그림은 TCP/IP를 사용하는 인터넷 환경에서 관련 프로토콜들의 계층 구조를 설명한다.   
맨 위의 응용 프로그램은 TCP와 UDP 를 사용해 데이터 송수신 기능을 수행하지만, 네트워크 게층의 IP 프로토콜을 직접 사용하기도 한다.   
ICMP 와 ARP/RARP 는 네트워크 계층에서 소속되어 IP의 동작을 도와준다.   

<img src="https://user-images.githubusercontent.com/83942393/128471096-144d72d3-d94e-4d4d-822b-4f52f0fe3544.png" width="50%" height="50%"></img></br>

<img src="https://user-images.githubusercontent.com/83942393/128471302-576d7328-59dd-427d-8136-b18ec5169110.png" width="60%" height="60%"></img></br>

네트워크 계층의 IP 는 사용자 데이터를 전송하는 프로토콜이다.   
IP 동작 과정에서 전송 오류가 발생하는 경우에 대비해, 오류 정보를 전송하는 목적으로 ICMP(Internet Control Message Protocol)를 사용한다.   
ICMP는 IP 프로토콜과 같은 계층으로 간주할 수 있지만, ICMP에서 발생하는 ICMP 메세지는 IP 패킷에 캡슐화되어 전송된다.   
</br>

### 2.2 ARP 와 RARP
* TCP/IP 모델에서 사용하는 주소는 데이터 링크 계층의 MAC 주소, 네트워크 계층의 IP 주소, 전송 계층의 포트 번호이다.   
* 포트 번호는 사용자 프로그램 환경에서 사용되므로, 번호 할당과 관리가 다른 계층 프로토콜 동작에 크게 영향을 미치지 않는다.   
</br>

* IP 주소와 MAC 주소는 프로토콜의 동작 특성상 몇 가지 고려할 사항이 있다.   
* 예를 들어, 계층 2 프로토콜을 이용해 데이터를 전송하려면 목적지 호스트의 MAC 주소가 필요하다.   
* 일반적으로 송신 호스트는 자신의 IP 주소와 MAC 주소는 쉽게 얻을 수 있지만, 수신자의 주소를 얻으려면 몇 단계의 처리 과정이 필요하다.   
</br>

* 먼저, 상대방의 IP 주소는 응용 프로그램의 사용자로부터 입력되지만, MAC 주소 정보는 어디에서도 얻을 수 없다.   
* 따라서 사용자로부터 입력된 상대방 호스트의 IP 주소를 이용해 MAC 주소를 구하는 기능이 필요한데, **ARP** (Address Resolution Protocol)가 이 기능을 담당한다.   
</br>

* 호스트의 IP 주소는 컴퓨터 설정 작업의 초기화 과정에서 특정 파일에 보관된다.   
* 그러나 하드디스크가 없는 시스템은 LAN 카드에 내장된 자신의 MAC 주소는 알지만, 파일 시스템이 존재하지 않으므로 IP 주소를 알 수 없다.   
* 이 문제를 해결하기 위하여 MAC 주소를 IP 주소로 변환하는 **RARP** (Reverse Address Resolution Protocol)가 필요하다.   
</br> 

### 2.3 ICMP
* 데이터 전송 프로토콜인 IP 가 동작하는 과정에서는 전송 오류가 발생할 수 있다.
* 오류가 발생하면 반드시 송신자에게 회신해 복구 작업을 하게 해야 하는데, 이 작업은 **ICMP** (Internet Control Message Protocol)가 담당한다.
* ICMP 프로토콜은 오류 메시지를 전송하기 위한 별도의 헤더 구조를 가지며, IP 패킷에 캡슐화되어 전송되지만, IP 와 같은 계층으로 취급된다.
</br>

표 2-3 ARP, RARP, ICMP의 비교    
| 프로토콜 | 특징 |
|:----------|:----------|
| ARP | * 인터넷에서 통신하려면 자신의 로컬 IP 주소와 MAC 주소, 원격 호스트의 IP 주소와 MAC 주소가 필요하다. </br> * ARP는 원격 호스트의 주소 변환 기능을 제공하는데, 사용자가 입력한 IP 주소를 이용해 MAC 주소를 제공하는 프로토콜이다. |
| RARP | * RARP 는 로컬 호스트의 주소 변환 기능을 제공하는데, LAN 카드에 보관된 MAC 주소를 이용해 IP 주소를 제공하는 프로토콜이다. </br> * 일반 컴퓨터 시스템은 로컬 호스트의 IP 주소가 파일 시스템에 보관되므로 RARP를 사용하지 않지만, 디스크가 장착되지 않은 시스템에서는 RARP를 반드시 사용해야 한다. |
| ICMP | 사용자 데이터의 전송 과정에서 오류가 발생하면, 오류 메시지가 생성되는데, ICMP는 이를 전송하는 기능을 담당하는 프로토콜이다. |









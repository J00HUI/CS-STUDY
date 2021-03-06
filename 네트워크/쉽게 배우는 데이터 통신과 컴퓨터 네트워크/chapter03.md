### 🔆 Preview

전화 교환기가 중개하는 음성 통신 서비스 시대가, 인터넷으로 대표되는 컴퓨터 통신 환경으로 전환되면서 통신 기술에 많은 발전이 있었다.   
고정 대역의 연속 전송 서비스를 지원하는 회선 교환 시스템은 음성 서비스에 적합하지만, 컴퓨터 네트워크 환경과는 어울리지 않는다.   

컴퓨터 네트워크와 같은 비실시간적인 가변 대역 통신을 지원하기 위해 패킷 교환 시스템이 개발되었다.   
그리고 인터넷으로 영상, 음성 등의 실시간 멀티미디어 서비스가 지원되면서 네트워크 서비스 품질에 대한 요구가 더욱 커지고 있다.   
사용자의 네트워크 서비스 요구 조건을 특성별로 분석하고, 이를 네트워크에서 적절히 지원하는 차등화된 네트워크 서비스가 인터넷에 활발히 도입되고 있다.   

컴퓨터 통신망은 가변적인 대역을 전제로 통신 서비스를 제공하기 때문에, 인터넷을 사용하면 데이터의 전송 속도가 일정하지 않다.   
이러한 가변적인 환경을 이해하려면, 통신망 내부에서 데이터 전송이 어떻게 이루어지는지를 알아야 한다.   
이것이 인터넷에서 사용하는 주요 데이터 서비스 환경인 가상 회선과 데이터 그램 전송 방식에 대해 학습해야 하는 이유이다.   

3장에서는 컴퓨터 통신의 기본 원리인, 패킷 교환 시스템의 구조와 동작 원리에 대하여 설명한다.   
이어서 인터넷이 어떻게 구성되는지, 인터네트워킹이라는 네트워크 연결의 확장이 어떤 원리에 이루어지는지에 대하여 학습한다. *\*(LAN->WAN)?*   
가변 대역의 컴퓨터 통신 환경에서 서비스 품질을 보장하기 위한 기본 개념에 대해서도 알아본다.   
</br>

< 음성 통신 서비스 시대 > -> < 컴퓨터 통신 서비스 시대> => 통신 기술의 발전
| 회선 교환 시스템 | 패킷 교환 시스템 |
|:----------:|:----------:|
| 고정 대역 | 비실시간 |
| 연속 전송 서비스 | 가변 대역 |
| | 데이터 전송 속도 일정 X |
| | * 가상 회선 방식 </br> * 데이터그램 전송 방식 |
</br>

## 💎 01 교환 시스템
1. 회선 교환 방식 2. 패킷 교환 방식 +) 3. 프레임 릴레이 방식 4. 셀 릴레이 방식   

그림은 데이터 통신망에서 제공하는 다양한 교환 방식을 설명한다.   
연결형 서비스를 제공하는 **회선 교환 방식** 은 음성 전화 서비스를 통해 발전했으며, 고정 대역폭의 전송률을 지원하므로, 네트워크의 구조가 상대적으로 단순하다.   
반면에, 비연결형 서비스를 제공하는 **패킷 교환 방식** 은 컴퓨터 네트워크를 통해 발전했으며, 가변 대역의 전송률을 지원해 네트워크 구조가 복잡하다.   

이외에도 프레임 릴레이와 셀 릴레이 교환 방식이 있는데, 이는 데이터의 전송 속도를 향상시키는 기술을 접목한 방식이다.   


![image](https://user-images.githubusercontent.com/83942393/128623679-7d6e8e40-eb7b-40e2-a8e3-fe5c4a346f6e.png)
</br>
</br>

**회선 교환** (Circuit Switching) 방식은 고정 대역으로 할당된 연결을 설정하여 데이터 전송을 시작한다.   
* 따라서, 회선에 할당된 고정 크기의 안정적인 전송률로 데이터를 전송할 수 있으며, 연결이 유지되는 동안에는 다른 연결에서 이 대역을 사용할 수 없다.   
* 데이터의 전송 경로가 연결 설정 과정에서 확정되므로, 라우팅 등의 작업이 상대적으로 쉽다.   
</br>

**패킷 교환** (Packet Switching) 방식은 컴퓨터 네트워크 환경에서 주로 이용한다.   
* 데이터를 미리 패킷 단위로 나누어 전송하므로, 패킷을 기준으로 교환 작업이 이루어진다.   
* 패킷 교환 방식은 데이터 전송을 위한 대역을 따로 할당하지 않기 때문에 , 가변 크기의 전송률을 지원한다.   
* 패킷 교환에는 모든 패킷의 경로를 일정하게 유지시키는 **가상 회선** (Virtual Circuit) 방식과 패킷들이 각각의 경로로 전송되는 **데이터그램** (Datagram) 방식이 있다.   
</br>

![image](https://user-images.githubusercontent.com/83942393/128623692-1b81c387-f798-4eac-8f1a-af486071c4f0.png)
</br>
</br>

### 1. 교환 시스템의 종류 
전송 선로를 이용해 데이터를 전송할 때는 **전용 회선** 을 이용하거나 **교환 회선** 을 이용할 수 있다.   
*\*전용 회선 방식에서는 송신 호스트와 수신 호스트가 전용으로 할당된 통신 선로로 데이터를 전송하지만, 교환 회선 방식에서는 전송 선로 하나를 다수의 사용자가 공유한다.*   

일반적으로 전화 서비스와 같은 공중 전화망은 **교환 회선 방식** 을 사용한다.   
그림은 교환 회선 방식을 이용하여 네트워크를 구성한 예이다.   

<img src="https://user-images.githubusercontent.com/83942393/128623962-66fce4af-884f-46a2-8187-08a0d1d71af8.png" width="50%" height="40%"></img> <img src="https://user-images.githubusercontent.com/83942393/128699939-23d32067-a661-4faf-a02a-d59738fc932a.png" width="30%" height="30%"></img></br>

그림 3-2 교환 회선 방식을 이용한 네트워크 구성 예   

교환 회선 방식을 이용해 데이터를 주고 받으려면, 중간에 위치한 교환 시스템의 중개가 필요하다.   
그림에서 뭉게구름 안에 있는 교환기와 전송 선로들은 바깥에 있는 호스트들이 데이터를 송수신하기 위해 공유하는 자원이다.   

```
호스트 a 에서 호스트 f 로 데이터를 보내려면, 먼저 연결 설정을 통해 전송 경로를 결정해야 한다.
외형상 가장 합리적인 경로는 교환기 1 -> 교환기 3 -> 교환기 5 이다.
만약 교환기 1과 3 사이에 트래픽이 많은 경우라면, 교환기 1 -> 교환기 2 -> 교환기 3 -> 교환기 5 가 대안이 될 수도 있다.
```

어떤 경로가 더 나을지는 전송 시점에서의 네트워크 혼잡도 등 여러 요인에 따라 달라진다.   
특정 전송 선로에 데이터가 집중되지 않으면서 효율적인 경로를 선택할 수 있도록 하는 것이 교환기의 중요한 역할이다.    
</br>

교환 회선을 이용하는 방식은 논리적 연결 설정 유무에 따라 크게 두 가지로 구분된다.   

* 하나는 그림의 (a)처럼 데이터를 전송하기 전에 통신 양단 사이에 **고정된 연결 경로를 설정** 하는 **회선 교환 방식** 이고,   
* 다른 하나는 (b)처럼 미리 연결을 설정하지 않고, **데이터를 패킷 단위로 나누어 전송** 하는 **패킷 교환 방식** 이다.   
* 이외에 메시지 교환이라는 중간 형태도 있다.   
</br>

![image](https://user-images.githubusercontent.com/83942393/128624099-453630bc-c824-449e-af2d-0d1e3a09c7a2.png)
</br>
</br>

### 1.1 회선 교환
* 회선 교환 방식은 그림의 (a)처럼 통신하고자 하는 호스트가 데이터를 전송하기 전에 연결 경로를 미리 설정하는 방식이다.
* 연결 설정 과정에서 송수신 호스트 간의 경로가 결정되기 때문에, 모든 데이터가 같은 경로로 전달된다.
* 회선 교환 방식은 고정 대역의 논리적인 전송 선로를 전용으로 할당받으므로, 안정적인 데이터 전송률을 지원한다.
</br>

### 1.2 메시지 교환
* 메시지 교환(Message Switching) 방식은 데이터를 전송하기 전에 경로를 미리 설정하지 않고, 대신 전송하는 메시지의 헤더마다 목적지 주소를 표시하는 방식이다.
* 중간의 교환 시스템은 이전 교환 시스템에서 보낸 전체 메시지가 도착할 때까지 받은 메시지를 일시적으로 버퍼에 저장한다.
* 이후 모든 메시지가 도착하면, 다음 교환 시스템으로 전달하는 방식을 사용하므로, 데이터 전송이 교환기 단위로 이어진다.
* 따라서 메시지 교환 방식은 송신 호스트가 전송하는 전체 데이터가 하나의 단위로 교환 처리된다고 볼 수 있다.
* 메시지 교환의 장점은 교환 시스템에서 전송 데이터를 저장하는 기능을 제공하기 때문에 송신 호스트가 보낸 시점과 수신 호스트가 받은 시점이 반드시 일치할 필요가 없다는 것이다.
* 메시지를 메모리에 저장하고, 여러 수신자에게 데이터를 전송할 수 있다.
* 전자우편에서 사용된다.
</br>

### 1.3 패킷 교환
* 그림의 (b) 와 같은 패킷 교환 방식은 회선 교환과 메시지 교환의 장점을 모두 이용한다.
* 송신 호스트는 전송할 데이터를 패킷이라는 일정 크기로 나누어 전송하며, 각 패킷은 독립적으로 라우팅 과정을 거쳐 목적지에 도착한다.
* 패킷 교환 시스템의 장점은 전송 대역의 호율적 이용, 호스트의 무제한 수용, 패킷에 우선순위 부여라는 세 가지로 요약할 수 있다.
</br>

> 전송 대역의 효율적 이용
* 여러 호스트에서 전송한 패킷들이 동적인 방식으로 전송 대역을 공유하기 때문에, 전송 선로의 이용 효율을 극대화할 수 있다.
* 이를 반대의 관점으로 설명할 수 있다.
* 즉 회선 교환 시스템에서는 호스트 간 **연결 시** 전송 대역을 전용으로 할당하기 때문에, 해당 호스트들이 데이터를 전송하지 않더라도 다른 호스트는 이 전송 대역을 이용할 수 없다.
* 결과적으로 회선 교환 시스템은 전송 선로 이용 면에서 비효율적이다.
</br>

> 호스트의 무제한 수용
* 회선 교환 방식에서는 개별 연결 요청에 대해 고정 대역을 할당하므로, 전송 대역이 부족하면 **새로운 연결 설정 요청** 을 수용할 수 없다.
* 즉, 모든 **회선 연결에 할당된 대역의 합** 이 **전체 네트워크의 전송 용량**을 초과할 수 없다.
* 그러나 패킷 교환 방식에서는 전송 대역이 부족해 연결 설정 요청을 수용하지 못하는 경우란 없다.
* 임의의 연결 요청에 고정 대역을 할당하지 않으므로, 이론상 호스트를 무한히 수용할 수 있다.
* 전송 대역을 사용하는 호스트의 수가 늘면, 네트워크의 혼잡도가 높아져, 패킷의 전송 지연이 심화될 뿐이다.
</br>

> 패킷에 우선순위 부여
* 패킷 교환 방식을 이용하면 데이터의 전송 작업이 패킷 단위로 이루어져 패킷에 우선순위를 부여하기 편하다.
* 즉, 특정 호스트가 전송하는 패킷들을 먼저 전송할 패킷과 나중에 전송해도 되는 패킷으로 구분하여 선택적으로 우선순위를 부여할 수 있다.
</br>

패킷 교환 방식에도 단점은 있다.
* 패킷을 전송하는 과정에서 회신 교환 방식에 비해 더 많은 지연이 발생한다.
```
예를 들어, 전송 패킷을 라우터의 내부 버퍼에 보관하는 과정에서 지연이 생기고, 기타 여러 종류의 대기 큐를 거치는 과정에서 가변 지연이 생길 수 있다.
또한, 각각의 전송 패킷이 독립적인 경로로 전달되므로, 패킷마다 전송에 걸리는 시간이 일정하지 않을 수 있다. 
따라서 전체 데이터의 전송 지연 시간은 가장 늦게 도착한 패킷의 전송 지연에 영향을 받는다.
각 패킷별로 지연되는 정도를 나타내는 지연 분포의 형태도 가변적일 수밖에 없는데, 이런 가변적인 전송 지연의 분포를 지터(Jiter)라고 한다.
지터 분포는 멀티미디어 데이터와 같이 실시간으로 처리되는 응용 환경에서 중요하다.
```
</br>

교환기에서 패킷 경로를 선택하는 방식은 두 가지이다.
* 호스트 사이의 전송 경로를 미리 고정하는 **정적 경로** (Static Routing)
* 네트워크 혼잡도를 비롯한 주변 상황에 따라 전송 경로를 지속적으로 조정하는 **동적 경로** (Dynamic Routing)
가 있다.

그러면 컴퓨터 네트워크 환경에서 주로 사용하는 패킷 교환 방식에 대해 좀 더 알아보자.
</br>
</br>

| 회선 교환 시스템 | 패킷 교환 시스템 |
|:----------:|:----------:|
| 고정 대역 | 비실시간 |
| 연속 전송 서비스 | 가변 대역 |
| 연결형 서비스 | 데이터 전송 속도 일정 X |
| 네트워크 구조 단순 | * 가상 회선 방식 </br> * 데이터그램 전송 방식 |
| 안정적인 전송률 | 비연결형 |
| 연결 유지시, 다른 연결에서 이 대역 사용 불가 | 네트워크 구조가 복잡 |
| 전송 경로가 연결 설정 과정에서 확정 </br> -> 라우팅 작업이 쉬움 | 데이터를 패킷으로 나눠 패킷 기준으로 교환 작업 |
| 정적 경로 | 가변 크기의 전송률 |
| | 연결 설정 X |
| | 동적 경로 |
</br>

### 2. 패킷 교환
네트워크 계층의 가장 중요한 역할은 앞에서 언급한 것처럼 **패킷의 전송 경로를 결정** 하는 것이다.   
데이터를 패킷 교환 방식으로 전송하는 네트워크는
1. 가상 회선
2. 데이터 그램   

이라는 두 가지 전송 방식을 지원한다.

* 가상 회선 방식 : 데이터를 패킷 단위로 나누어 전송하지만, 송수신 호스트 사이에 **가상 연결을 설정** 하므로 **모든 패킷의 전달 경로가 동일** 하다.   
* 데이터 그램 방식 : **패킷의 경로 선택이 독립적** 으로 이루어진다.   
</br>

### 2.1 가상 회선 
가상 회선(Virtual Circuit) 방식은 연결형 서비스를 지원하기 위한 기능으로, 연결을 통해 전송되는 모든 패킷의 경로가 동일하다.

* 송수신 호스트 사이에 설정된 가상의 단일 파이프를 통해, 송신 호스트가 입력단으로 패킷을 송신하고, 수신 호스트가 출력단에서 패킷을 수신한다.
* 따라서 모든 패킷이 하나의 파이프로 표현되는 동일 경로로 전송되므로, 패킷이 도착하는 순서가 보낸 순서와 같다.
```
여기서, 파이프는 한 프로세스의 출력을 다른 프로세스의 입력으로 사용할 수 있도록 프로세스를 연결하는 논리적 통신 매체이다.
프로세스뿐 아니라 호스트, 네트워크 등도 사용할 수 있다.
```
그림은 가상 회선 방식에서 패킷을 전송하는 방식을 시간의 흐름에 따라 보여준다.
* 가상 회선을 통해 모든 패킷이 동일한 경로로 전송되는 것을 볼 수 있다.
* 따라서 이러한 방식에서는 패킷의 도착 순서가 뒤바뀔 수 없다.
* **버스 노선**

![image](https://user-images.githubusercontent.com/83942393/128632345-4c597392-d468-46fc-b505-518744bb3f19.png)
</br>
</br>

```
가상 회선 방식으로 패킷을 전송하는 원리는, 용어에서 유추할 수 있듯이 회선 교환 방식과 비슷하다.
그러나, 가상 회선 방식은 패킷 교환 방식을 기반으로 하므로, 데이터의 전송 단위가 패킷 단위로 이루어지지만, 회선 교환 방식은 패킷 기능을 지원하지 않는다.
이는 두 교환 방식을 구분하는 중요한 차이점이다.
```
</br>

### 2.2 데이터그램
패킷  교환  방식에서 비연결형 서비스를 이용해 패킷을 독립적으로 전송하는 것을 데이터그램(Datagram) 방식이라 한다.   

* 데이터 그램 방식은 패킷을 송신하기 전에 연결을 설정하는 과정이 없으므로, 미리 경로를 할당하지 않는다.
* 따라서 전송되는 패킷들이 독립적인 경로로 전달된다.
* 일반적으로 데이터그램 방식은 전송할 정보의 양이 적거나, 상대적으로 신뢰성이 중요하지 않은 환경에서 사용된다.

그림은 데이터그램 방식에서 패킷을 전송하는 과정을 시간의 흐름에 따라 보여준다.  
* **택시**
</br>

![image](https://user-images.githubusercontent.com/83942393/128678285-7c9f8f4f-8126-422b-992d-d93db5c2e3e3.png)
</br>
</br>

* 송신 호스트가 전송한 패킷은 출발한 순서와 무관하게 수신 호스트에 도착할 수 있다.
```
예를 들어, (b) 처럼 3번 패킷은 1, 2번 패킷과 다른 경로를 선택할 수 있으며, 각 전송 경로의 속도는 네트워크 혼잡도에 따라 가변적이다.
따라서 목적지에 도착하는 순서를 예측할 수 없고, (d)처럼 송신 호스트에 늦게 출발한 3번 패킷이 2번보다 먼저 도착할 수도 있다.
```
* 데이터 그램 방식에서 데이터의 도착 순서가 바뀌는 것은 흔하게 벌어지는 현상이다.
</br>

### 3. 프레임 릴레이와 셀 릴레이
* 패킷 교환 방식이 개발된 시점에는 원거리 디지털 통신 과정에서 지금보다 더 많은 전송 오류가 발생했다.
* 그래서 전송 패킷에 물리적인 전송 오류를 처리하기 위한 오버헤드 비트를 많이 추가했는데, 이런 패킷들을 처리하는 송수신 시스템의 오류 처리 과정이 상당히 복잡했다.
* 또한 중간에 위치한 교환 시스템에서 오류를 검색하고 복구하는 기능도 필요했다.
* 이와 달리, 현대의 네트워크는 물리적인 전송 오류가 발생할 확률이 매우 낮다.
* 과거의 과도한 오류 제어 기능이 현재의 통신 환경에서는 낭비 요소가 된 것이다.
* 여러 계층에서 수행되는 복잡한 오류 제어 기능 중, 중복되는 부분을 제거하면 패킷의 전송 속도를 높일 수 있다.
* 이처럼, 낭비 요소를 제거해 데이터 전송 속도를 향상시키기 위해 프레임 릴레이와 셀 릴레이 방식이 고안되었다.
</br>

### 3.1 프레임 릴레이
* 신뢰도가 높은 새로운 네트워크 환경을 고려해, 전송 오류 제어 기능을 더 효율적으로 처리하는 네트워크 프로토콜을 작성할 필요가 있다.
* 이를 위해, 동일한 속도의 전송 매체로, 고속 데이터 전송을 지원할 수 있도록 고안된 기술이 **프레임 릴레이** (Frame Relay)이다.

그림은 송신 호스트가 데이터 패킷을 보내고, 수신 호스트가 긍정 응답 패킷으로 회신하는 과정을 패킷 교환 방식과 프레임 릴레이 방식에 각각 적용한 예이다.   

<img width="688" alt="스크린샷 2021-08-09 오후 8 40 08" src="https://user-images.githubusercontent.com/83942393/128700755-0148484b-6688-470d-b886-13a82ede197e.png">


* (a)의 패킷 교환 방식에서는 중간 라우터를 거치는 과정에서, 데이터 링크 계층의 기능이 개별적으로 수행된다.
* 따라서 개별 링크에서 데이터 프레임과 긍정 응답 프레임을 반복 교환한다.
* (b)의 프레임 릴레이 방식보다 오류 제어가 과도하게 이루어진다.
</br>

* (b)의 프레임 릴레이 방식에서는 각 라우터의 개별 연결을 의미하는 홉(Hop) 단위의 흐름 제어와 오류 제어 기능을 수행하지 않는다.
* 따라서 데이터 전송과 긍정 응답의 처리가 큰 흐름으로 이루어져, 전송 패킷의 양이 반으로 줄어든다.
* 이처럼 오류 제어 기능을 단순화하는 작업만으로도 데이터 전송 효율을 크게 향상시킬 수 있다.
</br>

* 패킷 교환 방식이 종단 사용자에게 64Kbps의 전송률을 지원하는 데 반해, 프레임 릴레이 방식은 2Mbps 전송률을 지원한다.
* 이는 앞서 언급한 오류 처리와 관련된 오버헤드를 최소화하여 얻은 결과이다.
* 참고로, 프레임 릴레이 방식은 연결형 패킷 서비스를 지원한다.
* 프레임 릴레이는 한 호스트에서 수신한 프레임을 다른 호스트로 중개(Relay)하는 역할만 한다.
* 오류 복구나 흐름 제어 같은 기능은 수행하지 않으므로, 데이터 링크 계층의 기능을 단순하게 설계할 수 있다.
</br>

### 3.2 셀 릴레이
* ATM(Asynchronous Transfer Mode) 방식응로 더 많이 알려진 셀 릴레이(Cell Relay) 방식은 회선 교환과 패킷 교환 방식이 장점을 모아 고안되었다.
* 셀 릴레이 방식도 프레임 릴레이 방식처럼 오류 제어에 대한 오버헤드를 최소화한다.
* 프레임 릴레이 방식은 가변 길이의 패킷을 지원하지만, 셀 릴레이 방식은 셀(Cell)이라는 고정 크기의 패킷을 사용한다.
* 패킷이 크기가 고정되면, 가변적인 경우보다 처리 과정에서 오버헤드를 더 줄일 수 있다.
* 셀 릴레이 방식은 2~100Mbps의 전송률을 지원한다.
</br>

### 💎 02 LAN, MAN, LAN
컴퓨터 네트워크를 다양한 기준으로 분류할 수 있지만, 가장 간단한 기준은 네트워크의 크기이다.   
```
가장 작은 네트워크의 구성 예는 컴퓨터 시스템 내부에서 볼 수 있다.
매우 빠른 전송 속도를 지원하는 시스템 버스를 이용해 다수의 프로세서(Processor)를 연결하는 다중 처리 시스템(Multiprocessor system)이 이에 해당한다.
```
</br>

컴퓨터 시스템의 내부와 컴퓨터 네트워크의 차이는 전송 매체의 성능에 있다.
* 시스템 버스는 매우 빠른 속도와 높은 전송 대역을 지원하기 때문에, 버스에 연결되는 CPU, 메모리, I/O 장치 등이 낮은 전송 지연으로 데이터를 전송할 수 있는 밀접한 연결(Tightly Coupled) 관계를 갖는다.
* 그에 비해, 네트워크는 전송 매체의 속도가 상대적으로 느려 느슨한 연결(Loosely Coupled) 관계를 지원한다.
</br>

* 일반적으로 네트워크는 물리적으로 일정 거리 이상 떨어진 위치에서 독립적으로 실행할 수 있는 호스트 간의 데이터 교환 환경을 지원한다.
* 호스트 사이의 연결 거리를 기준으로, 네트워크를 LAN, MAN, WAN 으로 구분할 수 있다.
* 이 연결 거리는 데이터의 전송 지연에 많은 영향을 미치므로 네트워크를 설계할 때 중요한 고려 사항이 된다.
</br>

![image](https://user-images.githubusercontent.com/83942393/128685157-83c749a4-7025-42e0-b691-9a5ec882b481.png)


### 1. LAN
LAN(Local Area Network)는 단일 건물이나 학교 같은 소규모 지역에 위치하는 호스트로 구성된 네트워크이다.   
규모가 아주 작을 때는 단일 전송 케이블로 모든 호스트를 연결할 수 있다.   
LAN 은 MAN 이나 WAN 환경보다 호스트 간의 간격이 가깝기 때문에, 데이터를 **브로드 캐스팅** (Broadcasting) 방식으로 전송한다.   

* 호스트 사이의 물리적 거리는 데이터 전송 과정에 영향을 많이 미친다.   
* 가까울수록 데이터 전송 지연이 적으며, 전송 오류가 발생할 가능성도 낮아진다.   
* LAN 에서는 보통 수십 Mbps~ 수Gbps 전송 속도를 지원한다.   
* LAN 환경에서 호스트를 연결하는 방식을 구성 형태(Topology)에 따라 **버스형, 링형** 으로 구분한다.   
</br>

### 1.1 버스형
LAN 환경에서 가장 많이 사용하는 네트워크 연결 형태는 버스형과 링형이다.    

* 버스(Bus)형은 그림처럼 공유 버스 하나에 여러 호스트를 직접 연결한다.
* 한 호스트가 전송한 데이터를 네트워크에 연결된 모든 호스트에 전송하므로, 브로드캐스팅 방식이다.

![image](https://user-images.githubusercontent.com/83942393/128682516-4d6cfc26-5039-4dde-b68a-82f09dda6212.png)

* 버스형 에서는 전송 데이터가 모든 호스트에 전송되므로, 라우팅 기능이 따로 필요 없다.
* 목적지에 해당하는 호스트만 데이터를 내부 버퍼에 보관하고 나머지 호스트들은 데이터를 버림으로써 한 호스트만 데이터를 수신한다.
* 이를 위해 각 호스트를 구분하는 호스트 주소를 이용하고, 전송 데이터에는 송수신 호스트의 주소를 표기한다.
* 둘 이상의 호스트에서 데이터를 동시에 전송하려고 하면, 공유 버스에서 데이터 **충돌** (collision)이 발생할 수 있다.
```
충돌 문제를 해결하는 방법에는
충돌이 발생할 가능성 자체를 차단하는 사전 해결 방식과
충돌을 허용하고, 나중에 해결하는 사후 해결 방식이 있다.
```
* 대표적인 버스형 연결 형태인 이더넷(Ethernet)은 충돌이 발생하는 것을 허용하는 대신, 충돌 후에 문제를 해결하는 사후 해결 방식이다.
* 이더넷 방식은 원래 1~10Mbps의 전송 속도를 지원했지만, 100Mbps, 1Gbps의 고속 이더넷이 등장하면서 영상 데이터처럼 높은 전송률이 필요한 응용 환경에서도 사용할 수 있게 되었다.
</br>

### 1.2 링형
* 링(Ring) 형은 그림처럼 전송 호스트의 연결이 순환 구조인 링 형태이다.
* 데이터는 시계나 반시계 방향으로 전송되며, 특정 호스트에서 전송한 데이터는 반드시 링을 한 바퀴 돌아 송신 호스트로 되돌아온다.
* 따라서 네트워크에 연결된 모든 호스트가 전송 데이터를 수신하는 브로드캐스팅 방식을 지원한다.
* 데이터를 송신한 호스트는 자신에게 되돌아온 데이터를 네트워크에서 회수할 책임이 있다.
</br>

* 링형도 둘 일상의 호스트에서 데이터를 동시에 전송하면, 충돌이 발생할 수 있다.
* 일반적으로 링형에서는 토큰(Token)이라는 제어 프레임을 사용해 충돌 가능성을 차단한다.
* 데이터를 전송할 호스트는 사전에 전송용 토큰을 확보해야 한다.
* 네트워크에는 토큰이 하나만 존재하도록 설계되므로, 특정 시간에 데이터를 전송할 수 있는 호스트는 하나뿐이다.
* 따라서, 호스트 사이에 충돌이 발생할 가능성을 미리 차단할 수 있다.
* 토큰은 네트워크에 연결된 호스트를 모두 순환하도록 설계되었기 때문에, 모든 호스트가 동등한 전송 기회를 갖는다.
</br>

### 2. MAN
* MAN(Metropolitan Area Network)은 LAN 보다 큰 지역을 지원한다.
* 사용하는 하드웨어와 소프트웨어는 LAN과 비슷하지만, 연결 규모가 더 크다.
* MAN은 근처에 위치한 여러 건물이나 한 도시에서의 네트워크 연결로 구성할 수 있다.
</br>

* MAN을 위한 국제 표준안은 DQDB(Distributed Queue Dual Bus)이다.
* 전송 방향이 다른 두 버스로 모든 호스트를 연결하는 구조를 지원한다.
</br>

* DQDB는 비디오와 그래픽 응용 환경을 위한 광 LAN을 위해 개발되었지만, DQDB 구조가 MAN 환경에 적합하여 MAN의 표준안으로 채택되었다.
* 그 후 케이블 TV 산업에 의해 개발이 촉진되었다.
</br>

* DQDB의 특징은 세 가지로 요약할 수 있다.
* 첫째, 분산 데이터 큐를 유지한다.
* 둘째, 데이터를 전송할 때 발생할 수 있는 충돌 문제를 해결하기 위해, 슬롯 링 개념을 변형한 FIFO 기반의 공유 슬롯 방식을 사용한다.
* 마지막으로, ATM(Asynchronous Transfer Mode)과 호환이 가능하도록 53바이트의 프레임을 지원한다.
</br>

DQDB에는 그림의 화솰표처럼 두 개의 단방향 선로가 존재하며, 이 전송 선로를 통해 모든 호스트가 연결된다.   

<img width="596" alt="스크린샷 2021-08-09 오후 6 28 52" src="https://user-images.githubusercontent.com/83942393/128685877-df539119-89d4-448d-aa08-f9682bba20e2.png">

* 버스 1은 데이터를 왼쪽에서 오른쪽으로, 버스 2는 오른쪽에서 왼쪽으로 전송한다.
* 버스 1에서는 헤드 역할을 하는 a가 일정 주기로 슬롯(Slot)을 내보내고, 이 슬롯은 호스트 e 에서 처리를 완료할 때까지 오른쪽으로 계속 이동한다.
* 이 과정에서 중간 호스트는 슬롯을 프레임으로 변형해 데이터를 전송할 수 있다.
* 버스 2에도 같은 원리가 적용되며, 데이터를 반대 방향으로 전송할 때 이용한다.
* 호스트 a에서 호스트 e까지 물리적인 거리가 짧으면 그림의 점선처럼 새로운 연결을 구성할 수 있다.
* 즉, 호스트 a와 호스트 e를 직접 연결하는 추가 전송 매체를 사용함으로써, 신뢰도를 높일 수 있다.
</br>

### 3. WAN
* WAN(Wide Area Network)은 국가 이상의 넓은 지역을 지원하는 네트워크 구조이다.
* LAN과 MAN의 구성엣서는 전송 호스트가 공유 버스를 이용한 브로드캐스팅을 지원하기 때문에 교환의 개념이 필요 없다.
* 그러나 **점대점** (Point-to-Point)으로 연결된 WAN 환경에서는 전송과 더불어 교환 기능이 필요하다.
</br>

WAN에서는 그림처럼 전송 매체를 이용해 호스트를 일대일(1:1)로 연결하는 방식으로 네트워크를 확장한다.    
</br>

![image](https://user-images.githubusercontent.com/83942393/128687241-48718e5c-b97e-4b4f-bed8-039529927d88.png)
</br>

* WAN 에서는 호스트 사이의 거리가 멀기 때문에 연결의 수가 증가할수록 전송 매체를 많이 사용하므로 비용이 많이 든다.
* 따라서 총 연결 거리를 줄이면서 전체 호스트를 효율적으로 연결하도록 설계해야 한다.
* WAN에서는 호스트를 스타형, 트리형, 완전형, 불규칙형 등 다양한 구조로 연결할 수 있다.
</br>

### 💎 03 인터네트워킹
라우팅 장비는 네트워크 내부에서 패킷 교환 기능을 수행하는데, 둘 이상의 서로 다른 네트워크를 연결하는 기능을 인터네트워킹(Internetworking)이라 한다.   
인터네트워킹을 지원하려면 연결되는 네트워크의 차이를 분석해, 전송 데이터를 적절히 중개할 수 있어야 한다.   

두 개의 네트워크를 연결하는 장비는 역할이 어느 계층에 속하느냐에 따라 종류가 달라진다.   
일반적으로 하위 3개 계층인 물리 계층, 데이터 링크 계층, 네트워크 계층의 기능을 수행하며, 특별히 네트워크 계층까지의 기능을 수행하는 장비는 라우터(Router)이다.   

네트워크 간의 차이는 다양한 방법으로 기술할 수 있다.   
```
예를 들어, 연결형·비연결형 서비스, 데이터 전송에 사용되는 프로토콜의 종류, 호스트를 구분하기 위한 주소 표현 방법, 전송 패킷의 크기, 멀티 캐스팅·브로드캐스팅의 지원 여부 등이 고려 대상이다.   
```
</br>

그림은 네트워크 연결을 위한 게이트웨이(Gateway) 장비의 역할을 보여준다.   

<img src="https://user-images.githubusercontent.com/83942393/128690265-a8cdf1c3-b536-4019-9804-a430bbaadf60.png" width="50%" height="50%"></img></br>

* 그림처럼 두 LAN을 연결하려면, 중간에 있는 네트워크 장비가 데이터를 중개해야 한다.   
* 네트워크 장비의 기능에 따라(네트워크 장비의 네트워크 계층, 데이터 링크 계층, 물리 계층의 기능에 따라) 양쪽 LAN 은 특성이 다를 수 있으며, 네트워크 장비 하나에 여러 종류의 LAN을 연결할 수도 있다.   
* 네트워크 장비는 수행 기능에 따라 리피터, 브리지, 라우터로 구분한다.   
```
참고로 데이터 링크 계층은 MAC 계층과 LLC 계층으로 나뉘며, MAC 계층이 하위에 위치하고 LLC 계층은 상위에 위치한다. (이에 대한 자세한 내용은 5장에서 다룬다. )
```
</br>

> 리피터
* 리피터는 계층 1 기능을 지원한다.
* 한쪽 단에서 들어온 비트 신호를 증폭하여 다른 단으로 단순히 전달하는 역할을 한다.
</br>

> 브리지
* 브리지는 계층 2 기능을 지원한다.
* 한쪽 단에서 들어온 프레임의 MAC 계층 헤더를 다른 단의 MAC 계층 헤더로 변형해 전송할 수 있어 종류가 다른 LAN을 연결할 수 있다.
* 브리지가 수신한 프레임의 목적지 주소와 송신 호스트의 주소가 같은 LAN에 소속되어 있으면 브리지는 아무 행동도 하지 않는다.
* 그러나 송수신 호스트의 위치가 서로 다른 LAN 에 속하면 중개 기능을 수행한다.
* 따라서 브리지는 리피터보다 LAN과 LAN 사이의 불필요한 트래픽 발생을 억제할 수 있다.
</br>

> 라우터
* 라우터는 계층 3 기능을 지원한다.
* 교환 기능을 수행할 수 있으므로, 여러 포트를 사용해 다수의 LAN을 연결하는 구조를 지원한다.
* 수신한 패킷을 해석해 적절한 경로로 전송하도록 경로를 배정하는 기능을 한다.
</br>

> 일반적으로 상위 계층의 개념인 게이트웨이는 서로 다른 응용 환경을 지원하기 위해 사용할 수 있으므로, 네트워크 양단의 특성이 다른 환경에서 중개하는 역할을 수행한다.   
</br>

### 1. 브리지
* 브리지 좌우에 위치하는 LAN은 종류가 같을 수도 있고, 다를 수도 있다.
* 에를 들어, 양쪽 LAN이 모두 이더넷을 사용하면, 프레임 헤더를 해석하는 간단한 작업을 통해 쉽게 중개할 수 있다.
* 하지만 종류가 다르면 프레임 변환 등의 복잡한 과정이 필요하다.

그림은 계층 2 의 기능을 수행하는 일반 브리지의 역할을 보여준다.   

<img src="https://user-images.githubusercontent.com/83942393/128692412-b8d882f7-c746-4517-8713-bd855ea87808.png" width="60%" height="60%"></img></br>

* 브리지를 이용해 LAN과 LAN 사이에서 데이터를 중개할 떄, 각 LAN에서 사용하는 MAC 계층이 다를 수 있다.
* 예를 들어, 그림에서 LAN1은 이더넷, LAN2는 토큰링을 사용한다고 가정할 수 있다.
* 이때는 브리지에 MAC 헤더를 해석해 변환하는 기능이 필요하다.
* 즉, LAN1로부터 데이터를 수신할 때는 해당 MAC 계층 헤더를 해석하고 제거해야 한다.
* 그러면 그림처럼 브리지의 최상위 계층에서는 MAC 헤더가 제거되고, LLC 헤더까지 포함된 데이터만 남는다.
* 반대로 LAN2로 전송할 때는 해당 LAN의 MAC 계층에 맞도록 헤더 정보를 적절히 추가해야 한다.
</br>

* 위 예는 브리지에 연결된 LAN이 두 개인 경우지만, 브리지는 더 많은 LAN을 동시에 연결할 수 있다.
* 따라서 브리지에 연결된 LAN의 종류만큼 MAC 계층과 물리 계층을 해석할 수 있어야 한다.
* 동작 방식에 따라 트랜스페런트 브리지와 소스 라우팅 브리지가 있다.
</br>

### 1.1 트랜스페런트 브리지
* 트랜스페런트 브리지(Transparent Bridge)는 이름처럼 라우팅 기능을 사용자에게 투명하게 보여준다.
* 브리질 사용자는 전송하는 프레임의 주소부에 라우팅에 관한 정보를 추가하지 않아도 되며, 필요한 라우팅 과정은 브리지가 자동으로 수행한다.
* 설치 과정에서 하드웨어의 조정이나 소프트웨어의 변경, 주소, 라우팅 테이블 관련 사항을 고려할 필요가 없다.
</br>

* 브리지에 연결된 임의의 LAN으로부터 프레임이 도착했을 때, 브리지가 수행하는 동작은 다음 두 가지 중 하나이다.
* 첫째, 해당 프레임의 수신 호스트가 송신 호스트와 동일한 방향에 위치한 경우는 프레임을 중개하는 과정이 필요 없기 때문에 무시해도 된다.
* 둘째, 프레임의 수신 호스트가 송신 호스트와 다른 방향에 위치하는 경우는 수신 호스트가 있는 방향으로 프레임을 중개해야 한다.
* 이 과정에서 브리지 내부에는 송수신 호스트가 동일한 방향에 있는지와 수신 호스트가 브리지의 어느 방향에 위치하는지에 대한 정보가 있어야 한다. -> 라우팅 테이블
</br>
 
그림은 브리지 B1 과 브리지 B2 를 사용하는 환경에서 브리지 B1 에는 LAN을 세 개(LAN1, LAN2, LAN3) 연결하고, 브리지 B2 에는 LAN을 두 개(LAN3, LAN4) 연결한 예이다.     

![image](https://user-images.githubusercontent.com/83942393/128694051-342ba126-fa3e-450b-9c3b-72a8891b5783.png)
* LAN1에서 전송한 프레임의 목적지 호스트가 LAN1에 위치하면 브리지 B1 의 중개 기능이 필요없다.
* 그러나 LAN2에 위치한 호스트가 목적지라면 2번 포트로 중개해야 한다.
* 그리고 LAN4로 가는 경우에는 브리지 B2의 중개가 추가로 필요하다.
* 이때 브리지의 중개 기능이 올바르게 동작하려면, 그림 상단의 라우팅 테이블과 같은 라우팅 정보가 꼭 필요하다.
* 수신한 프레임을 무시할지, 다른 LAN으로 전달할지는 전적으로 브리지의 라우팅 테이블을 근거로 판단한다.
</br>

> 라우팅 테이블
* 트랜스페런트 브리지가 제대로 동작하려면 라우팅 테이블(Routing Table) 정보가 정확해야 한다.
* 라우팅 테이블은 LAN이 동작하면서 자동으로 생성되는데, 이 과정을 요약하면 다음과 같다.
</br>

* 먼저 브리지에 전원이 들어오면, 라우팅 테이블의 내용이 비어, 초기에는 프레임의 수신자가 어느 쪽 포트에 위치하는지 판단할 수 없다.
* 그러므로, 이 경우에는 **플러딩**(Flooding) 알고리즘을 사용해 입력된 프레임을 브리지의 모든 포트 방향으로 전달한다. *(물론, 프레임이 들어온 방향으로는 전달하지 않는다.)*
* 플러팅 알고리즘의 동작 과정에서 브리지에 입력된 송신 호스트의 주소를 근거로, 송신 호스트가 몇 번 포트에 연결되었는지 알 수 있다.
```
예를 들어, 그림의 브리지 B1의 경우에 2번 포트로 받은 프레임의 송신 호스트 주소가 c 이면, 호스트 c 는 2번 포트에 연결되어 있다고 판단할 수 있다.
```
* 이와 같이 데이터 전달 과정에서 얻은 프레임의 송신 호스트 주소와 포트 번호를 라우팅 테이블에 반영한다.
</br>

* 위 방법을 사용하면 시간이 경과함에 따라 라우팅 테이블의 정보가 계속 누적되므로 라우팅 정보를 효과적으로 수집할 수 있다.
* 또, 호스트의 연결 위치를 변경해도 라우팅 정보를 자동으로 갱신할 수 있다.
* 이처럼 네트워크의 동작 과정에서 라우팅 정보를 얻는 방식을 **역방향 학습** (Backward Learning) 알고리즘이라 한다.
</br>

* 호스트의 위치가 바뀌어 라우팅 정보가 변경되는 경우에는, 가장 최근 정보로 수정해주어야 한다.
* 그림에서 LAN2에 연결된 호스트 c 가 LAN4로 이동하면 수신된 프레임의 송신 호스트 정보를 근거로 라우팅 테이블의 내용을 새로 수정해야 한다.
* 브리지 B1과 브리지 B2의 라우팅 테이블에 호스트 c 의 이동을 반영하면 다음 그림과 같다.
</br>

<img src="https://user-images.githubusercontent.com/83942393/128695060-2d30cc1b-53c7-4ae2-93a9-a3fa66845591.png" width="60%" height="60%"></img></br>
</br>

> 스패닝 트리

앞서 소개한 역방향 학습 알고리즘을 이용하면 라우팅 정보를 효과적으로 얻을 수 있다.     
그러나 다음 그림처럼 네트워크에 이중 경로가 존재하면 잘못된 라우팅 정보를 얻을 수 있다.      

<img src="https://user-images.githubusercontent.com/83942393/129304129-ef3885de-b38b-44de-b79f-72ef3aa18096.jpg" width="60%" height="60%"></img></br>

* 예를 들어, 그림에 소개한 네트워크의 초기 동작에서 브리지 B1과 브리지 B2는 플러딩 알고리즘을 사용해 프레임을 전달한다.
* 호스트 a가 임의의 수신 호스트에 프레임을 전달한다고 가정해보자.
* 호스트 a가 보낸 프레임은 브리지 B1의 1번 포트로 전달되므로, 브리지 B1의 라우팅 테이블에는 호스트 a가 1번 포트로 연결된 것으로 등록된다.
* 동시에 호스트 a가 보낸 프레임은 브리지 B2를 통해 브리지 B1의 2번 포트로도 들어온다.
* 결과적으로, 브리지 B1에서는 호스트 a가 보낸 프레임이 1번과 2번 포트 두 군데에서 다 들어오므로 모순된 라우팅 테이블이 만들어진다.
* 브리지 B2에도 동일한 원리가 적용되고, 호스트 a가 두 포트에 모두 연결된 것처럼 라우팅 정보가 만들어진다.
</br>

* 이후, 수신 호스트의 주소가 a로 지정된 프레임이 전송되면, 두 브리지는 데이터를 양쪽 포트로 전달하기 때문에 전송 프레임이 네트워크를 계속 순환하는 결과를 초래한다.
* 이런 문제점을 해결하려면 이중 경로가 존재하지 않도록 네트워크를 설계해야 한다.
* 네트워크의 설계 과정에서 순환 구조가 불가피하게 만들어진다면, 네트워크의 논리적인 연결 상태를 비순환 형태로 간주함으로써, 역방향 학습 알고리즘이 올바르게 동작하도록 해야 한다.
* 네트워크의 비순환 구조를 **스패닝 트리** (Spanning Tree)라 하고, 이를 지원하는 알고리즘을 스패닝 트리 알고리즘이라 한다.
```
스패닝 트리를 구성하려면, 먼저 임의의 브리지를 트리 구조의 최상위 브리지인 루트(Root)로 지정해야 한다.
이를 위해 브리지가 자신의 고유 번호를 서로 공개함으로써, 번호가 가장 낮은 브리지를 루트로 선정할 수 있다.
그런 다음, 루트 브리지에서 다른 모든 브리지까지의 최단 경로 트리를 구성하는 방식으로 LAN을 구축하는 과정을 밟는다.
```
</br>

### 1.2 소스 라우팅 브리지
트랜스페런트 브리지는 공유 버스에서 구현되는 CSMA/CD(Carrier Sense Multiple Access/Collision Detection) 방식과 토큰 버스 방식에서 사용한다.   
사용자 입장에서 보면 간편하지만, 효율적이지 못하다는 단점도 있다.   

일반적으로 소스 라우팅 브리지(Source Routing Bridge)는 링 구조의 네트워크에서 사용한다.   
이 방식은 이름처럼 프레임이 수신 호스트까지 도달하기 위한 라우팅 정보를 송신 호스트가 제공한다.   
즉, 송신 프레임 내부에 수신 호스트까지 도달하기 위한 모든 경로를 기술함으로써, 중간 브리지에 필요한 라우팅 정보가 프레임 자체에 포함된다.   
프레임을 수신한 브리지는 이 정보를 이용해 프레임을 적절한 경로로 전달한다.    
</br>

### 2. IP 네트워킹
인터넷 환경에서 IP 프로토콜을 사용해 **IP 인터네트워킹** (IP Internetworking)을 지원하려면 그림처럼 라우터가 송수신 호스트 간의 여러 네트워크 인터페이스를 거쳐 패킷을 전달할 수 있어야 한다.   

<img width="614" alt="스크린샷 2021-08-09 오후 8 42 35" src="https://user-images.githubusercontent.com/83942393/128700944-b9698a34-1cf3-40b5-aef3-2e56bb4ca1ce.png">

* 그림에서는 라우터 A가 이더넷 인터페이스와 PPP 인터페이스를 지원하고, 라우터 B는 PPP와 [ATM](https://terms.naver.com/entry.naver?docId=815541&cid=42344&categoryId=42344) 인터페이스를 지원하다고 가정해였다.
* 이들을 이용해 이더넷과 ATM이라는 상이한 네트워크 인터페이스를 지원하는 사용자 간의 연결 구조가 가능함을 알 수 있다.
* 패킷을 올바르게 중개하기 위해 라우터들은 IP 프로토콜까지의 계층 기능을 지원하고, 송수신 호스트는 TCP/IP 응용 프로그램을 이용해 통신한다.
</br>

* 라우터에는 양쪽의 MAC 계층의 차이를 해결하는 기능이 필요하다.
* 그림처럼 라우터 A 는 입력된 이더넷 헤더를 PPP 헤더로 변환하고, 라우터 B는 PPP 헤더를 ATM 헤더로 변환해주어야 한다.

<img width="684" alt="스크린샷 2021-08-09 오후 8 56 46" src="https://user-images.githubusercontent.com/83942393/128702518-2e434969-2605-4c0c-bf4f-ddee0cd25e22.png">

```
데이터가 반대 방향으로 전달되는 경우에는 헤더 변환 과정이 반대로 이루어진다.
```
* 라우터에 연결된 네트워크가 동일한 종류의 MAC 계층을 사용하면 MAC 헤더의 변환 과정은 이루어지지 않는다.
* 헤더 변환 과정과는 별도로, 라우터를 거치는 동안에 전송되는 패킷이 특정 MAC 계층에서 전송하기에 너무 크면, 패킷의 분할과 병합 과정이 이루어진다.
</br>

### 3. 인터넷 라우팅
* 라우터의 역할은 수신된 IP 데이터그램을 적절한 경로로 전달하는 것이다.
* 그러려면 인터넷의 전체 구성과 현재 상태에 대한 정보를 활용해 경로를 선택해야 한다.
* 대표적인 라우팅 방식으로 고정 경로 배정과 적응 경로 배정이 있다. 
</br>

### 3.1 고정 경로 배정
* 고정 경로 배정(Fixed Routing)은 간단한 구현만으로도 효과적인 라우팅이 가능한 방법으로, 송수신 호스트 사이에 영구불변의 경로를 배정한다.   
* 단점은 전송 경로가 고정되므로, 트래픽 변화에 따른 동적 경로 배정이 불가능하다는 점이다.   
* 그러나, 송수신 호스트 사이의 트래픽을 미리 측정하여 고정 경로를 적절히 배정하면 간단하고 효율적인 라우팅이 가능하다.   

예를 들어 다음 그림과 같은 네트워크를 가정해보자.   
<img src="https://user-images.githubusercontent.com/83942393/128703384-2c694242-9fcf-4e30-a2af-1b146db25e2e.png" width="45%" height="45%"></img> <img src="https://user-images.githubusercontent.com/83942393/128703424-84a9028f-8d8c-4a29-911a-b67fca3c601f.png" width="45%" height="45%"></img>

* 라우터 주위의 숫자는 연결하는 라우터의 포트 번호이다.
* 각 라우터가 관리하는 라우팅 정보는 표처럼 결정되는데, 경로 배정은 네트워크를 연결하는 선로의 전송 용량이나 네트워크 간의 데이터 전송량을 측정해 이루어진다.
* 그림에서는 라우터 R3과 R7로 연결한 선로가 다른 선로보다 고속 통신을 지원하며, 라우터 R1, R4, R6이 연결된 네트워크 Net.2가 라우터 R2, R5, R8 쪽의 네트워크 Net.4보다 덜 붐빈다고 가정하였다.
</br>

* 라우팅 테이블의 값은 목적지 네트워크의 주소와 해당 목적지로 향하는 경로 위에 있는 다음 라우터의 주소이다.
* 각 네트워크 내부에 존재하는 호스트에도 그림과 같은 형태의 라우팅 테이블이 존재한다.
```
예를 들어, Net.1에 존재하는 호스트가 Net.5에 존재하는 호스트에 데이터를 전송한다고 가정하자.

먼저 Net.1에 존재하는 호스트의 라우팅 테이블에 목적지가 Net.5인 데이터는 라우터 R1로 전송하라고 되어 있다면, 해당 데이터는 R1으로 간다.
라우터 R1의 라우팅 테이블을 보면, Net.5로 가는 데이터는 라우터 R6으로 중개하도록 되어 있으므로, 데이터는 라우터 R6으로 전달된다.

최종 경로는 R1 -> Net.2 -> R6 -> Net.5 순서이다.
```
</br>

### 3.2 적응 경로 배정
고정 경로 배정에서 라우팅 테이블의 경로 정보 변경은 네트워크 구성이 변경된 경우에만 가능하다.   
인터넷에서 사용되는 라우터는 **적응 경로 배정** (Adaptive Routing)을 채택한다.   

적응 경로 배정에서는 인터넷 연결 상태가 변하면 이를 데이터그램의 전달 경로에 반영한다.   
이때 결정에 영향을 주는 요소는 크게 두 가지이다.   
하나는 특정 네트워크나 라우터가 정상적으로 동작하지 않는 경우이고,   
다른 하나는, 네트워크의 특정 위치에서 혼잡이 발생하는 경우이다.   

적응 경로 배정은 이론적인 타당성에도 불구하고, 가볍게 넘길 수 없는 단점이 있다.   
경로를 결정하는 과정이 복잡해지면 이를 처리하는 라우터의 부담이 증가하는데, 인터넷처럼 복잡한 망에서 이것은 상당히 부담스러운 작업이다.   

네트워크에서의 변화는 내부적으로, 상태 정보에 대한 처리를 수반한다.   
그러나 특정 위치에서 어떤 변화가 발생했을 때, 네트워크의 모든 라우터에 동시 반영하는 것은 현실적으로 불가능하므로, 라우터들끼리 불일치성(Inconsistency)이 발생할 수 있다.   
이러한 불일치성을 해소하려면 라우터 사이의 정보 교환이 빠르게 자주 이루어져야 한다.    
하지만 이것은 네트워크 트래픽을 증가시키고, 라우터의 처리 부담을 증가시키는 결과를 초래한다.   
</br>

### 3.3 자율 시스템
라우팅 프로토콜과 관련해 자율 시스템(Autonomous System)이라는 개념이 존재한다.   
자율 시스템은 다수의 라우터로 구성할 수 있으며, 라우터들은 서로 공통의 라우팅 프로토콜을 사용해 정보를 교환한다.   
자율 시스템은 동일한 라우팅 특성에 의해 동작하는 논리적인 단일 구성체라고 볼 수 있다.   

자율 시스템 내부에서 사용하는 공통 프로토콜을 **내부 라우팅 프로토콜** (IRP, Interior Routing Protocol)이라 하며, 라우터끼리 라우팅 정보를 교환하는 용도로 사용한다.   

학교 같은 인터넷 환경에서는 각 건물을 라우터로 연결해 자율 시스템을 구성할 수 있고, 그림과 같이 외부의 자율 시스템과도 연결한다.
<img width="519" alt="스크린샷 2021-08-09 오후 9 43 33" src="https://user-images.githubusercontent.com/83942393/128707946-45eac333-7819-41e9-a557-00eda2f41dde.png">

이러한 구조에서는 자율 시스템이 사용하는 알고리즘과 라우팅 테이블 정보의 구조가 다를 수 있으므로, 자율 시스템 사이의 연동을 위한 방안을 고려해야 한다.   
자율 시스템들 간에 사용하는 라우팅 프로토콜을 일반적으로 **외부 라우팅 프로토콜**(ERP, Exterior Routing Protocol)이라 한다.   

그림에서 동일한 자율 시스템에 위치한 라우터 사이에는 내부 라우팅 프로토콜을 사용하고, 서로 다른 자율 시스템을 연결하는 라우터 사이에는 외부 라우팅 프로토콜을 사용한다.   
내부 라우팅 프로토콜에는 RIP, OSPF 등이 있고, 외부 라우팅 프로토콜에는 BGP 등이 있다.   
</br>

### 💎 04 서비스 품질(QoS)
네트워크에서의 품질(Quality)이란, 보통 데이터를 어느 정도로 신뢰성 있게 전송하는지를 의미한다.   
즉, 전송 과정에서의 데이터 분실, 전송 지연, 지연 값의 일관성(지터) 등을 기준으로 전송 품질을 판단할 수 있다.   
 
네트워크가 사용자에게 제공하는 서비스는 매우 다양하기 때문에, 네트워크 서비스 품질을 한마디로 규정하기는 어렵다.   
하지만 네트워크 서비스 제공자와 사용자 사이의 기본 서비스 품질은 특정 네트워크 서비스를 사용자에게 제공하는지 여부에서 출발한다.   
그리고 이를 바탕으로 서비스를 이용하는 데 있어서, 네트워크가 서비스의 특성에 부합하도록 어느 수준까지 올바르게 동작하는지를 판단해야 한다.   

사용자에게 제공되는 네트워크 서비스를 등급에 따라 분류할 수 있는데, 이를 서비스 클래스라 한다.   
서비스 클래스와 서비스 품질은 비슷한 의미로 해석할 수 있지만, 서비스 클래스가 서비스를 좀 더 세부적으로 분류하는 반면에, 서비스 품질은 포괄적이다.   

### 1. QoS 개요
인터넷 환경에서 전송 서비스 문제를 다루는 Qos(Quality of Service)는 중요한 고려 대상 중 하나이다.   
전송 서비스의 좋고 나쁨을 판단하는 기준은 사용자의 관점에 따라 다양하지만, 대부분 QoS로 정의할 수 있다.  
Qos 기준은 보통 연결형 서비스을 위한 것이지만, 비연결형 서비스에도 부분적으로 적용된다.   

Qos는 주로 전송 계층 사용자가 요청하므로 전송 계층 연결을 설정할 때 필요한 서비스의 정도를 매개변수로 표시한다.   
Qos 서비스를 지원하려면 전송 계층에 해당 기능을 구현해야 하는데, 하위의 네트워크 계층이 기능의 일부를 수행할 수 있으면 전송 계층의 역할이 그만큼 줄어든다.   
자주 언급되는 Qos 매개변수는 다음과 같다.   
</br>

> 연결 설정 지연
* 연결 설정 지연(Connection Establishment Delay)은 연결 설정을 위한 request 프리미티브 발생과 confirm 프리미티브 도착 사이의 경과 시간이다.
* 일반적으로 경과 시간이 짧을수록 서비스 품질이 좋으며, 네트워크 혼잡도 등의 영향을 많이 받는다.
* 연결 해제 요구에도 동일한 기준을 적용할 수 있다.
</br>

> 연결 설정 실패 확률
* 연결 설정 실패 확률(Connection Establishment Failure Probability)은 임의의 최대 연결 설정 지연 시간을 기준으로 연결 설정이 이루어지지 않을 확률이다.
* 연결 해제 요구에도 동일한 기준을 적용할 수 있다.
</br>

> 전송률
* 전송률(Throughput)은 임의의 시간 구간에서 초당 전송할 수 있는 바이트 수이다.
* 전송률은 양방향 값이 다를 수 있으므로, 별개로 다루어져야 한다.
</br>

> 전송 지연
* 전송 지연(Transit Dalay)은 송신 호스트가 전송한 데이터가 수신 호스트에 도착할 때까지 경과한 시간이다.
* 전송률처럼 양방향이 따로 다루어진다.
</br>

> 전송 오류율
* 전송 오류율(Residual Error Rate)은 임의의 시간 구간에서 전송된 총 데이터 수와 오류 발생 데이터 수의 비율이다.
</br>

> 우선순위
* 우선순위(Priority)는 다른 연결보다 먼저 처리함을 의미한다.
* 우선순위가 높은 연결이 우선순위가 낮은 연결보다 좋은 서비스를 제공받는다.
</br>

### 2. 인터넷에서의 QoS
IP 프로토콜은 원칙적으로 모든 패킷에 대해 동일한 기준을 적용해 목적지까지 데이터를 중개한다.   
특히, 데이터의 도착 순서나 데이터의 100% 수신 등을 보장하지 않기 때문에 버퍼를 사용해 이 문제를 해결한 후에 응용 계층으로 전달해야 한다.  
IP 프로토콜을 이용해 실시간 서비스를 제공하려면 약간의 시간을 미리 확보해 데이터를 버퍼에 저장하는 작업이 선행되어야 한다.   
따라서 첫 번째 데이터가 응용 환경에 전달되는 시점은 전송 지연시간보다 더 늦어진다.

QoS에서의 전송 데이터를 특징에 따라 여러 종류로 분류한다.   
예를 들어, 영상 데이터 등은 대용량 실시간 전송이 필요하지만, 전송 오류 문제에는 상대적으로 관대하다.   
그에 비해, 일반 컴퓨터 데이터는 실시간 기능이 필요 없지만, 전송 오류에 매우 민감하다.   
IP 프로토콜에는 특정 패킷의 우선순위를 조절하는 기능이 존재하지 않으므로, 모든 패킷을 동일한 기준으로 처리한다는 단점이 있다.   

IP 프로토콜에서 QoS를 지원하려면 각 패킷을 서로 다른 QoS 기준으로 구분할 수 있어야 하고, 라우터에서 이를 처리해야 한다.   
또 사용하는 대역의 요구 조건에 따라 패킷을 구분하고, 네트워크 자원의 할당도 그에 부합해야 한다.   















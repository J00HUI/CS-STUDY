### 🔆 요약

#### 01 데이터 링크 계층의 역할
데이터 링크 계층은 물리적 전송 매체에 의해 일대일로 직접 연결된 호스트 사이의 오류 제어와 흐름 제어 기능을 제공한다. 송신 호스트에서 전송한 프레임은 점대점으로 직접 연결된 수신 호스트에 라우팅 과정 없이 전달된다.
하나의 호스트가 다수의 호스트와 연결된 비대칭 형태의 구조를 멀티 드롭 방식이라 한다. 멀티 드롭에서는 하나의 물리 매체를 여러 호스트가 공유하므로, 임의의 호스트에서 전송한 프레임은 물리적으로 다른 모든 호스트에 전달된다.
멀티 드롭을 지원하려면 여러 수신 호스트 중에서 프레임의 목적지 호스트를 지칭하기 위한 주소 개념이 필요하다.

#### 02 프레임의 종류
데이터 링크 계층에서 전송 오류를 해결하는 과정에서 사용하는 프레임에는 정보 프레임, 긍정 응답 프레임, 부정 응답 프레임이 있다. 정보 프레임은 상위 계층이 전송을 요구한 데이터를 수신 호스트에 전송하는 용도로 사용한다.
정보 프레임을 수신한 호스트는 맨 먼저 프레임의 내용이 깨졌는지 확인해야 한다. 프레임 변형 오류가 발생하지 않으면 송신 호스트에 해당 프레임을 올바르게 수신했다는 의미로 긍정 응답 프레임을 회신한다. 정보 프레임의
전송 과정에서 프레임 변형 오류가 발생하면 수신 호스트는 송신 호스트에 부정 응답 프레임을 회신한다.

#### 03 슬라이딩 윈도우 프로토콜
슬라이딩 윈도우 프로토콜은 두 호스트 간의 프레임 전송을 위한 일반적인 통신 프로토콜로, 오류 제어와 흐름 제어 기능을 함께 지원한다. 정보 프레임을 전송하는 송신 호스트는 보내려는 데이터뿐 아니라 프레임의 순서 번호,
오류 검출 코드 등을 프레임에 표기한 후에 정해진 순서 번호에 따라 순차적으로 송신한다. 송신 호스트는 송신한 정보 프레임을 자신의 내부 버퍼에 유지해야 하며, 이를 송신 윈도우라 한다. 수신 호스트는 수신한 정보 프레임을
보관하기 위해 내부 버퍼인 수신 윈도우를 유지할 수 있다.

#### 04 연속형 전송
각각의 정보 프레임에 대하여 긍정 응답 프레임을 받지 않고도 여러 정보 프레임을 연속으로 전송하는 기능을 연속형 전송이라 한다. 전송된 정보 프레임을 위한 ACK 프레임의 회신이 이루어지지 않은 상태에서 다음 프레임을 전송하는
방식은 전송 오류의 발생 가능성이 적은 환경에서는 상당히 효율적이다. 연속형 전송 방식의 오류를 해결하는 방식에는 고백 N 방식과 선택적 전송 방식이 있다. 

#### 05 피기배킹
양방향 전송 기능을 갖는 채널 방식에서는 송신 호스트와 수신 호스트의 구분 없이 양방향으로 동시에 정보 프레임과 응답 프레임을 교차하여 전송할 수 있다. 이때 정보 프레임의 구조를 적당히 조정하여 재정의하면 정보 프레임을
전송하면서 응답 기능까지 함께 수행할 수 있다. 이런 방식으로 프로토콜을 작성하면 응답 프레임의 전송 횟수를 줄이는 효과가 있어 전송 효율을 높일 수 있는데, 이를 피기배킹이라 한다.

#### 06 HDLC 프로토콜
HDLC 프로토콜은 컴퓨터가 일대일 혹은 일대다로 연결된 환경에서 데이터의 송수신 기능을 제공한다. 데이터 통신을 위해 연결된 호스트들은 주국과 종국으로 구분되고, 다시 이들의 기능을 모두 지닌 혼합국으로 정의된다.
주국에서 전송되는 메시지를 명령이라 하며, 이에 대한 종국의 회신을 응답이라 한다. 




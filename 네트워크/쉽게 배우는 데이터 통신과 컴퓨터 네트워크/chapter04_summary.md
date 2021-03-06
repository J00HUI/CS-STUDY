### 🔆 요약

#### 01 전송과 교환
송신 호스트가 수신 호스트에 데이터를 전달하려면 전송과 교환 과정을 거쳐야 한다. 교환은 전달 경로가 둘 이상일 때 라우터에서 데이터를 어느 방향으로 전달할지를 선택하는 기능으로, 데이터를 올바른 경로로 전달할 수 있도록
해준다. 전송은 물리 매체에 의하여 일대일로 직접 연결된 두 시스템 간의 신뢰성 있는 데이터 전송을 보장하기 위한 것이다. 전송에는 라우팅 개념이 포함되지 않는다.

#### 02 점대점 방식
점대점 방식 네트워크에서는 교환 호스트가 송수신 호스트의 중간에 위치한다. 호스트는 전송 매체를 이용해 일대일로 직접 연결되므로, 모든 호스트가 점대점 연결을 통해 네트워크를 확장한다. 점대점 방식은 전체 연결 개수가 많아지면
성능 면에서 유리하지만 전송 매체의 길이가 증가해 비용이 많이 든다. 반대로 연결 개수가 적어지면 전송 매체를 더 많이 공유해 네트워크 혼잡도가 증가한다.

#### 03 브로드캐스팅 방식
브로드캐스팅 방식은 특정 호스트가 전송한 데이터가 네트워크에 연결된 모든 호스트에 전달된다는 특징이 있다. LAN에서는 데이터를 목적지 호스트까지 얼마나 효율적으로 전달할 수 있는지가 중요한 잣대가 된다. 이를 지원하는
브로드캐스팅 방식은 네트워크의 모든 호스트를 하나의 전송 매체로 연결하므로, 중개 기능을 수행하는 교환 호스트가 필요 없다.

#### 04 멀티캐스팅
송신 호스트를 기준으로, 수신 호스트 하나와 연결되면 유니포인트이고, 다수의 수신 호스트와 연결되면 멀티포인트가 된다. 송신 호스트가 한 번의 전송으로 수신 호스트 하나에만 데이터를 전송할 수 있으면 유니캐스팅이고,
다수의 수신 호스트에 전송할 수 있으면 멀티캐스팅이다. 멀티캐스팅을 구현하려면 멀티캐스트 그룹을 생성하고 관리하는 기능이 반드시 필요하다. 또 멀티캐스트 데이터를 중개하는 라우터에서 멀티캐스트 그룹 주소를 인식하고,
다수의 수신 호스트에 중개하는 등이 멀티캐스트 트래픽에 대한 처리 기능도 구현되어야 한다.

#### 05 수신 호스트의 응답 프레임
수신 호스트는 송신 호스트가 전송한 데이터 프레임의 일부가 깨지는 프레임 변형 오류를 확인하면 송신 호스트에 응답 프레임을 전송해 원래의 데이터 프레임을 재전송하도록 요구할 수 있다. 수신 호스트가 전송하는 응답 프레임의
종류는 두 가지이다. 하나는 데이터 프레임이 정상적으로 도착했을 때 회신하는 긍정 응답 프레임이고 다른 하나는 데이터 프레임이 깨졌을 때 회신하는 부정 응답 프레임이다. 송신 호스트의 재전송 기능은 수신 호스트의 부정 응답
프레임 회신에 의해 이루어진다.

#### 06 송신 호스트의 타임아웃 기능
송신 호스트가 전송한 데이터 프레임이 수신 호스트에 도착하지 못하는 프레임 분실 오류가 발생하면 수신 호스트는 이 사실을 인지할 수 없다. 따라서 오류 복구 과정은 송신 호스트의 주도로 이루어져야 한다. 송신 호스트는 데이터
프레임을 전송한 후에 일정 시간 이내에 수신 호스트로부터 긍정 응답 프레임 회신이 없으면 타임아웃 기능을 동작시켜 데이터 프레임을 재전송한다.

#### 07 순서 번호 기능
수신 호스트가 보낸 긍정 응답 프레임을 분실하면 데이터 프레임이 제대로 도착했어도 송신 호스트가 이를 인지할 수 없다. 따라서 송신 호스트가 타임아웃 기능에 의해 원래의 프레임을 재전송함으로써 수신 호스트가 데이터 프레임을
중복 수신하는 결과를 초래한다. 이럴 때 수신 호스트가 중복 데이터 프레임을 가려내려면 각 프레임 내부에 순서 번호를 기록해야 한다.

#### 08 흐름 제어
오류 제어와 함께 데이터 링크 계층에서 제공하는 주요 기능은 전송 데이터 프레임의 속도를 조절하는 것이다. 송신 호스트는 수신 호스트가 감당할 수 있을 정도의 전송 속도를 유지하면서 데이터 프레임을 전송해야 하는데, 이러한 
기능을 흐름 제어라 한다. 흐름 제어의 기본 원리는 수신 호스트가 다음에 수신할 프레임의 전송 시점을 송신 호스트에 통지하는 방식이다.

#### 09 프레임
데이터 링크 계층에서는 전송 데이터를 프레임(Frame) 이라는 작은 단위로 나누어 처리한다. 전송 프레임에는 상위 계층에서 보낸 전송 데이터의 오류를 확인하기 위한 체크섬(Checksum), 송수신 호스트의 주소, 기타 프로토콜에서 
사용하는 제어 코드 같은 정보가 포함된다. 프레임을 전송받은 수신 호스트는 제일 먼저 체크섬을 확인해 전송 중에 프레임 변형 오류가 발생했는지 확인해야 한다. 오류가 발생하면 부정 응답 프레임을 회신하여, 송신 호스트가 
원래의 데이터를 재전송하도록 요구함으로써 복구 과정을 시작해야 한다.

#### 10 문자 프레임
문자 프레임은 프레임의 내용이 문자로 구성되므로 문자 데이터를 전송할 때 사용한다. 하나의 프레임 단위를 구분하기 위해 프레임의 앞뒤에 ASCII 코드의 특수 문자를 이용한다. 즉, 각 프레임의 시작 위치에 DLE, STX 문자를
추가하고, 끝나는 위치에는 DLE, ETX를 추가해 프레임의 다른 정보와 구분할 수 있도록 한다. 문자 스터핑은 문자 프레임 내부의 전송 데이터에 DLE 문자가 포함되면서 발생하는 혼란을 예방하는 방법이다.

#### 11 비트 프레임
비트 프레임 방식은 임의의 비트 패턴 데이터를 지원하는데, 프레임의 시작과 끝 위치에 플래그라는 특수하게 정의된 비트 패턴(01111110을 사용해 프레임 단위를 구분한다. 비트 프레임 방식에서는 송신 호스트가 전송하고자 하는
데이터의 내용 중에 값이 1인 패턴이 연속해서 5번 발생하면 강제로 0을 추가해 전송한다. 이는 플래그 패턴에서 1이 연속해 6개가 나오므로 원천적으로 데이터 내용에 플래그 패턴이 나타나는 것을 차단하기 위함이다. 이와 같은 
기능을 비트 스터핑이라 한다.

#### 12 다항 코드
CRC라고도 알려진 다항 코드 방식은 버스트 에러 형태의 오류를 검출하는 확률이 높은 것으로 알려져 있다. 송신 호스트가 전송할 데이터가 m비트의 M(x)라면 데이터 전송 과정에서 n+1비트의 생성 다항식 G(x)를 사용해 오류
검출 코드를 생성함으로써 오류 제어 기능을 수행한다. 송신 호스는 전송 데이터 M(x)를 생성 다항식 G(x)로 나누어 체크섬 정보를 얻는다. 나누기 연산 과정에서는 전송 데이터 뒤에 나머지를 보관할 n비트의 공간을 확보하고, 
이 자리를 모두 0으로 채운 후에 나누기 연산을 수행한다. 연산에서 얻은 나머지 값을 체크섬이라 정의하며, 체크섬을 전송 데이터의 뒤에 추가해 수신 호스트에 전송해야 한다. 

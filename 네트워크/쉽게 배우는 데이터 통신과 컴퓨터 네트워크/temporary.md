### DHCP 프로토콜 주요 메시지
* DHCP 프로토콜의 동작 과정에 필요한 주요 메시지의 종류는 다음과 같으며, 이는 Options 필드에 의하여 구분된다.    
* DHCP 메시지는 UDP 데이터그램에 캡슐화되어 전송되며, 클라이언트의 포트 번호는 68, DHCP 서버의 포트 번호는 67이다.    
   
![image](https://user-images.githubusercontent.com/83942393/131071921-88475899-f346-487f-8cc5-8cb4fda8486f.png)</br>
</br>

* **DHCP_DISCOVER** : 클라이언트가 DHCP 서버를 찾기 위해 전송하는 브로드캐스팅 메시지이며, Transaction Identifier 에 특정한 값을 지정한다. 클라이언트는 IP 주소 값이 없으므로 하부의 IP 프로토콜 송신자의 IP 주소는 0.0.0.0으로 지정한다. 클라이언트가 DHCP 서버의 IP 주소를 모르므로 수신자의 IP 주소는 브로드캐스팅 주소인 255.255.255.255 로 지정한다.
* **DHCP_OFFER** : 클라이언트의 DHCP_DISCOVER 메시지에 대한 응답으로 DHCP 서버가 응답하는 메시지이다. Your IP Address 필드에 권고하는 IP 주소를 지정하고, Server IP Address 필드에는 서버의 IP 주소를 지정한다. 아직 클라이언트의 IP 주소가 결정되지 않았으므로 IP 패킷은 브로드캐스팅 형식으로 전송된다.
* **DHCP_REQUEST** : 클라이언트는 여러 서버로부터 다수의 DHCP_OFFER를 받을 수 있기 때문에 이 중에서 적당한 IP 주소를 선택해야 한다. 그리고 이 주소를 권고한 DHCP 서버에 DHCP_REQUEST 메시지를 전송하여 권고한 주소를 사용한다고 알려준다.
* **DHCP_ACK** : 클라이언트로부터 DHCP_REQUEST 메시지를 받은 DHCP 서버는 권고한 IP 주소가 최종적으로 사용 가능한지를 판단한다. 사용 가능하면 DHCP_ACK 메시지를 전송한다.
* **DHCP_NACK** : DHCP 서버는 동일한 IP 주소를 여러 클라이언트에 권고할 수 있다. 따라서 다른 클라이언트가 IP 주소를 선점한 경우 DHCP_ACK 메시지를 회신할 수 없다. 이떄는 DHCP_NACK 메시지를 전송해 클라이언트가 DHCP_DISCOVER 과정을 다시 하도록 해야 한다.
</br>

DHCP 메시지를 사용하여 클라이언트가 DHCP 서버로부터 IP 주소를 얻는 과정은 그림과 같다.    
* 먼저, 클라이언트가 DHCP_DISCOVER 메시지를 전송하고, 이어서 DHCP 서버로부터 211.223.201.99 로 권고된 IP 주소를 받는다.
* 세 번째의 DHCP_REQUEST 메시지를 이용하여 권고된 IP 주소를 사용하겠다는 의사 표시에 대하여 DHCP 서버로부터 긍정 응답을 받고 있다. 
</br>

<그림 p.256>

DHCP 메시지가 UDP와 IP 프로토콜로 캡슐화되어 전송되는 과정은 다음 그림과 같다.    
<그림 p.257>

* UDP 헤더에서 보이는 것처럼 DHCP 서버의 포트 번호는 67이고, 클라이언트는 68을 사용한다.
* IP 헤더에는 IP 주소를 표기해야 하는데, 목적지 IP 주소를 255.255.255.255 로 지정하여 브로드캐스팅 전송을 하고 있다.
* DHCP_DISCOVER 메시지를 전송하는 송신자의 IP 주소는 없으므로 0.0.0.0 을 지정한다.
</br>


   

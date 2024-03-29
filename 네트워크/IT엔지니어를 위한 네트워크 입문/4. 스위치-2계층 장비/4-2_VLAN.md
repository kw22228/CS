### VLAN

- 하나의 물리 스위치에서 여러 개의 네트워크를 나누어 사용할 수 있는 가상화 기술.

#### VLAN 이란?

- 물리적 배치와 상관없이 LAN을 논리적으로 분할, 구성하는 기술이다.
  기업과 같이 여러 부서가 함께 근무하면서 각 부서별로 네트워크를 분할할 때는 네트워크를 여러 개 운영해야 한다.
- 아예 서로 다른 네트워크를 갖도록 논리적으로 분할한 것이므로 유니캐스트 뿐만아니라 브로드캐스트도 분할된 VLAN간에 통신할 수 없다.
  통신하기 위해서는 완전히 서로 다른 네트워크 이므로 3계층 장비가 필요하다.

#### VLAN의 종류와 특징

- 포트 기반의 VLAN

  - 스위치를 각 포트를 논리적으로 분할하여 사용하는것이 목적이다.
  - 우리가 언급하는 대부분의 VLAN은 포트기반의 VLAN이다.

- MAC기반의 VLAN (다이나믹 VLAN)

  - 스위치의 고정포트에 VLAN을 할당하는 것이 아니라, 스위치에 열결되는 단말의 MAC주소를 기반으로 VLAN을 할당한다.
    단말이 연력되면 해당 단말의 MAC주소를 인식한 스위치가 해당 포트를 지정한 VLAN으로 변경한다.

#### VLAN 모드(Trunk/Access) 동작 방식

- 포트 기반 VLAN에서는 각 VLAN이 한대의 스위치에 연결되더라도 서로 다른 VLAN은 통신이 불가능하다. (완전히 서로 다른 네트워크 이기 때문)
  따라서, VLAN끼리 통신하기 위해서는 라우터 같은 3계층 장비가 필요함.
- 하지만, 태그 포트를 이용한 스위치를 사용하면 서로 다른 VLAN들을 하나의 포트로 지원하여 스위치간의 VLAN통신이 가능하게 된다.
  같은포트에서 전송하기때문에 출발지, 도착지 MAC주소와 VLAN ID를 같이 보낸다.

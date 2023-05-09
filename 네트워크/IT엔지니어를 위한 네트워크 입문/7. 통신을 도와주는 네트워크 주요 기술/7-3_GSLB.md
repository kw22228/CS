### GSLB

- DNS에서 동일한 레코드 이름으로 서로 다른 IP 주소를 동시에 설정할 수 있다. 도메인 질의에 따라 응답받는 IP주소를 나누어 로드밸런싱할 수 있음. (DNS 로드밸런싱)
  하지만 DNS서버는 해당 서버의 서비스 상태가 정상인지 여부를 확인하지 않고 무조건 던져주기 때문에 위험요소가 있다.
  이러한 문제를 해결하기 위해 GSLB 라는 기술이 나왔다.

- GSLB(Global Server/Service Load Balancing)란?
  - 동일한 레코드로 서로 다른 IP주소를 동시에 설정해 로드밸런서처럼 등록된 도메인에 연결된 서비스가 정상적으로 가동되고 있는지 헬스 체크를 수행해준다.
    이로 인해서 DNS서버에서 정상이던 장애나는 서버던 무조건 던져주는 문제를 해결할 수 있다.
  - 인텔리전스 DNS라고도 불린다.

#### GSLB 동작 방식

- 현재 서비스가 가동중인 리얼 서버는 서울과 부산의 데이터센터에 가동중인것으로 가정함.

1. 사용자가 web.zigispace.net에 접속하기 위해 DNS에 질의한다.
2. LDNS는 web.zigispace.net을 관리하는 NS 서버를 찾기 위해 root부터 순차 질의한다.
3. zigispace.net을 관리하는 NS서버로 web.zigispace.net에 질의한다.
4. DNS 서버는 GSLB로 web.zigispace.net에 대해 위임하여 GSLB가 NS서버라고 LDNS에 응답.
5. LDNS는 다시 GSLB로 web.zigispace.net에 대해 질의한다.
6. GSLB는 web.zigispace.net에 대한 IP 주솟값 중 현재 정상적으로 가동하는 데이터센터 서버값을 LDNS에 응답한다. (1.1.1.1)
7. 클라이언트에 1.1.1.1을 응답해준다.

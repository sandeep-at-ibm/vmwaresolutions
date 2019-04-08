---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# VMware HCX on IBM Cloud 포트 액세스 요구사항
{: #hcx-archi-port-req}

HCX는 공용 인터넷 및 사설 회선을 순회하고 네트워크, 스위치 및 포트 그룹과 같은 데이터 센터 컴포넌트에 연결해야 합니다.

다음 표에는 하이브리드 클라우드 서비스 가상 어플라이언스가 설치될 수 있도록 열려 있어야 하는 포트가 나열되어 있습니다. vSphere 환경 및 IBM Cloud 환경은 모두 vSphere 온프레미스 디바이스와 IBM Cloud 사이에 NTP(Network Time Protocol) 클록 동기화를 허용해야 합니다. UDP 포트 123은 하이브리드 클라우드 서비스 가상 어플라이언스 및 네트워크에 액세스할 수 있어야 합니다. 설치된 NTP 서버는 하이브리드 클라우드 서비스 어플라이언스가 설치될 때 지정될 수 있습니다.

표 1. 포트 액세스 요구사항

| 소스 | 대상       | 포트 | 프로토콜 | 용도         |서비스 |
|--------|--------------|------|----------|-----------------|----------|
|HCX    | 고객 DNS | 53   | TCP/UDP  | 이름 분석 |DNS      |
|HCX    | IBM Cloud의 NSX LB | 443 | TCP | 등록 서비스 | HTTPS |
|HCX    | IBM Cloud의 vCenter | 443 | TCP | HCX REST 서비스 | HTTPS |
|HCX    | IBM Cloud의 PSC | 443 | TCP | HCX REST 서비스 | HTTPS |
|HCX    | connect.hcx.vmware.com | 443 | TCP | 등록 서비스 | HTTPS |
| 웹 브라우저 |HCX | 9443 | TCP | HCX 시스템 구성을 위한 HCX 가상 어플라이언스 관리 인터페이스 | HTTPS |
| 관리자 네트워크 |HCX | 22 | SSH | 하이브리드 클라우드 서비스에 대한 관리자 SSH 액세스 | SSH |
|HCX | ESXi 호스트 | 902 | TCP | IBM Cloud의 HCX에서 ESXi 호스트로 관리 및 프로비저닝 지시사항 전송 |내부 |
|HCX | vCenter SSO 서버 | 7444 | TCP | vSphere 검색 서비스 |  |
|HCX | NTP 서버 | 123 | UDP | 시간 동기화 | |
|HCX | Syslog |   | 구성된 사용자 | HCX(클라이언트)와 Syslog 서버 간의 연결. Syslog 포트 및 프로토콜의 값이 vSphere Web Client에 지정되어 있습니다. 예를 들어, UDP 프로토콜의 경우에는 포트 514입니다. | |
|HCX |클라우드 게이트웨이 | 8123 | TCP | 하이브리드 클라우드 게이트웨이에 호스트 기반 복제 서비스 지시사항 전송 | HTTP |
|HCX |클라우드 게이트웨이 | 9443 | TCP | REST API를 사용하여 로컬 하이브리드 클라우드 게이트웨이에 관리 지시사항 전송. | HTTP</br>HTTPS |
|클라우드 게이트웨이 | L2C | 443 | TCP | 클라우드 게이트웨이에서 L2C로 관리 지시사항 전송(L2C가 하이브리드 클라우드 게이트웨이와 동일한 경로를 사용하는 경우) | HTTP</br>HTTPS |
|클라우드 게이트웨이 | L2C | 8443 | TCP | 클라우드 게이트웨이에서 L2C로 양방향 관리 지시사항 전송(L2C가 대체 데이터 경로를 사용하는 경우) | HTTP</br>HTTPS |
| L2C | L2C(원격) | 443 | TCP | 클라우드 게이트웨이에서 L2C로 양방향 관리 지시사항 전송(L2C가 대체 데이터 경로를 사용하는 경우) | HTTP</br>HTTPS |
|클라우드 게이트웨이 | ESXi 호스트 | 80, 902  | TCP | 관리 및 OVF 배치 |내부 |
| ESXi 호스트 |클라우드 게이트웨이 | 31031, 44046 | TCP | 내부 호스트 기반 복제 트래픽 |내부 |
|클라우드 게이트웨이 | ESXi 호스트 | 8000  | TCP | vMotion(무중단 마이그레이션) |  |
| 클라우드 게이트웨이(로컬) |클라우드 게이트웨이</br>(원격) | 4500  | UDP | 양방향 터널의 워크로드를 캡슐화하는 인터넷 키 교환(IKEv2) | IPSEC |
| 클라우드 게이트웨이(로컬) |클라우드 게이트웨이</br>(원격) | 500  | UDP | 양방향 터널의 내부 키 교환(ISAKMP) | IPSEC |

## 관련 링크
{: #hcx-archi-port-req-related}

* [소스에 HCX 설치 및 구성](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)

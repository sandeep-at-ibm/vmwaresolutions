---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

# 초기 구성
{: #vum-init-config}

IC4VS 자동화는 기본 게이트웨이를 {{site.data.keyword.cloud}} BCR(Backend Customer Router)로 설정하여 VCSA를 구성합니다. 그러나 BCR을 통한 인터넷 연결 라우트는 존재하지 않습니다. VMware vCenter Server on {{site.data.keyword.cloud_notm}} 인스턴스에서 인터넷에 연결하는 표준 라우트는 관리 ESG를 통하는 것입니다. VCSA 또는 관리 ESG의 구성을 변경하는 것은 권장되지 않으므로 VUM을 사용으로 설정하려면 고객 서브넷에 프록시 서버를 구현하는 것이 좋습니다.

이 접근 방식은 VCSA 또는 관리 ESG를 재구성할 필요는 없지만 소규모의 가상 머신(VM) 또는 어플라이언스를 설치해야 함을 의미합니다. 프록시 서버는 두 엔드포인트 디바이스 사이에 있으며 중간 디바이스 역할을 하는 시스템입니다. 이 경우 VUM과 VMware의 업데이트 서버 사이에 위치합니다.

VUM이 VMware에 있는 업데이트 서버의 리소스를 요청하면 먼저 요청이 프록시 서버로 전송된 다음 프록시 서버가 해당 요청을 업데이트 서버로 전송합니다. 프록시 서버가 리소스를 얻은 후 해당 리소스를 VUM으로 전송합니다. 프록시 서버를 사용하여 보안, 관리 제어 및 캐싱 서비스를 용이하게 할 수 있습니다.

이 문서에서는 CentOS와 Squid에 기반한 프록시 서버 사용에 대해 설명합니다. 스퀴드 프록시는 웹용 오픈 소스 캐싱 프록시이며 HTTP 및 HTTPS를 포함하는 많은 프로토콜을 지원합니다. 사용 가능한 여러 VM 및 어플라이언스 기반 프록시가 있으며 엔터프라이즈 요구사항에 따라 적합한 프록시를 선택하고 공급업체의 지침에 따라 설치 및 구성해야 합니다. CentOS/Squid 구현을 사용하도록 선택하는 클라이언트는 다음 프로세스를 계속 진행해야 합니다.

* CentOS ISO를 점프 서버에 다운로드
* vCenter 라이브러리 작성
* ISO를 vCenter 라이브러리에 업로드
* VM 작성, CentOS 설치 및 구성, Squid 설치

이 태스크를 시작하기 전에 표 1을 채우기 위한 정보를 수집해야 합니다. 제안 값을 검토하고 제안 값이 엔터프라이즈에 적합한지 확인하십시오. 이 구성은 CentOS-Minimal 및 Squid를 사용하는 VUM 전용 소규모 프록시를 기반으로 합니다.

표 1. 배치 값

|매개변수 |제안 값 |참고 |
|:--------- |:-------------- |:------ |
|프록시 CPU |1개의 vCPU |Squid에는 최소 요구사항이 없음 |
|프록시 RAM |2GB |Squid에는 최소 요구사항이 없음 |
|프록시 디스크 |25GB |Squid에는 최소 요구사항이 없음 |
|호스트 이름 |Proxy01 | |
|주소 |프록시 IP |예비 IP 주소는 프로비저닝 프로세스 중에 지정된 고객의 사설 포터블 서브넷에서 사용되어야 합니다. 이 서브넷에는 두 개의 IP 주소만 예약되어 있을 수 있습니다(하나는 BCR용, 다른 하나는 customer-esg용).
|넷마스크 |255.255.255.192 | |
|게이트웨이| customer-nsx-edge private uplink ip | customer-nsx-edge의 사설 업링크 주소인 프록시 서버에 대한 기본 게이트웨이 설정입니다. IP 주소는 **customer-nsx-edge**에 대한 **설정** 탭을 검토하여 찾을 수 있습니다. |
|DNS 서버 |AD/DNS ip |이 IP 주소는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 있는 인스턴스 페이지 **리소스** 페이지에서 찾을 수 있습니다. |
|BCR IP |bcr ip |{{site.data.keyword.cloud_notm}} Backend Customer Router의 IP 주소이며 10.0.0.0/8 및 161.26.0.0/16의 게이트웨이입니다. 이 주소는 VCSA 및 AD/DNS 서버에 연결할 수 있도록 프록시 서버의 정적 라우트에 사용됩니다. |

## NSX 구성
{: #vum-init-config-config-nsx}

프록시 서버 트래픽을 사용으로 설정하려면 NSX 고객 ESG 방화벽 및 NAT 설정이 필요합니다.

### 방화벽
{: #vum-init-config-firewall}

1. **홈** > **네트워킹 및 보안**으로 이동하십시오.
2. **NSX Edge**, customer-nsx-edge를 선택한 후 **방화벽**을 선택하십시오.
3. **+** 기호를 클릭하고 방화벽 규칙을 추가하십시오.
4. 다음 표에 언급된 대로 필수 매개변수를 제공하십시오. 새 방화벽 규칙은 마지막 규칙인 기본 거부 규칙 앞에 와야 합니다.

표 2. 방화벽 규칙

|매개변수 |제안 값 |
|:--------- |:-------------- |
|이름 |아웃바운드 Proxy01 |
|유형 | User |
|소스 |프록시 서버 IP |
|대상 | any |
|서비스 |HTTP/HTTPS/ICMP Echo |
| 조치 | Accept |

매개변수가 제공된 후 **변경사항 공개**를 클릭하십시오.

### 프록시 서버 설치 및 구성
{: #vum-init-config-inst-cfg-proxy}

다음 프로세스는 컨텐츠 라이브러리에서 CentOS 및 Squid를 호스팅하기 위해 VM을 배치하며 다음 단계로 구성됩니다. 점프 박스로 사용하도록 프로비저닝된 Windows VSI가 있고 RDP(Remote Desktop Protocol)를 사용하여 VSI의 공용 인터페이스에 연결한다고 가정합니다.

* CentOS-Minimal ISO 파일 다운로드
* vCenter 컨텐츠 라이브러리를 구성하고 CentOS ISO 파일로 채우기
* 프록시 VM 구성, CentOS 및 Squid 설치

### CentOS-Minimal ISO 파일 다운로드
{: #vum-init-config-downloading-centos}

점프 서버에서 브라우저를 사용하여 [CentOS](https://www.centos.org/download/)에서 CentOS-Minimal ISO 파일을 다운로드하십시오. {{site.data.keyword.cloud_notm}}는 많이 사용하는 여러 Linux 배포판의 미러를 유지보수합니다. 이 미러는 사설 네트워크에서만 사용할 수 있으며 CentOS ISO는 `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`에서 사용할 수 있습니다.

### 컨텐츠 라이브러리를 구성하고 CentOS ISO 파일로 채우기
{: #vum-init-config-config-conent-library}

로컬 vCenter 컨텐츠 라이브러리를 작성하십시오. 라이브러리가 작성된 vCenter Server 인스턴스에서만 해당 라이브러리에 액세스할 수 있습니다. VM을 배치하는 데 필요한 템플리트 및 ISO로 라이브러리를 채우십시오.

1. vSphere Web Client를 사용하여 **홈** > **컨텐츠 라이브러리** > **오브젝트** > **새 컨텐츠 라이브러리 작성** > **vCenter에 구독 라이브러리 작성**으로 이동하십시오.
2. 컨텐츠 라이브러리의 이름(예: ISO)을 입력하고 참고 텍스트 상자에 라이브러리에 대한 설명을 입력한 후 **다음**을 클릭하십시오.
3. **로컬 컨텐츠 라이브러리**를 선택하고 **다음**을 클릭하십시오.
4. 데이터 저장소를 선택한 후 적합한 데이터 저장소(예: vsanDatastore)를 클릭하십시오.
5. **완료 준비** 페이지에서 정보를 검토하고 **완료**를 클릭하십시오.

### 프록시 VM 구성, CentOS 및 Squid 설치
{: #vum-init-config-config-proxy}

이 활동에는 다음과 같은 태스크가 있습니다.

*	새 VM 작성
*	CentOS 설치
*	Squid 설치

#### 새 VM 작성
{: #vum-init-config-create-new-vm}

이 태스크는 프록시 서버로 사용할 준비가 된 새 VM을 작성합니다. 표 1 배치 값의 설정을 사용하여 구성을 채워야 합니다.

1.	vSphere Web Client를 통해 **홈** > **VM 및 템플리트**로 이동하십시오.
2.	네비게이터 분할창에서 **datacenter1**을 클릭한 후 마우스 오른쪽 단추를 클릭하고 **새 가상 머신** > **새 가상 머신**을 선택하십시오.
3.	**새 가상 머신 작성**을 선택한 후 **다음**을 클릭하십시오.
4.	VM의 이름(예: Proxy01)을 입력하고 **datacenter1**을 선택한 후 **다음**을 클릭하십시오.
5.	**cluster1**을 선택한 후 **다음**을 클릭하십시오.
6.	적절한 데이터 저장소(예: vsanDatastore)를 선택하고 **다음**을 클릭한 후 **다음**을 다시 클릭하십시오.
7.	**게스트 OS 제품군**에서 **Linux**를 선택하고 **게스트 OS 버전**에서 **CentOS 7(64비트)**을 선택한 후 **다음**을 클릭하십시오.
8.	**CPU를 1로**, **메모리를 2048MB로**, **새 하드 디스크를 25GB로** 설정하십시오. **컨텐츠 라이브러리 ISO 파일** > **CentOS-7-x86_64-Minimal**을 선택하고 **확인**을 클릭한 후 **연결됨** 상자에 체크 표시를 하십시오.
9.	새 디바이스 상자에서 **네트워크**를 선택한 후 **추가**를 클릭하십시오.
10.	**SDDC-DPortGroup-Mgmt** 네트워크를 선택하고 연결 선택란에 체크 표시가 되어 있는지 확인한 후 **다음**을 클릭하십시오.
11.	검토한 후 **완료**를 클릭하십시오.

#### CentOS 설치
{: #vum-init-config-install-centos}

이 태스크는 Squid 설치를 위해 준비된 새로 작성된 VM을 설치하고 구성합니다.

1.	vSphere Web Client의 네비게이터 분할창에서 방금 작성한 **VM**, Proxy01을 선택한 후 **요약 탭**을 선택하십시오.
2.	**"재생"**을 클릭하여 VM에 전원을 공급하십시오.
3.	이제 VM에 전원이 공급되고 CentOS 7 ISO에서 부팅됩니다. **원격 콘솔 또는 웹 콘솔**을 VM으로 시작하십시오. 원격 콘솔을 설치해야 하며 웹 브라우저를 실행 중인 시스템이 vSphere ESXi 호스트를 이름으로 분석해야 합니다.
4.	CentOS 7 시작 화면에서 필수 언어를 선택하고 **계속**을 클릭하십시오.
5.	**현지화** 화면에서 **날짜 및 시간/MD:STRONG>을 클릭하고 시간대를 선택한 후 **완료**를 클릭하십시오.
6.	**현지화** 화면에서 필요한 경우 **키보드**를 클릭하여 기본값에서 변경한 후 **완료**를 누르십시오.
7.	**현지화** 화면에서 **설치 대상**을 클릭하고 **VMware 가상 디스크 아이콘**을 클릭한 후 **완료**를 클릭하십시오.
8.	**현지화** 화면에서 **네트워크 및 호스트 이름**을 클릭하고 호스트 이름을 선택한 호스트 이름(예: Proxy01)으로 변경하십시오.
9.	**구성**을 클릭한 후 **IPv4 설정**을 클릭하십시오. **방법** 상자에서 **매뉴얼**을 선택하십시오.
10.	**추가** 단추를 사용하여 _표 1 - 배치 값_의 _주소 넷마스크_ 및 _게이트웨이_를 삽입하십시오.
11.	표 1 - 배치 값의 _DNS 서버 IP 주소_를 입력하십시오.
12.	**라우트** 단추를 클릭하고 표 1 배치 값에 있는 _BCR IP 주소_의 게이트웨이 IP 주소가 게이트웨이로 사용하여 정적 라우트 _10.0.0.0/8 and 161.26.0.0/16_을 추가하십시오. 프록시 서버가 이 정적 라우트를 사용하여 DNS 서버에 연결할 수 있습니다.
13.	**저장**을 클릭한 후 이더넷 인터페이스가 설정되고 연결된 것으로 표시되는지 확인하십시오. **완료**를 클릭하고 **설치 시작**을 클릭하십시오.
14.	설치가 계속될 때 루트 비밀번호를 설정하고 사용자를 설정하십시오.
15.	설치가 완료되면 루트로 로그인한 후 _ping vmware.com_ 명령을 입력하십시오. 이름이 IP 주소로 해석되고 사용자는 응답을 받게 됩니다. 응답을 받지 못한 경우 IP 주소, 방화벽 규칙 및 NAT 설정을 확인하십시오.

#### Squid 설치 및 구성
{: #vum-init-config-install-cfg-squid}

Squid는 최소 하드웨어 요구사항을 갖추고 있지 않지만 프록시를 통해 RAM 용량은 인터넷에 액세스하는 사용자 및 캐시에 저장된 오브젝트에 따라 다를 수 있습니다. VUM에서만 프록시 서버에 액세스하고 캐시가 사용으로 설정되지 않았으므로 소규모 VM만 구성되었습니다.

1. vSphere Web Client에서 웹 콘솔 또는 원격 콘솔을 사용하여 사용자로 프록시 서버에 로그인 후 root로 `su`하십시오.
2. 패키지를 설치하기 전에 `yum -y update` 명령을 사용하여 시스템 및 패키지를 업데이트하십시오.

3. Squid가 기본 yum 저장소에서 사용 가능하지 않으므로 Squid를 설치하려면 시스템에 EPEL 저장소를 설치해야 합니다. `yum -y install epel-release` 명령을 실행하여 EPEL 저장소를 설치하십시오.

4. 다음 명령을 사용하여 업데이트하고 정리하십시오.

  `yum -y update`
  `yum clean all`

5. `yum -y install squid` 명령을 사용하여 Squid를 설치하십시오.
6. 설치된 후 `systemctl start squid` 명령을 사용하여 Squid를 즉시 시작하십시오.
7. `systemctl enable squid` 명령을 실행하여 부팅 시 Squid를 자동으로 시작하십시오.
8. `systemctl status squid` 명령을 실행하여 Squid가 실행 중인지 확인하십시오.
9. CentOS 방화벽은 다음 명령을 사용하여 Squid 포트, TCP 3128에 대한 액세스를 허용해야 합니다. `firewall-cmd –add-port=3128/tcp –permanent`
10.	규칙을 저장하고 서비스를 다시 시작하려면 `firewall-cmd –reload` 명령을 사용하십시오.

## VUM의 초기 설정
{: #vum-init-config-init-setup-vum}

프록시 서버를 사용하여 인터넷에서 저장소에 액세스하도록 VUM을 구성하십시오.
1. vSphere Web Client를 사용하여 **홈** > **Update Manager**로 이동하십시오. vCenter Server를 클릭하십시오.
2. **관리 탭**을 선택하고 **설정** 단추를 클릭하십시오.
3. **다운로드 설정**을 선택한 후 _프록시 설정_ 아래 **편집**을 클릭하십시오.
4. **프록시 사용** 상자를 선택하고 _프록시 서버 IP 주소_ 및 _포트 3128_을 입력한 후 **확인**을 클릭하십시오. 연결 상태가 _유효성 검증 중_으로 변경된 후 _연결됨_으로 변경됩니다.
5. **지금 다운로드**를 클릭하십시오. _최근 태스크_ 분할창에 이 활동이 완료됨으로 표시되어야 합니다.

## 관련 링크
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 디지털 기술 업무](https://ibm-dte.mybluemix.net/ibm-vmware)(데모)

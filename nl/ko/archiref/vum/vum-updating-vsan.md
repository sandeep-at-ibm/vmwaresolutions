---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# vSAN 클러스터 업데이트
{: #vum-updating-vsan}

vSAN은 VUM에 사용할 시스템 기준선 및 기준선 그룹을 생성합니다. 이러한 권장 기준선을 통해 vSAN을 사용 중인 {{site.data.keyword.cloud_notm}} 인스턴스의 VMware vCenter Server에서 ESXi 호스트에 대한 소프트웨어, 패치 및 확장을 업데이트할 수 있습니다. vSAN 6.6.1 이상은 vSAN 클러스터에 대한 자동화된 빌드 권장사항을 생성합니다. vSAN은 VMware 호환성 안내서 및 vSAN 릴리스 카탈로그의 정보와 설치된 vSphere ESXi 릴리스에 대한 정보를 결합합니다.

이러한 권장 업데이트는 하드웨어를 지원되는 상태로 유지하기 위해 사용 가능한 최상의 릴리스를 제공합니다.
* **vSAN 시스템 기준선** - vSAN 빌드 권장사항은 VUM에 대한 vSAN 시스템 기준선을 통해 제공됩니다. vSAN은 각 vSAN 클러스터마다 하나의 기준선 그룹을 생성하며 기준선 및 그룹 탭의 기준선 분할창에 나열됩니다. VUM이 자동으로 각 vSAN 클러스터를 스캔하여 기준선 그룹에 대한 준수를 확인합니다. 그러나 vSAN 클러스터를 업그레이드하려면 단일 호스트 또는 전체 클러스터에서 vSAN 시스템 기준선을 수정할 수 있는 VUM을 통해 수동으로 시스템 기준선을 수동으로 수정해야 합니다.
* **vSAN 릴리스 카탈로그** - vSAN 릴리스 카탈로그는 사용 가능한 릴리스, 릴리스에 대한 우선순위 및 각 릴리스에 필요한 중요 패치에 대한 정보를 유지보수합니다. vSAN에서 릴리스 카탈로그에 액세스하려면 인터넷 연결이 필요합니다. vSAN에서 릴리스 카탈로그에 액세스하기 위해 고객 환경 향상 프로그램(CEIP)에 등록할 필요가 없습니다.
* **vSAN 빌드 권장사항에 대한 작업** - VUM은 vSphere ESXi 릴리스를 VMware 호환성 안내서에 있는 하드웨어 호환성 목록(HCL)의 정보와 비교하여 검사합니다. 현재 vSAN 릴리스 카탈로그에 기반하여 각 vSAN 클러스터에 대한 올바른 업그레이드 경로를 판별합니다. 또한 vSAN은 권장 릴리스에 필요한 드라이버 및 패치 업데이트를 시스템 기준선에 포함시킵니다. vSAN 빌드 권장사항은 각 vSAN 클러스터가 현재 하드웨어 호환성 상태 또는 더 개선된 상태를 유지하도록 보장합니다. vSAN 클러스터의 하드웨어가 HCL에 포함되지 않은 경우 vSAN에서 최신 릴리스로 업그레이드하도록 권장합니다.

vSAN 클러스터 업그레이드는 다음과 같은 태스크 순서로 진행됩니다.
* **vSAN 온라인 상태 워크플로우 사용** – 이 워크플로우는 업데이트가 검토되고 수정될 수 있도록 VUM에서 vSAN 기준선을 사용으로 설정합니다. 이 워크플로우는 처음에 VUM에서 vSAN을 사용하도록 설정하기 위해서만 수행되어야 합니다.
* **전제조건** – 전제조건, 프로세스 및 제한사항을 이해합니다.
* **vCenter Server 어플라이언스 업그레이드** - 자세한 정보는 [VCSA 업데이트 및 SSO 링크된 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)를 참조하십시오.
* **vSphere ESXi 호스트 업그레이드** – 자세한 정보는 [기준선 작성 및 인벤토리 오브젝트에 연결](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)을 참조하십시오.
* **vSAN 디스크 형식 업그레이드** - vSAN 디스크 형식 업그레이드를 참조하십시오. 디스크 형식 업그레이드는 선택사항이지만 최상의 결과를 얻으려면 최신 버전을 사용하도록 오브젝트를 업그레이드하십시오. 온디스크 형식은 사용자 환경을 vSAN의 전체 기능 세트에 노출합니다.

## vSAN 온라인 상태 워크플로우 사용
{: #vum-updating-vsan-enable-vsan-workflow}

다음 섹션의 태스크를 통해 VUM에서 vSAN 기준선을 사용할 수 있습니다. vSAN 6.6.1 이상에서는 다음을 통해 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 인스턴스를 지원되는 상태로 유지하기 위해 vSAN 클러스터가 사용 가능한 최상의 릴리스로 최신 상태가 되도록 원활한 자동 업데이트 프로세스를 제공합니다.
* **vSAN 버전 권장사항** - VMware 호환성 안내서, vSAN 릴리스 카탈로그 및 기본 하드웨어 구성 인식의 정보를 사용하여 자동으로 생성됩니다. 또한 권장 릴리스에 필요한 드라이버 및 패치 업데이트를 시스템 기준선에 포함시킵니다.
* **vSAN 빌드 권장사항** - 클러스터가 현재 하드웨어 호환성 상태 또는 더 개선된 상태를 유지하도록 보장합니다.

vCenter 6.5 패치 2 이상 버전은 일부 프록시 사용 문제를 수정하므로 계속하기 전에 VCSA가 이 버전인지 확인하십시오. 자세한 정보는 [VCSA 업데이트 및 SSO 링크된 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)를 참조하십시오.

VUM에서 해당 vSAN 업데이트를 보기 위해 vSAN 온라인 상태 워크플로우가 이어집니다. 따라서 vSAN 온라인 상태를 사이트 `vcsa.vmware.com` 및 `vmware.com`에 연결하여 필요한 vSAN 온라인 상태 워크플로우를 사용으로 설정할 수 있도록 이러한 온라인 상태 검사를 수행해야 합니다.
* 프록시를 사용하도록 VCSA 구성
* 프록시를 사용하도록 vSAN 구성
* 고객 환경 향상 프로그램(CEIP) 사용
* 테스트 업로드를 수행하고 업로드가 작동했는지 유효성 검증

첫 번째 단계는 vSAN 빌드 권장사항 엔진에 my.vmware.com 인증 정보를 추가하는 것입니다. 성공적으로 로그인되면 vSAN이 각 vSAN 클러스터에 대한 권장 업데이트의 기준선 그룹을 생성합니다. vSAN 시스템 기준선은 기준선 및 그룹 탭의 기준선 분할창에 나열됩니다.

### 프록시를 사용하도록 VCSA 구성
{: #vum-updating-vsan-config-vcsa-proxy}

1.	점프 서버 웹 브라우저에서 VCSA 관리 인터페이스 `https://<vCenter ip>:5480`에 연결하십시오.
2.	IC4VS 콘솔의 인증 정보를 사용하여 VCSA 관리 인터페이스에 루트로 로그인하십시오.
3.	vCenter Server Appliance 관리 인터페이스에서 **네트워킹**을 클릭하고 **관리**를 클릭하십시오.
4.	프록시 서버를 구성하려면 프록시 설정 분할창에서 **편집**을 클릭하십시오.
5.	**프록시 서버 사용**을 선택하고 프록시 서버 설정을 입력한 후 **확인**을 클릭하십시오.

HTTP에 대한 프록시 정보만 설정되고 HTTPS에 대한 프록시 정보는 설정되지 않는 보고서가 있습니다. HTTPS 트래픽에 대한 프록시 정보도 구성하려면 먼저 사용으로 설정되어야 합니다. SSH를 통해 VCSA에 로그인한 후 proxy.get 명령을 사용하여 구성을 보고 HTTPS 매개변수가 설정되지 않았는지 확인하십시오.

HTTPS 매개변수가 설정되지 않은 경우 다음 명령을 사용하십시오.
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### 프록시를 사용하도록 vSAN 구성
{: #vum-updating-vsan-config-vsan-proxy}

1. **홈** > **호스트 및 클러스터**로 이동하여 탐색 분할창에서 **vSAN 클러스터**를 선택한 후 **구성 탭**을 선택하고 **vSAN**으로 이동한 후 **일반**으로 이동하십시오. **인터넷 연결** 섹션으로 스크롤하여 **편집**을 클릭하십시오.
2. 프록시의 IP 주소 및 포트 번호를 입력하고 **확인**을 클릭하십시오.

### 고객 환경 향상 프로그램(CEIP) 사용
{: #vum-updating-vsan-enable-ceip}

이 단계는 선택사항입니다. vSphere Web Client를 사용하여 **홈** > **관리** > **고객 환경 향상 프로그램**으로 이동한 후 **참여**를 클릭하십시오.

### 테스트 업로드를 완료하고 업로드가 작동했는지 유효성 검증
{: #vum-updating-vsan-complete-upload}

1. vSphere Web Client를 사용하여 **홈** > **호스트 및 클러스터**로 이동하십시오. 필수 클러스터를 선택하고 **모니터 탭** 및 **vSAN** 페이지를 선택한 후 **상태**를 클릭하십시오. **온라인 상태 사용**을 클릭하십시오.
2. **다시 테스트**를 클릭하고 프로세스가 완료될 때까지 기다리십시오.
3. 상태에 _온라인 상태 연결_이라는 새 검사가 표시되고 **온라인 상태 사용**이 **온라인 상태를 사용하여 다시 테스트**로 변경됩니다.
4. **온라인 상태를 사용하여 다시 테스트**를 클릭하여 첫 번째 업로드를 시작하고 최근 태스크 분할창에서 상태를 검토하여 프로세스가 완료될 때까지 기다리십시오. 테스트 이름이 온라인 상태(마지막 검사: 방금)로 변경됩니다.
5. 완료되면 상태 창에서 vSAN 빌드 권장사항으로 스크롤하여 펼치고 **vSAN 빌드 권장사항 엔진 상태**를 클릭하십시오.
6. **my.vmware.com에 로그인**을 클릭하고 인증 정보를 입력하십시오. 프로세스가 완료되면 **테스트 결과**가 **패스됨** 상태로 변경됩니다.
7. **Update Manager 탭**을 누르면 vSAN 클러스터가 기준선에 추가됩니다.

## 전제조건
{: #vum-updating-vsan-prereq}

vSAN 업그레이드 프로세스를 시작하기 전에 다음 요구사항이 충족되었는지 확인하십시오.
* VMware 기술 자료 문서를 검토하고 현재 vSAN 버전과 원하는 대상 vSAN 버전 간의 알려진 호환성 문제를 검토하십시오.
* **vSphere 환경이 최신 상태여야 합니다.**
  - VCSA의 패치 레벨이 vSphere ESXi 호스트보다 높거나 같아야 합니다. 필요한 경우 VCSA를 업데이트하십시오.
  - 모든 호스트가 동일한 ESXi 빌드를 실행 중이어야 합니다. vSphere ESXi 호스트 버전이 일치하지 않는 경우 업데이트하십시오.
* **모든 vSAN 디스크가 정상이어야 합니다.**
  - 장애가 있거나 존재하지 않는 디스크가 없습니다. vSphere Web Client에서 **vSAN 디스크 관리** 보기를 통해 이를 판별할 수 있습니다. **홈** > **호스트 및 클러스터**를 선택한 후 **vSAN 클러스터**를 선택하고 **vSAN 탭**을 클릭한 후 **실제 디스크**를 클릭하십시오. 모든 디스크를 스크롤하여 vSAN 상태를 검토하십시오.
  - 액세스할 수 없는 vSAN 오브젝트가 없습니다. **홈** > **호스트 및 클러스터**를 클릭한 후 **vSAN 클러스터**를 선택하여 **vSAN 상태 서비스**를 통해 이를 확인할 수 있습니다. **모니터 탭**, **vSAN**을 클릭한 후 **상태**를 클릭하십시오. 테스트 결과를 검토하십시오.
  - 업그레이드 프로세스 시작 시 **홈** > **호스트 및 클러스터**를 클릭한 후 **vSAN 클러스터**를 선택하고 **vSAN 탭** > **컴포넌트 재동기화**를 클릭하여 활성화된 재동기화가 없습니다. _컴포넌트 재동기화 수가 0이어야 합니다._ 호스트를 다시 부팅한 후에 데이터를 동기화해야 하므로 업그레이드 프로세스 중에 일부 재동기화 활동이 예상됩니다.
* **vSphere ESXi 호스트 준비** - vSAN 클러스터에서 호스트를 유지보수 모드로 이동할 때 선택할 수 있는 세 가지 옵션이 있습니다.
  - **데이터 마이그레이션 없음** - 이 옵션을 선택하면 vSAN이 이 호스트에서 데이터를 제거하지 않습니다. 호스트의 전원을 끄거나 호스트를 클러스터에서 제거하면 일부 가상 머신(VM)에 액세스하지 못하게 될 수도 있습니다.
  - **가용성 보장** - 이 옵션을 선택하는 경우 vSAN이 호스트를 전체 데이터 마이그레이션보다 더 빠르게 유지보수 모드로 이동할 수 있도록 하고 사용자 환경의 VM에 대한 액세스를 허용합니다.
  - **전체 데이터 마이그레이션**
* **유지보수 종료 및 재동기화** - vSphere ESXi 호스트가 업그레이드되고 유지보수 모드가 종료되면 재동기화가 발생합니다. 웹 클라이언트를 통해 이를 확인할 수 있습니다. 다음 호스트로 이동하기 전에 이 작업이 완료되었는지 확인하십시오. 업데이트된 호스트가 이제 vSAN 데이터 저장소에 다시 컨트리뷰션할 수 있으므로 재동기화가 발생합니다. 데이터 손실이 없도록 이 재동기화가 완료될 때까지 기다리는 것이 중요합니다.
* **vSAN 클러스터 업그레이드를 시작한 후**:
  - 클러스터에 새 버전을 도입하고 워크로드를 마이그레이션하여 클러스터를 업그레이드하려고 시도하지 마십시오.
  - 새 호스트를 도입할 경우 해당 호스트가 동일한 초기 버전인지 확인하고 클러스터의 나머지 호스트와 함께 업그레이드하십시오.
  - 업그레이드 중에 디스크를 추가하거나 교체할 경우 적절한 레거시 온디스크 형식 버전으로 형식화되었는지 확인하십시오(해당되는 경우).
  - 따라서 특정 vSAN 동작 변경사항은 온디스크 형식으로 제어되므로 새 온디스크 형식 버전을 혼합 버전 클러스터에 도입하지 않는 것이 중요합니다.

## vCenter Server 어플라이언스 업그레이드
{: #vum-updating-vsan-upgrade-vcsa}

자세한 정보는 [VCSA 업데이트 및 SSO 링크된 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)를 참조하십시오.

##	vSphere ESXi 호스트 업그레이드
{: #vum-updating-vsan-upgrade-hosts}

자세한 정보는 [기준선 작성 및 인벤토리 오브젝트에 연결](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)을 참조하십시오.

##	vSAN 디스크 형식 업그레이드
{: #vum-updating-vsan-upgrade-vsan}

RVC(Ruby vSphere Console)는 vSphere에 대한 Ruby 기반 명령행 인터페이스이며 VMware vSphere ESXi 및 vCenter를 관리하는 데 사용될 수 있습니다. vSphere 인벤토리는 트리 구조로 표시되어 vCenter 오브젝트에 대한 명령을 탐색하고 실행할 수 있습니다.

vSphere Client를 클릭하는 것보다 훨씬 더 효율적으로 많은 기본 관리 태스크를 수행할 수 있습니다. RVC는 VCSA에서 완전히 구현되며 어플라이언스에 대한 SSH 연결을 통해 발행됩니다.
1. VCSA에 SSH로 연결하고 root 및 ICVS 콘솔에 제공된 비밀번호를 사용하여 로그인하십시오.
2. 프롬프트에 `rvc Administrator@vsphere.local@localhost`를 입력하고 **Enter**를 누르십시오.
3. ICVS 콘솔에 제공된 관리자의 비밀번호를 입력하십시오. 이제 가상 파일 시스템의 루트에 있습니다. Is를 입력하고 **Enter**를 누르면 다음과 같이 표시됩니다.
  `0 /
  1 localhost/``

5. `cd 1`을 입력하고 Enter를 누른 후 `ls`를 입력하고 **Enter**를 누르십시오. 다음과 같이 표시됩니다.
  `0 / datacenter1 (datacenter)`

6. `cd 0`을 입력한 후 Enter를 누르고 `ls`를 입력한 후 **Enter**를 누르십시오. 다음과 같이 표시됩니다.

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. `cd 1`을 입력하고 **Enter**를 누른 후 `ls`를 입력하고 **Enter**를 누르십시오. 다음과 같이 표시됩니다.
  `0 cluster1 (cluster)``

8. 이 클러스터에 대해 VSAN 명령을 사용하십시오. 디스크 상태를 확인하려면 `vsan.disks_stats 0`을 입력하고 **Enter**를 누르십시오.

9. 모든 디스크의 상태가 정상인지 확인하십시오. 그런 다음 `vsan.ondisk_upgrade 0`을 입력한 다음 **Enter**를 눌러 업그레이드를 시작하십시오.

10. vSAN 크기에 따라 이 태스크에는 많은 시간이 걸릴 수 있습니다. 완료된 후 `vsan.objstatusreport 0`을 입력한 다음 **Enter**를 눌러 오브젝트 버전이 새 온디스크 형식으로 업그레이드되었는지 확인하십시오.

11. 이제 VSAN 클러스터 업그레이드가 완료되었습니다. `exit`를 입력하고 **Enter**를 눌러 RVC를 종료하십시오.

## 관련 링크
{: #vum-updating-vsan-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on IBM Cloud 디지털 기술 업무](https://ibm-dte.mybluemix.net/ibm-vmware)(데모)

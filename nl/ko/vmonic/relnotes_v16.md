---

copyright:

  years:  2016, 2019

lastupdated: "2017-05-22"

---

# V1.6 릴리스 정보

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VMware Cloud Foundation 인스턴스에 대한 업데이트

다음 컴포넌트가 새로 작성되거나 업데이트됩니다.

*  SDDC Manager 2.2.1
*  IBM 관리 컴포넌트 V1.6
*  새 하드웨어 스펙: 사용자 요구사항에 따른 **소형** 또는 **표준**
*  배치에 사용 가능한 새 데이터 센터: **HKG02 - 홍콩**, **OSL01 - 오슬로**, **SEO01 - 서울**, **SNG01 - 싱가포르** 및 **SYD04 - 시드니**

전체 컴포넌트의 목록은 [VMware Cloud Foundation 개요](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)를 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트

### vCenter Server 인스턴스에 대한 하드웨어 개선사항

V1.6 릴리스부터 vCenter Server 인스턴스에 대한 여러 개선사항을 사용할 수 있습니다.

*  vCenter Server 오퍼링에 대한 V2.0 스펙의 전체 구현. 자세한 정보는 [VMware vCenter Server on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0)를 참조하십시오.
*  새 하드웨어 스펙: 사용자 요구사항에 따른 **소형**, **중형** 또는 **대형**
*  배치에 사용 가능한 새 데이터 센터: **HKG02 - 홍콩**, **OSL01 - 오슬로**, **SEO01 - 서울**, **SNG01 - 싱가포르** 및 **SYD04 - 시드니**
*  기본적으로 VMware vSphere DRS(Distributed Resource Scheduler) 및 VMware HA(High Availability)가 사용으로 설정된 상태에서 인스턴스 주문에 최소 두 개의 ESXi 서버를 사용할 수 있음
*  인스턴스 주문 시 최대 일곱 개의 NFS 파일 공유를 추가할 수 있음. 이제 관리 컴포넌트(vCenter, PSC, NSX Manager 및 Controllers, CloudDriver)가 고가용성을 위해 NFS 파일 공유에서 실행됩니다.
*  고객 관리 VMware NSX Edge Services Gateway의 자동 배치 및 구성

이 변경으로 인해 현재 릴리스에서 기존의 vCenter Server 인스턴스 그대로 사용(또는 업그레이드)할 수 없습니다. V1.6 이전 릴리스의 vCenter Server 인스턴스가 보기 전용 모드로 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 계속해서 표시됩니다. 이 인스턴스는 경고 기호 아이콘을 사용하여 **더 이상 사용되지 않음**으로 사용자 인터페이스에 표시됩니다.

다음 조치는 V1.6 이전 vCenter Server 인스턴스에서 사용할 수 있습니다.

*  인스턴스 세부사항 페이지의 정보를 봅니다. 인스턴스 특성에 표시되는 정보는 V1.6 릴리스 날짜 기준으로 데이터를 반영하고 더 이상 새로 고쳐지지 않습니다.
*  VMware vSphere Web Client를 열어 vCenter의 인스턴스를 사용합니다.
*  인스턴스를 삭제합니다.

V1.6 이전 인스턴스의 기타 모든 조치는 더 이상 사용할 수 없습니다.

### vCenter Server 인스턴스에 대한 네트워킹 개선사항

*  사용자 VM(가상 머신)이 인터넷에 액세스할 수 있도록 사용자 대신 공용 VLAN의 16개 IP 주소가 있는 공인 서브넷이 주문됩니다.
*  사용자 VM이 SoftLayer® 내부 네트워크에 액세스할 수 있도록 사용자 대신 사설 VLAN의 64개 IP 주소가 있는 사설 서브넷이 주문됩니다.
*  NSX Controller가 비유사성 규칙으로 배치되고 3 노드 배치 구성으로 별도의 ESXi 서버에 실행됨
*  고객 사용을 위한 새 VMware NSX Edge Services Gateway

   추가 NSX Edge Services Gateway(ESG)가 이제 주문 중인 새 vCenter Server 인스턴스의 일부로 배치됩니다.

   이 ESG는 사용자 대신 주문된 사설 서브넷과 공인 서브넷 간의 통신을 위해 고유한 VM에서 사용하도록 제공되고,
   여기에는 두 개의 인터페이스가 포함됩니다. 즉, 하나의 인터페이스는 VM과 연관된 가상화된 VXLAN에 연결되고
   다른 인터페이스는 공용 VLAN에 연결됩니다. 또한 다음 설정이 구성됩니다.
   *  IP 주소의 사설 서브넷 범위에서 모든 지속적인 트래픽을 허용하는 방화벽 규칙
   *  이 사설 서브넷에서 공인 서브넷의 단일 IP 주소로 모든 IP 주소를 변환하는 SNAT(Source Network Address Translation)
   규칙(기본적으로 사용 안함으로 설정됨)
   * VMware HA(High Availability)가 관리 ESG 및 고객 관리 ESG 간에 공유되는 새 포트 그룹을 사용하도록
   구성됨

   이 ESG는 모든 하드웨어 유형에 대해 배치되고 고객은 구성을 수정할 수 있습니다. 자세한 정보는 다음 주제를
   참조하십시오.
   *  [VM에서 고객 관리 NSX Edge Services Gateway를 사용하도록 네트워크 구성](/docs/services/vmwaresolutions/vcenter/vc_esg_config.html)
   *  [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 사용성 개선사항

개선사항은 사용자 인터페이스를 통해 수행됩니다.

*  콘솔의 기본 탐색이 사용자 인터페이스의 모든 영역에 대한 액세스 권한이 있는 왼쪽 탐색 분할창의 도입을 통해 크게 개선되었습니다. 새 인스턴스를 빠르게 주문하고, 배치된 인스턴스를 보고, 시스템 알림을 검토하고, 설정을 변경하며, 온라인 문서에 액세스할 수 있습니다.
*  왼쪽 탐색 분할창에서 액세스할 수 있는 새 **시작하기** 분할창이 주문 중인 인스턴스의 컴포넌트에 대한 올바른 결정을 할 수 있도록 콘솔에 직접 충분한 세부사항을 제공할 수 있습니다. 또한 **시작하기** 페이지에서 필수 사용자 계정과 같이 인스턴스 주문을 위한 모든 전제조건 충족부터 주문하기까지의 인스턴스 주문 프로세스를 통해 단계별로 안내됩니다.
*  두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스에 대한 요약이 왼쪽 탐색 분할창의 **배치된 인스턴스** 메뉴에서 액세스할 수 있는 단일 페이지로 통합됩니다. 페이지에서 적절한 탭을 선택하여 Cloud Foundation 인스턴스 또는 vCenter Server 인스턴스를 필터링할 수 있습니다.
* Zerto 재해 복구가 인스턴스에 설치된 경우 한 번의 클릭으로 서비스 세부사항 페이지에서 Zerto 콘솔로 바로 액세스할 수 있습니다. 자세한 정보는 [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html) 및 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)를 참조하십시오.

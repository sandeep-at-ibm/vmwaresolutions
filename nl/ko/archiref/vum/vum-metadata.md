---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

#	메타데이터 수집
{: #vum-metadata}

VUM은 수정할 수 있는 사전 정의된 자동 프로세스를 통해 업그레이드, 패치 또는 확장에 대한 메타데이터를 다운로드합니다. VUM은 구성 가능한 정규 간격으로 VMware 또는 서드파티 소스에 연결하여 사용 가능한 업그레이드, 패치 또는 확장에 대한 최신 메타데이터를 수집합니다. 그러나 VMware의 기본 설정을 VMware vCenter Server on {{site.data.keyword.cloud}} 인스턴스에서 사용하도록 승인할 수 있습니다. 필요에 따라 엔터프라이즈 요구사항에 맞게 해당 설정을 변경할 수 있습니다.

VUM은 vSAN에서 생성된 시스템 관리 기준선을 표시합니다. 시스템 관리 기준선이 주기적으로 해당 컨텐츠를 자동 업데이트하며, 이를 위해서는 VUM이 인터넷에 지속적으로 액세스할 수 있어야 합니다. 일반적으로 vSAN 시스템 기준선은 24시간마다 새로 고쳐집니다.

시스템 관리 기준선을 사용하여 vSAN 클러스터를 vSAN에 대해 권장되는 중요 패치, 드라이버, 업데이트 또는 최신 지원 ESXi 호스트 버전으로 업그레이드할 수 있습니다.

대부분의 엔터프라이즈에서 VUM에 대한 VMware 기본 설정이 적합한 것으로 간주됩니다. 다음 정보는 엔터프라이즈에서 다른 설정을 사용하려는 경우 이러한 설정을 변경하는 방법을 제공합니다.

##	다운로드 스케줄
{: #vum-metadata-download-schedule}

업데이트는 가상 어플라이언스 업그레이드, 호스트 패치 및 확장이며 기본적으로 VUM이 매일 업데이트를 다운로드합니다. vSphere Web Client에 액세스하고 **홈** > **Update Manager** > **관리** > **설정**으로 이동하여 **다운로드 스케줄**을 선택한 후 **편집**을 클릭하여 변경합니다.

##	알림 확인 스케줄
{: #vum-metadata-notif-check-schedule}

알림은 패치 재호출, 새 수정사항 및 경보에 대한 정보이며 기본적으로 VUM이 시간별로 알림을 다운로드합니다. vSphere Web Client에 액세스하고 **홈** > **Update Manager** > **관리** > **설정**으로 이동하여 **알림 확인 스케줄**을 선택한 후 **편집**을 클릭하여 이를 변경할 수 있습니다.

##	가상 머신 설정
{: #vum-metadata-vm-settings}

가상 머신(VM) 설정을 변경하려면 vSphere Web Client에 액세스하고 **홈** > **Update Manager** > **관리** > **설정** 및 **VM 설정**으로 이동한 후 **편집**을 클릭하십시오.

##	호스트/클러스터 설정
{: #vum-metadata-host-settings}

호스트/클러스터 설정을 변경하려면 vSphere Web Client에 액세스하고 **홈** > **Update Manager** > **관리** > **설정** 및 **호스트/클러스터 설정**으로 이동한 후 **편집**을 클릭하십시오.

## 관련 링크
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 디지털 기술 업무](https://ibm-dte.mybluemix.net/ibm-vmware)(데모)

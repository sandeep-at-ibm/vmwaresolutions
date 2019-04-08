---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.9 릴리스 정보
{: #relnotes_v29}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

이 릴리스에서는 개념 검증 또는 샌드박스 테스트 오퍼링으로 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T 오퍼링이 도입되었습니다. vCenter Server with NSX-T는 VMware 차세대 네트워킹 플랫폼인 NSX-T를 테스트할 수 있게 해주는 사설 호스트 클라우드입니다.

자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server with NSX-T 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware Cloud Foundation on IBM Cloud의 지원 종료
{: #relnotes_v29-vcf-eos}

보다 나은 고객 경험을 위해 오퍼링을 통합하기 위해 {{site.data.keyword.cloud_notm}}에서는 2019년 5월 13일부터 더 이상 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}에 대한 지원을 제공하지 않습니다.
앞으로 모든 고객은 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로 이동하여 스토리지 및 라이센싱 옵션을 보다 유연성 있게 사용할 수 있습니다. 
VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}를 사용하는 기존 고객은 지원 종료 날짜인 2019년 5월 13일까지 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로의 마이그레이션을 지원받게 됩니다.

5월 13일 이후에는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}에 대한 관리 기능이 제거됩니다. VMware vCenter Server on {{site.data.keyword.cloud_notm}}로 마이그레이션되지 않은 인스턴스는 IBM Cloud 인프라 콘솔을 통해 액세스할 수 있습니다.

고객은 2019년 3월 25일 이전에 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}의 마이그레이션을 시작하도록 {{site.data.keyword.cloud_notm}} 지원 센터에서 연락을 받게 됩니다. 기존 고객을 위한 마이그레이션 옵션에 대한 자세한 정보는 [{{site.data.keyword.vmwaresolutions_short}} wiki 페이지](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}의 내용을 참조하십시오.
 
고객은 [{{site.data.keyword.vmwaresolutions_short}} 콘솔](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted)에서 기존 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 인스턴스를 볼 수 있습니다.

## VMware vSphere 6.7 Update 1 지원
{: #relnotes_v29-vsphere}

이제 VMware vCenter Server, VMware vCenter Server with Hybridity Bundle 및 VMware vSphere on {{site.data.keyword.cloud_notm}} 인스턴스와 함께 VMware vSphere 버전 6.7 Update 1을 주문할 수 있습니다.

또한 마이그레이션 및 앱 현대화 인스턴스에 대한 단일 노드 평가판을 vSphere Enterprise Plus 6.7u1과 함께 주문합니다.

vSphere Enterprise Plus 6.7u1은 Broadwell 및 Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}용으로만 사용 가능합니다.

자세한 정보는 다음의 _라이센스 설정_ 섹션을 참조하십시오.

* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## VLAN Spanning에 대한 지원 종료
{: #relnotes_v29-vlan}

2019년 8월부터는 {{site.data.keyword.vmwaresolutions_short}}에서 더 이상 VLAN Spanning을 지원하지 않습니다. 2019년 7월 말까지는 {{site.data.keyword.cloud_notm}} 인프라 계정을 VRF(Virtual Routing) 및 VRF(Forwarding)로 변환하고 사용자 계정에 대해 서비스 엔드포인트를 사용으로 설정해야 합니다.

자세한 정보는 다음을 참조하십시오.

* [IBM Cloud의 VRF(Virtual Routing and Forwarding) 개요](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [IBM Cloud CLI를 사용하여 서비스 엔드포인트를 사용할 계정 사용](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## API(Application Programming Interface)에 대한 지원
{: #relnotes_v29-api}

이제 API(Application Programming Interface)를 사용하여 인스턴스를 배치하고, 인스턴스를 삭제하고, ESXi 서버 및 클러스터를 추가 및 제거할 수 있습니다.

REST API 문서는 사용자 문서의 *참조* 섹션에서도 사용할 수 있습니다. 자세한 정보는 [{{site.data.keyword.vmwaresolutions_short}} API](https://cloud.ibm.com/apidocs/vmware-solutions)의 내용을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v29-vcs}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.7 Update 1(빌드 6.7.0-11675023)
* vSphere ESXi 6.5 Update 2(빌드 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1(빌드 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4(빌드 11197766)
* vSphere 2.4용 NSX-T

VMware 컴포넌트 선택에 대한 자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)를 참조하십시오.

### 데이터 센터에 대한 업데이트
{: #relnotes_v29-dc}

**FRA-05 - 프랑크푸르트** 및 **LON-05 - 런던**과 같은 새 데이터 센터를 배치에 사용할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)을 참조하십시오.

### ESXi 서버 개선사항
{: #relnotes_v29-vcs-esxi}

* SSH(Secure Shell) 프로토콜은 인스턴스 전달 전에 ESXi 서버에 대해 사용 안함으로 설정됩니다.
* V2.9 릴리스부터는 다음 ESXi 서버 조작을 사용할 수 있습니다.

   * 서버가 유지보수 모드에 있는 동안 새 ESXi 서버를 기존 클러스터에 추가합니다. 가상 머신은 유지보수 모드에서 이를 제거할 때까지는 새 서버로 마이그레이션되지 않습니다.
   * 동시에 인스턴스의 여러 클러스터에서 ESXi 서버를 추가 또는 제거합니다.

자세한 정보는 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)를 참조하십시오.

### 네트워크 파일 시스템 스토리지 크기
{: #relnotes_v29-vcs-nfs}

vCenter Server 인스턴스 주문의 경우, 0.25, 2및 4 IOPS/GB의 성능 레벨을 위해 이제 최대 24TB의 NFS(Network File System) 공유 스토리지를 추가할 수 있습니다.

10 IOPS/GB 성능 레벨은 파일 공유당 4TB의 최대 용량으로 계속 제한됩니다.
{:note}

## 추가 서비스에 대한 업데이트
{: #relnotes_v29-services}

### IBM Cloud의 Caveonix RiskForesight
{: #relnotes_v29-services-caveonix}

이제 {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스는 V2.9 이상 릴리스에 배치되거나 업그레이드된 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 이 서비스는 위협으로부터 보호하고 업계 또는 정부 규제를 충족하도록 하기 위해 사전 모니터링 및 자동화된 방어 제어를 통해 사이버 및 규제 준수 위험을 관리하는 데 도움이 될 수 있습니다.

{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스가 포함된 vCenter Server 인스턴스를 주문하거나 인스턴스 세부사항 페이지의 **서비스** 탭에서 나중에 이 서비스를 기존 vCenter Server 인스턴스에 추가할 수 있습니다.

온프레미스 워크로드의 라이센싱 및 활성화를 위해 독립형 Caveonix RiskForesight 라이센스를 VMware 인스턴스와 연관시키지 않고 주문할 수도 있습니다.

자세한 정보는 다음을 참조하십시오.
* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight에 대한 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Caveonix 라이센스에 대한 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Caveonix 라이센스 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 F5-BigIP VE V14.1.0.2가 설치되어 있습니다. F5-BigIP VE V14.1.0.2의 새로운 기능에 대한 자세한 정보는 [릴리스 노트: BIG-IP 14.1.0 새로운 기능 및 설치](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}를 참조하십시오.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 HyTrust CloudControl 5.4.2가 설치되어 있습니다. HyTrust CloudControl 5.4.2의 새 기능에 대한 자세한 정보는 [HyTrust CloudControl 릴리스 정보 버전 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}의 내용을 참조하십시오.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

이제 VMware on {{site.data.keyword.cloud_notm}} 서비스에 대해 KMIP용으로 Sydney에서 두 개의 새 엔드포인트를 사용할 수 있습니다. 자세한 정보는 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 구성](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config)을 참조하십시오.

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 Veeam 백업 및 복제 9.5 Update 4가 설치됩니다. Veeam 9.5u4의 새로운 기능에 대한 자세한 정보는 [Veeam 백업 및 복제 9.5 Update 4에 대한 릴리스 정보](https://www.veeam.com/kb2878){:new_window}를 참조하십시오.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 Zerto Virtual Replication 6.5 Update 3이 설치됩니다. Zerto Virtual Replication 6.5 Update 3의 새로운 기능에 대한 자세한 정보는 [Zerto Virtual Replication V6.5 Update 3에 대한 릴리스 정보](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}를 참조하십시오.

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v29-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* **인프라** 페이지에서는 새 **네트워크 인터페이스** 테이블이 클러스터에 대한 VLAN, 서브넷 및 IP 주소 세부사항을 제공합니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# IBM Cloud for VMware Solutions에 대한 일반 FAQ

{{site.data.keyword.vmwaresolutions_full}}에 대한 자주 묻는 질문의 답을 찾으십시오.

## IBM Cloud for VMware Solutions에 필요한 사용자 계정은 무엇입니까?

* **IBM ID 계정**. 이 계정은 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 액세스하는 데 필요합니다. 콘솔은 {{site.data.keyword.slportal}}에서 분리된 독립형 사용자 인터페이스입니다. 자세한 정보는 [시작하기](../index.html)를 참조하십시오.
* **{{site.data.keyword.cloud_notm}} 계정**. 이 계정은 프로비저닝에 필요합니다. 기존 **IBM ID**를 사용하거나 새 **IBM ID**를 작성하여 {{site.data.keyword.cloud_notm}} 계정을 등록할 수 있습니다.
* **{{site.data.keyword.cloud_notm}} 인프라 계정**. 이전에는 **IBM SoftLayer** 계정이라고 부르던 이 계정은 인프라 제품 및 서비스를 관리하기 위한 일부 추가 기능을 제공하는 {{site.data.keyword.cloud_notm}} 인프라 고객 포털에 로그인하는 데 사용됩니다. **{{site.data.keyword.cloud_notm}} 계정**을 종량과금제 유형의 계정으로 업그레이드하거나 기존 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정을 {{site.data.keyword.cloud_notm}} 계정과 링크하여 {{site.data.keyword.cloud_notm}} 인프라 계정을 가져올 수 있습니다. 사용 중인 {{site.data.keyword.cloud_notm}} 인프라 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [필수 계정 등록](signing_softlayer_account.html) 및 [{{site.data.keyword.cloud_notm}} 인프라 계정 요구사항](slaccountrequirement.html)을 참조하십시오.

## 내 IBM Cloud 인프라 인증 정보를 IBM Cloud for VMware Solutions 콘솔과 연관시킬 수 있는 방법은 무엇입니까?

처음 인스턴스를 주문할 때는 콘솔의 **설정** 페이지의 지시사항에 따라 {{site.data.keyword.slportal}}에서 {{site.data.keyword.cloud_notm}} 인프라 사용자 이름 및 API 키를 찾아서 복사하십시오. 첫 번째 주문 후 {{site.data.keyword.cloud_notm}} 인프라 인증 정보가 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 저장됩니다. 이후 주문 시 저장된 인증 정보를 자동으로 사용합니다.

## VMware 가상 플랫폼 사용 비용은 어떻게 청구됩니까?

실제 및 가상 인프라의 모든 비용과 인스턴스에서 발생한 라이센스는 {{site.data.keyword.cloud_notm}} 계정에 비용이 청구됩니다. 인스턴스를 주문할 때 {{site.data.keyword.cloud_notm}} 계정이 있어야 하고 계정과 연관된 {{site.data.keyword.slapi_short}} 키를 제공해야 합니다.

## vCenter Server 인스턴스, Cloud Foundation 인스턴스 및 VMware vSphere 클러스터 간 차이는 무엇입니까?

모든 인스턴스 유형은 VMware 가상 환경에 맞는 배치 선택사항을 제공합니다. 하지만 사용자 정의 가능성과 자동화의 범위에 차이가 있습니다.

* VMware vCenter Server 인스턴스를 주문하는 경우 사용자 정의된 컴퓨팅, 스토리지 및 네트워크 리소스와 함께 VMware 가상 환경을 배치하십시오. 배치된 컴포넌트에 대한 자세한 정보는 [vCenter Server 인스턴스의 기술 스펙](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)을 참조하십시오.
* VMware Cloud Foundation 인스턴스를 주문하는 경우 통합된 소프트웨어 정의 데이터 센터(SDDC) 플랫폼을 배치하십시오. 배치된 컴포넌트에 대한 자세한 정보는 [Cloud Foundation 인스턴스의 기술 스펙](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)을 참조하십시오.
* VMware vSphere 클러스터를 주문하는 경우 VMware 호환 하드웨어를 통합하면서 호스팅된 VMware 환경을 디자인하고 빌드할 수 있는 최대한의 유연성을 확보합니다. 하지만 {{site.data.keyword.cloud_notm}}는 VMware vSphere 클러스터에 대한 선택적 VMware 컴포넌트의 설치, 구성 및 가져오기를 자동화하지 않습니다.
* vCenter Server 인스턴스, Cloud Foundation 인스턴스 및 vSphere 클러스터에 지원되는 기능은 서로 다릅니다. 자세한 정보는 [오퍼링 비교 차트](inst_comp_chart.html)를 참조하십시오.

## vCenter Server 인스턴스에 포함되는 항목은 무엇입니까?

자세한 정보는 [vCenter Server 인스턴스의 기술 스펙](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)을 참조하십시오.

## Cloud Foundation 인스턴스에 포함되는 항목은 무엇입니까?

자세한 정보는 [Cloud Foundation 인스턴스의 기술 스펙](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)을 참조하십시오.

## vSphere 클러스터에 포함된 것은 무엇입니까?
자세한 정보는 [VMware vSphere on {{site.data.keyword.cloud_notm}}의 컴포넌트](../vsphere/vs_vsphereclusteroverview.html)를 참조하십시오.

## 두 개의 노드 vCenter Server 인스턴스는 고가용성입니까?

최소 세 개의 노드가 있는 환경에 프로덕션 워크로드를 배치하는 것이 좋습니다.

기본적으로 VMware vSphere DRS(Distributed Resource Scheduler) 및 VMware HA(High Availability)가 사용으로 설정되어 있습니다. 하지만 VMware의 우수 사례에서는 개별 노드에 세 개의 NSX Controller를 각각 배치할 것을 제안합니다.

두 개의 노드 최소 배치에서 하나의 노드에는 하나의 NSX Controller가 있고 다른 노드에는 두 개의 NSX Controller가 있습니다. 두 개의 NSX Controller가 포함된 노드의 작동이 중지되면 NSX Controller 오퍼레이션이 읽기 전용 모드로 배치되고 새 가상 머신(VM) 또는 vMotion VM에서 네트워킹 문제가 발생할 수 있습니다.

세 번째 노드가 두 개의 노드 클러스터에 추가되면 vCenter Server가 세 개의 노드에서 세 개의 NSX Controller를 자동으로 다시 밸런싱하고 고가용성 환경을 작성합니다.

## VMware vCenter 6.5 HA 구성을 설정할 수 있습니까?

아니오, 권장하지 않습니다. {{site.data.keyword.vmwaresolutions_short}}에서 실패가 발생할 수 있습니다.

## 클러스터의 이름을 바꿀 수 있습니까?

vCenter Server 인스턴스의 경우, 배치 중에 작성된 첫 번째 클러스터의 이름은 기본 이름인 **cluster1**입니다. VMware vSphere Client에서 기본 클러스터의 이름을 변경할 수 있습니다. 클러스터를 vCenter Server 인스턴스에 추가하는 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 원하는 이름을 지정할 수 있습니다.

**참고:** Cloud Foundation 인스턴스의 경우, 기본 클러스터 이름을 변경할 수 없습니다.

##패치가 어떻게 관리되고 있습니까?

IBM은 요청 시 IBM CloudDriver VSI(Virtual Server Instance)를 배치하여 IBM 코드에 대한 지속적 업데이트를 제공합니다. IBM은 Zerto on {{site.data.keyword.cloud_notm}} 또는 Veeam on {{site.data.keyword.cloud_notm}}와 같은 추가 서비스에 대한 지속적인 업데이트를 제공하지 않습니다. 업데이트의 확보 및 설치는 사용자의 책임입니다.

VMware 업데이트는 배치한 VMware 인스턴스의 유형에 따라 다른 방식으로 적용됩니다.

* VMware Cloud Foundation 인스턴스의 경우, vSphere ESXi, NSX, vCenter, Platform Services Controller 및 SDDC Manager 컴포넌트에 대한 업데이트가 {{site.data.keyword.vmwaresolutions_short}} 콘솔을 통해 제공됩니다.
* VMware vCenter Server 인스턴스의 경우:
  * V2.1 이상에 배치되거나 V2.1 이상으로 업그레이드된 인스턴스의 경우, 새로 배치된 ESXi 서버 및 클러스터가 VMware에서 최근(최신일 필요는 없음) ESXi 업데이트로 배치됩니다.
  * 사용자는 새로 배치된 ESXi 서버 및 클러스터에 필요한 모든 최신 업데이트가 있는지 확인하는 작업을 포함하여 VMware 컴포넌트에 대한 기타 모든 업데이트를 수행해야 합니다.
  * V2.0 이상에 배치된 인스턴스의 경우, VUM(VMware Update Manager)은 vCenter 서버에 통합됩니다. VUM을 구성하여 VMware에서 ESXi 업데이트를 다운로드할 수 있습니다.

자세한 정보는 다음 리소스를 참조하십시오.
* [VMware Support](https://www.vmware.com/support.html)
* [vCenter Server 인스턴스에 업데이트 적용](../vcenter/vc_applyingupdates.html)
* [업데이트를 Cloud Foundation 인스턴스에 적용](../sddc/sd_applyingupdates.html)

## 관리 서비스 NSX Edge는 보안 문제점을 발생시킵니까?

관리 서비스용 VMware NSX Edge가 공인 서브넷에 있지만 보안 위험이 발생하지 않도록 보안 조치가 제공됩니다. 해당 조치는 다음과 같습니다.
*  NSX Edge 방화벽은 관리 가상 머신에서 시작된 발신 HTTPS(TCP 포트 443) 트래픽만 허용하도록 구성됩니다.
*  사설 IP 주소가 사설 네트워크 외부에 표시되지 않도록 SNAT(Source Network Address Translation)가 사용됩니다.
*  관리 서비스 NSX Edge 어플라이언스에 대한 원격 액세스가 사용 안함으로 설정됩니다.
*  사설 네트워크에서 관리 서비스 NSX Edge에 액세스하기 위한 비밀번호는 무작위로 설정되고 암호화됩니다.

## 고객 관리 NSX Edge는 보안 문제점을 발생시킵니까?

고객 관리 NSX Edge가 공용 VLAN에 연결되지만 보안 위험이 발생하지 않도록 보안 조치가 제공됩니다. 다음 보안 조치가 준비되어 있습니다.
*  IP 주소의 사설 서브넷 범위에서 지속적인 트래픽만 허용하도록 방화벽 규칙이 제공됩니다.
*  SNAT(Source Network Address Translation) 규칙(기본적으로 사용 안함으로 설정됨)이 사설 서브넷에서 공인 서브넷의 단일 IP 주소로 모든 IP 주소를 변환하도록 제공됩니다.
*  고객 관리 NSX Edge 어플라이언스에 대한 원격 액세스가 사용 안함으로 설정됩니다.
*  사설 네트워크에서 고객 관리 NSX Edge에 액세스하기 위한 비밀번호는 무작위로 설정되고 암호화됩니다.

## 내 인스턴스의 데이터 센터는 어떻게 선택합니까?

인스턴스 배치에는 엄격한 실제 인프라 요구사항이 있으며 이는 {{site.data.keyword.CloudDataCents_notm}} 간에 다릅니다. 인스턴스를 주문할 때 사용 가능한 데이터 센터가 지역 내에 나열되며 목록에서 원하는 데이터 센터를 선택할 수 있습니다.

자세한 정보는 _IBM Cloud Data Center 가용성_ 절을 참조하십시오.
* [vCenter Server 인스턴스 요구사항 및 계획](../vcenter/vc_planning.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 요구사항 및 계획](../vcenter/vc_hybrid_planning.html)
* [Cloud Foundation 인스턴스에 대한 요구사항 및 계획](../sddc/sd_planning.html)
* [VMware vSphere on {{site.data.keyword.cloud_notm}}에 대한 요구사항 및 계획](../vsphere/vs_planning.html)
* [NetApp ONTAP Select 인스턴스에 대한 요구사항 및 계획](../netapp/np_planning.html)
* [VMware Federal 인스턴스에 대한 요구사항 및 계획](../vcenter/vc_fed_planning.html)

## 내 인스턴스를 배치하는 데 시간이 얼마나 걸립니까?

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스 세부사항 페이지의 배치 히스토리를 보고 인스턴스 배치의 상태를 확인할 수 있습니다.

## VMware vSphere on IBM Cloud가 VMware 스택을 설치하고 구성하고 가져오는 데 자동화를 사용합니까?

아니오. VMware vSphere on {{site.data.keyword.cloud_notm}}는 Cloud Foundation 및 vCenter Server 플랫폼에 있는 고급 자동화를 사용하지 않습니다. 사용자의 주문 항목에 따라 플랫폼은 선택적 VMware 라이센스, ESXi 서버를 제공하고, 선택적으로 FortiGate 실제 방화벽의 HA 쌍을 제공합니다. 새 클러스터가 작성되는 경우 세 개의 새 VLAN(하나의 공용 VLAN 및 두 개의 사설 VLAN)도 프로비저닝됩니다.

VMware ESXi는 각 베어메탈 서버에 자동으로 설치되지만 vCenter Server 또는 NSX와 같은 추가 VMware 컴포넌트를 설치해야 합니다. vSphere on {{site.data.keyword.cloud_notm}}는 VMware 호환 하드웨어가 선택된 VMware 컴포넌트에 따라 주문되는지 확인하지만, VMware 환경을 구성하고 가져오기 위해 제공된 자동화가 없습니다. 사용자는 IBM 호스팅 환경을 디자인하고 설계해야 합니다.

## 모든 알림의 목록을 볼 수 있는 방법은 무엇입니까?

전체 알림 히스토리를 보려면 왼쪽 탐색 분할창에서 **알림**을 클릭하십시오.

## IBM Cloud for VMware Solutions에 대한 문제점이 있으면 어떻게 해야 합니까?

{{site.data.keyword.vmwaresolutions_short}}에 대한 지원이 필요하면 지원 채널 중 하나를 통해 IBM 지원 센터에 문의하십시오. 자세한 정보는 [IBM 지원 센터에 문의](trbl_support.html)를 참조하십시오.

### 관련 링크

* [알림](notifications.html)
* [Cloud Foundation 인스턴스](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 인스턴스](../vcenter/vc_vcenterserveroverview.html)
* [콘솔에 액세스](loginmethod.html)
* [사용자 계정 및 설정](useraccount.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# VMware vSphere on IBM Cloud 개요

VMware vSphere on {{site.data.keyword.cloud}}가 간소화화되고 최적화된 VMware용 주문 플랫폼이며, 이를 통해 선택된 VMware 컴포넌트 기반의 VMware 호환 하드웨어를 사용자 정의하고 주문하여 고유한 IBM 호스팅 VMware 환경을 빌드할 수 있습니다.

{{site.data.keyword.vmwaresolutions_short}} 콘솔은 선택하는 VMware 컴포넌트에 따라 하드웨어를 자동으로 필터링합니다. 예를 들어, 새로운 모든 플래시 VMware vSAN 클러스터를 작성하는 경우 [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php)와 비교하여 유효성 검증된 하드웨어만 표시되고 최소 네 개의 ESXi 서버만 필요합니다.

VMware vSphere on {{site.data.keyword.cloud_notm}}는 선택적 VMware 컴포넌트의 설계, 구성 및 가져오기를 자동화하지 않고 VMware 호환 하드웨어를 통합하면서 호스팅된 VMware 환경을 디자인하고 빌드할 수 있는 최대한의 유연성을 허용합니다.

이 오퍼링을 사용하여 ESXi 서버의 새 클러스터를 작성하거나 {{site.data.keyword.CloudDataCent_notm}}에서 ESXi 서버의 기존 클러스터를 스케일링하십시오. 선택하는 VMware 컴포넌트에 따라 하나의 ESXi 서버만 사용하여 시작한 후 필요한 경우 나중에 클러스터를 스케일링할 수 있습니다.

## VMware vSphere on IBM Cloud의 컴포넌트

VMware vSphere on {{site.data.keyword.cloud_notm}}의 컴포넌트를 검토하십시오.

**참고**: 표준화된 하드웨어 구성의 가용성 및 가격 책정은 배치에 선택된 {{site.data.keyword.CloudDataCent_notm}}에 따라 달라질 수 있습니다.

### VMware 컴포넌트

다음 VMware 컴포넌트의 라이센스(IBM 제공 또는 BYOL):
* VMware vSphere Enterprise Plus 6.0u2 또는 6.5u1
* 선택적 VMware 컴포넌트:
   * VMware vCenter Server Standard
   * VMware NSX(Base, Advanced 또는 Enterprise)
   * VMware vSAN(Advanced 또는 Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

선택한 CPU 모델 및 RAM 크기를 사용하는 하나 이상의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}:
* 2CPU Intel Broadwell 세대(Intel Xeon E5-2600 v4 시리즈)
* 2CPU Intel Skylake 세대(Intel Xeon 4100/5100/6100 시리즈)

사용 가능한 옵션은 VMware vSAN 컴포넌트 선택 여부에 따라 달라집니다.

또한 다음 디스크 및 네트워킹 스펙:
* 10Gbps 듀얼 공용 및 사설 네트워크 업링크
* 한 개의 RAID 디스크 제어기

### 네트워킹

* 세 개의 VLAN(Virtual LANs): 한 개의 공인 VLAN 및 두 개의 사설 VLAN
* (선택사항) FortiGate Security Appliance 디바이스의 HA 쌍

### 스토리지

VMware vSAN 컴포넌트가 선택될 때 vSAN 구성을 위한 사용자 정의 스토리지:
* 스토리지 디스크 옵션: 960GB SSD SED, 1.9TB SSD SED 또는 3.8TB SSD SED
* 디스크 양 옵션: 2, 4, 6 또는 8

**참고:** 3.8TB SSD(Solid State Disk) 드라이브는 일반적으로 데이터 센터에서 사용 가능할 때 지원됩니다.

## vSphere 클러스터 확장 노드의 컴포넌트

각 vSphere 클러스터 확장 노드가 배치되고 {{site.data.keyword.slportal}} 계정에서 다음 컴포넌트에 대한 비용이 발생합니다.

### 확장 노드를 위한 하드웨어

하드웨어 구성이 포함된 하나의 IBM Cloud Bare Metal Serve가 [VMware vSphere on IBM Cloud의 컴포넌트](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)에 표시되어 있습니다.

### 확장 노드를 위한 네트워킹

[VMware vSphere on IBM Cloud의 컴포넌트](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)에 표시된 하나의 IBM Cloud Bare Metal Server(네트워킹 구성 포함)

### 확장 노드를 위한 VMware 컴포넌트

* VMware vSphere Enterprise Plus 6.0u2 또는 6.5u1이 포함된 하나의 IBM Cloud Bare Metal Server  
* [VMware vSphere on IBM Cloud의 컴포넌트](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)에 표시된 선택적 VMware 컴포넌트

**중요**: 주문되고 {{site.data.keyword.slportal}}에서 {{site.data.keyword.cloud_notm}} 계정으로만 제공되는 ESXi 서버, 선택적 VMware 컴포넌트 및 추가 하드웨어를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 클러스터를 작성한 후 콘솔로 돌아가서 저장된 구성을 사용하여 새 클러스터를 스케일링할 수 있습니다. 자세한 정보는 [기존 vSphere 클러스터 스케일링](vs_scalingexistingclusters.html)을 참조하십시오. 

## 관련 링크

* [VMware vSphere Software 명세서](vs_bom.html)
* [vSphere 클러스터 계획](vs_planning.html)
* [vSphere 클러스터 주문](vs_orderinginstances.html)
* [기존 vSphere 클러스터 스케일링](vs_scalingexistingclusters.html)

---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.0 릴리스 정보
{: #relnotes_v20}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v20-fva}

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스는 이제 V2.0 이상 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스에 사용 가능합니다. 이 서비스는 가상 인프라 내에 중요 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances의 고가용성(HA) 쌍을 환경에 배치합니다.

인스턴스를 주문할 때 포함된 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스와 함께 인스턴스를 주문하거나 인스턴스 세부사항 페이지에 있는 **서비스** 탭에서 나중에 이 서비스를 기존 인스턴스에 추가하십시오. 사용자 요구사항에 따라 이 서비스에 대한 세 가지 배치 크기 및 라이센싱 옵션 중 하나를 선택하십시오. 서비스가 설치되고 나면 FortiGate 콘솔에서 FortiGate 가상 어플라이언스의 방화벽 규칙을 관리하고 구성하십시오.

자세한 정보는 다음 주제를 참조하십시오.
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}에 대한 컴포넌트 및 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)

## F5 on IBM Cloud and FortiGate Virtual Appliance on IBM Cloud에 대한 다중 서비스 설치
{: #relnotes_v20-multiple-services}

이제 Cloud Foundation 인스턴스 또는 vCenter Server 인스턴스에 대한 F5 on {{site.data.keyword.cloud_notm}} 서비스 및 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스의 다중 인스턴스를 설치할 수 있습니다. 인스턴스 주문 중에 F5 서비스 또는 FortiGate 서비스를 선택하는 경우 서비스 인스턴스에 이름을 지정하여 나중에 설치하는 추가 서비스 인스턴스와 구별하십시오.

인스턴스 배치가 완료된 후 인스턴스 세부사항 페이지의 **서비스 추가** 탭에 서비스를 설치하여 F5 또는 FortiGate 서비스의 더 많은 인스턴스를 추가할 수 있습니다. 동시에 하나의 서비스만 추가할 수 있고, 서비스에 대해 추가할 모든 인스턴스에 대한 프로세스를 반복해야 합니다.

자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)를 참조하십시오.

## FortiGate Security Appliance on IBM Cloud에 대한 업데이트
{: #relnotes_v20-fsa}

이 릴리스에서 Fortinet on {{site.data.keyword.cloud_notm}} 서비스가 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}로 이름이 변경되었습니다. 서비스의 FSA(FortiGate Security Appliances) 쌍은 인스턴스에 배치될 때 기본적으로 보호되도록 구성됩니다.
* 새 Cloud Foundation 인스턴스 또는 vCenter Server 인스턴스의 일부로 FSA 쌍을 배치하는 경우 FSA는 인스턴스와 공용 네트워크 간의 필수 아웃바운드 통신만 허용하고 기타 모든 통신을 거부하도록 구성됩니다.
* 기존 Cloud Foundation 인스턴스 또는 vCenter Server 인스턴스의 일부로 FSA 쌍을 배치하는 경우 FSA는 인스턴스와 공용 네트워크 간의 모든 필수 아웃바운드 관리 통신을 허용하도록 명시적인 규칙으로 구성되고, 또한 FSA는 기존 애플리케이션 트래픽이 인터럽트되지 않는지 확인하기 위해 다른 모든 통신을 허용하는 규칙으로 구성됩니다.

모든 경우, 필요한 통신만 허용하고 기타 모든 통신은 거부하도록 FSA 구성을 주의하여 관리해야 합니다.

## 완전한 도메인 이름 형식 일관성
{: #relnotes_v20-fqdn}

이제 FQDN(Fully Qualified Domain Name)은 모든 인스턴스에 대해 일관성 있는 방식으로 표시됩니다. 주문할 때 FQDN 형식에 대한 업계 규칙을 따르도록 고유한 하위 도메인 접두부 및 호스트 이름 접두부를 입력할 수 있습니다. (예: `host-name-prefix<n>.subdomain-prefix.domain-name`).

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## 인스턴스를 주문하는 동안 워크로드 및 스토리지 예상
{: #relnotes_v20-estimates-order}

* VMware vSphere on {{site.data.keyword.cloud_notm}} 주문 중에 사용자에게는 주문된 인스턴스에서 실행될 수 있는 가상 머신의 수에 대한 예상 값이 제공됩니다.
* Cloud Foundation 및 vCenter Server 주문 중에 주문된 인스턴스에 사용 가능한 스토리지 용량의 예상 값이 제공됩니다.

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## VMware Cloud Foundation 인스턴스에 대한 업데이트
{: #relnotes_v20-vcf}

현재 릴리스는 새 배치에 대한 다음 컴포넌트 업데이트 및 개선사항이 적용됩니다.

* VMware vSphere Enterprise Plus 6.5u1(5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, 패치 릴리스 ESXi650-201710401-BG. 업데이트 esx-base, esx-tboot, vsan 및 vsanhealth VIBs(2151061). 패치 세부사항에 대한 자세한 정보는 [VMware vCenter Server Appliance Photon OS 보안 패치](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}를 참조하십시오.

기존 인스턴스(V1.9 이전 릴리스에서)를 이 목록의 컴포넌트 버전으로 업그레이드할 수 없습니다.
{:note}

### Cloud Foundation 인스턴스에 대한 클러스터 지원
{: #relnotes_v20-vcf-cluster}

이제 더 나은 리소스 관리 및 고가용성을 위해 클러스터를 사용하여 V2.0 이상 릴리스에 배치되는 Cloud Foundation 인스턴스의 ESXi 서버를 관리할 수 있습니다. 인스턴스를 주문할 때 구성한 ESXi 서버는 기본적으로 **SDDC-Cluster**로 그룹화됩니다.

클러스터 새부사항을 보거나 인스턴스 세부사항 페이지에 있는 **인프라** 탭의 인스턴스에 총 다섯 개의 클러스터를 추가할 수 있습니다. 인스턴스의 용량을 확장하거나 축소하는 경우 ESXi 서버를 추가할 클러스터 또는 ESXi 서버를 제거할 클러스터를 선택할 수 있습니다.

### Cloud Foundation 인스턴스에 대한 사용자 정의 vSAN 스토리지 지원
{: #relnotes_v20-custom-vsan-vcf}

이제 인스턴스 주문의 일부로 vSAN 스토리지 드라이브의 수와 크기를 선택하여 vSAN 스토리지 구성을 사용자 정의할 수 있습니다.

### Cloud Foundation 인스턴스에 대한 VMware vSAN 라이센스 에디션의 선택사항: Advanced 또는 Enterprise
{: #relnotes_v20-vsan-license}

이제 Cloud Foundation 인스턴스 주문 중에 원하는 vSAN 라이센스 에디션을 선택할 수 있습니다. 주문의 일부로 라이센스를 구매하거나 고유한 라이센스를 가져올(BYOL) 수 있습니다.

### Cloud Foundation 인스턴스에 대해 새로 표준화된 IBM Bare Metal Server 구성
{: #relnotes_v20-vcf-bare-metal}

다음 Bare Metal Server 구성 설정을 사용할 수 있습니다.
* 소형(듀얼 Intel Xeon E5-2650 v4 / 총 24개의 코어, 2.2GHz / 128GB RAM / 12개의 디스크)
* 대형(듀얼 Intel Xeon E5-2690 v4 / 총 28개의 코어, 2.6GHz / 512GB RAM / 12개의 디스크)

섀시에는 12개의 디스크를 위한 공간이 있습니다. 모든 슬롯을 채울 수 없습니다. **소형** 구성은 두 개의 1.9TB Micron 5100 최대 드라이브를 제공하고 **대형** 구성은 네 개의 3.8TB Micron 5100 PRO 드라이브를 제공합니다.
{:note}

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v20-vcs}

현재 릴리스는 새 배치를 위해 컴포넌트 업데이트가 적용됩니다.

* VMware vSphere Enterprise Plus 6.5u1(5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

vSAN 컴포넌트가 포함되거나 포함되지 않은 vCenter Server 사용자 정의된 주문은 항상 12개의 디스크 섀시 서버를 포함합니다. 이 서버는 가격 예상 PDF에서 비vSAN 주문 케이스에 대한 {{site.data.keyword.baremetal_short}}의 비용이 약간 높아질 수 있습니다.
{:note}

컴포넌트에 대한 자세한 정보는 [vCenter Server 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)를 참조하십시오.

### vCenter Server 인스턴스에 대한 다중 사이트 구성 지원
{: #relnotes_v20-vcs-multisite}

이제 단일 vCenter Server 인스턴스와 기본 인스턴스에 연결되는 보조 인스턴스를 배치할 수 있습니다. 다중 사이트 구성 모델은 기본 사이트와 최대 일곱 개의 보조 사이트로 허브 및 스포크 토폴로지를 사용합니다.

자세한 정보는 [vCenter Server 인스턴스에 대한 다중 사이트 구성](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)을 참조하십시오.

### vCenter Server 인스턴스에 대한 사용자 정의 vSAN 스토리지 지원
{: #relnotes_v20-custom-vsan-vcs}

vSAN 스토리지는 이제 기본 및 보조 인스턴스 모두에 대한 vCenter Server 인스턴스에 사용할 수 있습니다. 사용자 정의 구성을 선택하는 경우에만 사용할 수 있습니다. 이제 vCenter Server 인스턴스 주문 중에 원하는 vSAN 라이센스 에디션(Advanced 또는 Enterprise)을 선택할 수 있습니다. 주문의 일부로 라이센스를 구매하거나 고유한 라이센스를 가져올(BYOL) 수 있습니다.

자세한 정보는 [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)을 참조하십시오.

### VMware vCenter Server 인스턴스에 고유한 라이센스 가져오기(BYOL)
{: #relnotes_v20-byol}

BYOL은 이제 vCenter Server 인스턴스에 사용할 수 있습니다. vCenter Server 라이센스를 주문할 떄 하나 이상의 고유 vCenter Server, vSphere, vSAN 및 NSX VMware 라이센스를 사용하십시오.

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## VMware vSphere on IBM Cloud에 대한 업데이트
{: #relnotes_v20-vss}

### Bare Metal Server를 위한 새 디스크 유형
{: #relnotes_v20-disk-type}

VMware vSAN 컴포넌트의 경우 이제 {{site.data.keyword.baremetal_short}}에 다음 디스크 유형을 사용할 수 있습니다.
* 960GB SSD SED
* 1.9TB SSD SED
* 3.8TB SSD SED

**참고**:
* 3.8TB SSD SED 드라이브는 {{site.data.keyword.CloudDataCent_notm}}에서 일반적으로 사용 가능하게 되면 지원됩니다.
* VMware vSAN 컴포넌트가 포함되거나 포함되지 않은 주문은 항상 12개 디스크 섀시 서버를 포함합니다. 이 서버는 가격 예상 PDF에서 비vSAN 주문 케이스에 대한 {{site.data.keyword.baremetal_short}}의 비용이 약간 높아질 수 있습니다.

자세한 정보는 [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)을 참조하십시오.

## NetApp ONTAP Select on IBM Cloud에 대한 업데이트
{: #relnotes_v20-netapp}

### 새 베어메탈 서버 옵션
{: #relnotes_v20-netapp-bare-metal}

이제 다음 베어메탈 서버 구성 옵션을 사용할 수 있습니다.
* **고성능(중형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 1.9TB SSD 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 59TB
* **고성능(대형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 3.8TB SSD 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 118TB
* **고용량** – 표준 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 64GB RAM / 노드당 10개의 4TB SATA 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 60TB

3.8TB SSD 드라이브는 {{site.data.keyword.CloudDataCent_notm}}에서 일반적으로 사용 가능하게 되면 지원됩니다.
{:note}

자세한 정보는 다음 주제를 참조하십시오.
* [NetApp ONTAP Select 개요](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [NetApp ONTAP Select 인스턴스 주문](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## 새로 작성되고 업데이트된 문서
{: #relnotes_v20-new-docs}

VMware Cloud Foundation 사용자는 가상 머신이 서로 간에 및 인터넷과 통신할 수 있도록 {{site.data.keyword.cloud_notm}}에 있는 VMware의 NSX 플랫폼과 함께 단계별 지시사항을 사용할 수 있습니다. 자세한 정보는 [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}(VCF)에서 워크로드 VM에 대한 NSX 설정](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}을 참조하십시오.

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v20-ui}

* 클러스터에 추가할 수 있는 최대 ESXi 서버 수는 이제 32개의 서버로 업데이트되었습니다. 최대 클러스터의 수는 다섯 개로 유지됩니다.
* **리소스** 페이지에서 인스턴스 요약 테이블의 **ESXi 서버** 열이 인스턴스가 배치되거나 업데이트된 릴리스 버전을 찾을 수 있는 **버전** 열로 대체됩니다.
* SDDC Manager for Cloud Foundation 인스턴스의 버전은 이제 인스턴스 세부사항 페이지에서 사용할 수 있습니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

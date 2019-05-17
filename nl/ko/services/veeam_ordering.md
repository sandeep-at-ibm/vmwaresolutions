---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud 주문
{: #veeam_ordering}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 Veeam on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 Veeam on IBM Cloud 주문
{: #veeam_ordering-new}

다음 방법 중 하나를 사용하여 Veeam on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **Veeam on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **Veeam on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 Veeam on IBM Cloud 주문
{: #veeam_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 Veeam on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **Veeam on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## Veeam on IBM Cloud 서비스 구성
{: #veeam_ordering-config}

서비스를 주문할 때 다음 설정을 제공하십시오.

### 라이센스를 부여할 VM의 수
{: #veeam_ordering-config-vms}

최소 10개의 VM이 라이센스 관리에 필요합니다.

### 스토리지 크기
{: #veeam_ordering-config-storage-size}

스토리지 요구에 맞는 용량입니다. 스토리지 크기 예상 시 고려사항은 [Estimating Repository Capacity](https://bp.veeam.expert/repository_server/repository_planning/repository_planning_sizing)를 참조하십시오.

### 스토리지 성능
{: #veeam_ordering-config-storage-performance}

워크로드 요구사항에 기반한 GB당 IOPS(Input/output Operations Per Second)입니다.

## 관련 링크
{: #veeam_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam 웹 사이트](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

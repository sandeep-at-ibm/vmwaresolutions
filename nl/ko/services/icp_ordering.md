---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# IBM Cloud Private Hosted 주문
{: #icp_ordering}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 {{site.data.keyword.cloud}} Private Hosted 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 IBM Cloud Private Hosted 주문
{: #icp_ordering-new}

다음 방법 중 하나를 사용하여 포함된 {{site.data.keyword.cloud_notm}} Private Hosted 서비스와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **선택적 서비스** 섹션에서 **IBM Cloud Private Hosted**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 왼쪽 탐색 분할창에 있는 **VMware** 아이콘을 클릭한 다음 **VMware Services** 섹션에 있는 **IBM Cloud Private Hosted** 카드를 클릭하십시오. 서비스 설정을 지정하고 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 IBM Cloud Private Hosted 주문
{: #icp_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 {{site.data.keyword.cloud_notm}} Private Hosted 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 왼쪽 탐색 분할창에 있는 **VMware** 아이콘을 클릭한 다음 **VMware Services** 섹션에 있는 **IBM Cloud Private Hosted** 카드를 클릭하십시오. 서비스 설정을 지정하고 **기존 인스턴스에 추가**를 선택하십시오.

## IBM Cloud Private Hosted 서비스 구성
{: #icp_ordering-config}

서비스를 주문할 때 다음 설정을 제공하십시오.
* 사용자의 요구에 따라 **프로덕션에 사용 가능** 또는 **개발/테스트**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} Private Hosted 서비스를 배치하는 데 필요한 라이센스를 이미 확보했음을 인증하려면 필수 선택란을 선택하십시오.

## 추가 노드 배치
{: #icp_ordering-deploy-nodes}

추가 노드를 배치하려면 다음 정보를 검토하십시오.
* 초기 {{site.data.keyword.cloud_notm}} Private Hosted 설치로 배치되는 {{site.data.keyword.cloud_notm}} Private Ubuntu 템플리트(Ubuntu1604)를 사용하십시오.
* Ubuntu 템플리트를 찾으려면 VMware vSphere Web Client에서 `cam` 폴더 아래에 있는 **VM 및 템플리트** 탭으로 이동하십시오.
* Ubuntu 템플리트의 기본 비밀번호는 `icponcloud`입니다. 템플리트를 사용하기 전에 이 비밀번호를 변경하는 것이 좋습니다.
* {{site.data.keyword.vmwaresolutions_short}}는 Ubuntu 템플리트의 업데이트 및 패치 적용에 대한 지원을 제공하지 않습니다. 이 업데이트를 자체적으로 모니터하고 적용해야 합니다.

## 관련 링크
{: #icp_ordering-related}

* [IBM Cloud Private Hosted 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

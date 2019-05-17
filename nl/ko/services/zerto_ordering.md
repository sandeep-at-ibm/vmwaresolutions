---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 주문
{: #zerto_ordering}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 Zerto on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 Zerto on IBM Cloud 주문
{: #zerto_ordering-new}

다음 방법 중 하나를 사용하여 Zerto on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **Zerto on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **Zerto on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 Zerto on IBM Cloud 주문
{: #zerto_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 Zerto on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **Zerto on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

유지보수 모드의 ESXi 서버가 있는 vCenter Server 인스턴스에 {{site.data.keyword.cloud_notm}}용 Zerto를 추가할 경우 ZVM(Zerto Virtual Manager) 콘솔 및 사전에 채워진 Zerto Virtual Replication Appliance(VRA) IP 주소를 사용하여 수동으로 VRA 가상 머신(VM)을 배치해야 합니다.
{:note}

## 사설 전용 인스턴스에 대한 Zerto on IBM Cloud 주문
{: #zerto_ordering-private-only}

Zerto on {{site.data.keyword.cloud_notm}}를 사설 전용 인스턴스에 추가할 경우 다음 요구사항이 충족되는지 확인하십시오. 
* 사용자는 인터넷에 연결하도록 고유한 프록시 서버를 설정해야 합니다. 자세한 정보는 [공용 네트워크 연결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity)을 참조하십시오.
* Zerto용 콜홈 기능도 구성해야 합니다. Zerto 콜홈에 대한 자세한 정보는 [엔터프라이즈를 위한 Zerto 보고 환경(콜홈)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}을 참조하십시오.

## 관련 링크
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 웹 사이트](https://www.zerto.com){:new_window}
* [Zerto 기술 문서](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

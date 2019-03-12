---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# KMIP for VMware on IBM Cloud 주문 - 더 이상 사용되지 않음
{: #kmip_ordering}

KMIP for VMware on IBM Cloud의 현재 버전은 더 이상 사용되지 않습니다. 자세한 정보는 [IBM 지원 센터에 문의](../vmonic/trbl_support.html)하십시오.
{:deprecated}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 KMIP for VMware on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 KMIP for VMware on IBM Cloud 주문
{: #kmip_ordering-new}

다음 방법 중 하나를 사용하여 KMIP for VMware on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **KMIP for VMware on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **KMIP for VMware on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 KMIP for VMware on IBM Cloud 주문
{: #kmip_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **KMIP for VMware on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## KMIP for VMware on IBM Cloud 서비스 구성
{: #kmip_ordering-config}

이 서비스를 주문할 때 다음 설정을 제공하십시오.

### 서비스 지역
{: #kmip_ordering-service-region}

KMIP for VMware {{site.data.keyword.cloud_notm}} 서비스 인스턴스를 호스팅할 {{site.data.keyword.cloud_notm}} 지역을 선택하십시오.

{{site.data.keyword.cloud_notm}}는 서비스가 사용 가능한 각 지역에서 고가용성 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 엔드포인트를 유지보수합니다.

### 클라이언트 SSL 인증서
{: #kmip_ordering-ssl}

vCenter Server의 경우 KMS(Key Management Server) 클러스터를 구성해야 합니다. 선택한 지역의 엔드포인트는 클라이언트 SSL 인증서를 통해 KMS에 안전하게 연결됩니다. 각 지역의 엔드포인트는 다음 표를 참조하십시오. 이 엔드포인트는 {{site.data.keyword.vmwaresolutions_short}} 팀에서 유지보수하는 자체 서명된 인증서를 사용합니다. 인증서의 지문은 `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`입니다.

표 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 엔드포인트 지역

|지역         |엔드포인트               |
|:---------------|:-----------------------|
|독일        |  `161.156.68.107:5696` |
|시드니         |  `130.198.73.134:5696` |
|영국 |  `158.175.93.122:5696` |
|미국 남부       |  `169.60.185.42:5696`  |

이 설정은 초기 구성 시 선택사항입니다. 인스턴스가 배치된 후 vCenter Server에 있는 KMS의 클라이언트 인증서가 알려져 있으므로 이 필드를 공백으로 둘 수 있습니다. 그러나 인스턴스가 배치된 후 KMS에 대한 vCenter Server 연결이 완료될 수 있도록 인증서를 입력해야 합니다.

### 서비스 ID의 API 키
{: #kmip_ordering-api-key}

IBM Key Protect Service 인스턴스에 액세스하는 데 사용되는 {{site.data.keyword.cloud_notm}} 서비스 ID의 API 키를 입력하십시오.

### Key Protect 인스턴스
{: #kmip_ordering-key-protect}

**검색**을 클릭하여 사용 가능한 IBM Key Protect Service 인스턴스의 목록을 가져온 후 키 관리에 사용할 인스턴스를 선택하십시오.

### 고객 루트 키
{: #kmip_ordering-root-key}

**검색**을 클릭하여 선택된 IBM Key Protect 인스턴스에 저장된 고객 루트 키를 가져오십시오.

## 관련 링크
{: #kmip_ordering-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](kmip_considerations.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_hybrid_addingremovingservices.html)
* [{{site.data.keyword.cloudaccesstrailshort}} 이벤트](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

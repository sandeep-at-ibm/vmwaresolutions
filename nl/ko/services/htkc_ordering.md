---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# HyTrust KeyControl on IBM Cloud 주문

HyTrust KeyControl 어플라이언스의 HA 이중화가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 HyTrust KeyControl 어플라이언스를 추가하여 HyTrust KeyControl on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 HyTrust KeyControl on IBM Cloud 주문

다음 방법 중 하나를 사용하여 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **HyTrust KeyControl on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **HyTrust KeyControl on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 HyTrust KeyControl on IBM Cloud 주문

다음 방법 중 하나를 사용하여 기존 인스턴스에 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **HyTrust KeyControl on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## HyTrust KeyControl on IBM Cloud 서비스 구성

서비스를 주문할 때 다음 설정을 제공하십시오.

2 노드 고가용성 KeyControl 클러스터를 작성할지 여부를 지정하십시오.
* 이 옵션을 선택하면 두 개 KeyControl 노드가 배치되고 새 활성-활성 고가용성 클러스터가 작성됩니다. 이 옵션은 기본 옵션입니다.
* 이 옵션을 선택하지 않으면 두 개 독립형 KeyControl 노드가 배치되고 클러스터가 작성되지 않습니다. 독립형 노드를 수동으로 클러스터링하거나 배치 후에 기존 KeyControl 클러스터에 추가할 수 있습니다.

### 관련 링크

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 개요](htkc_considerations.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 관리](managinghtkc.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

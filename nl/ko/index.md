---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# IBM Cloud for VMware Solutions 시작하기
{: #gettingstarted}

{{site.data.keyword.vmwaresolutions_full}} 콘솔은 배치를 주문하고 관리하는 인터페이스입니다. 각 배치는 콘솔의 인스턴스로 관리됩니다. 콘솔은 {{site.data.keyword.slportal}}에서 분리된 독립형 사용자 인터페이스입니다.

## 시작하기 전에

{{site.data.keyword.vmwaresolutions_short}}에 대한 작업을 시작하기 전에 브라우저 요구사항 및 사용자 계정에 대한 중요 정보를 검토하십시오.

### 브라우저 및 해상도 요구사항

지원되는 브라우저는 다음과 같습니다.
*  Mozilla Firefox
*  Google Chrome
*  Apple Safari

**참고**: Microsoft Internet Explorer는 지원되지 않습니다.

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 보기 및 작업을 최적화하려면 최소 1024 픽셀 너비 x 500 픽셀 높이로 화면 해상도를 설정하십시오.

### IBM ID

**IBM ID**를 사용하면 {{site.data.keyword.cloud_notm}}를 포함하여 사용 중인 모든 IBM 제품과 서비스에 대해 하나의 로그인 사용자 이름을 사용할 수 있습니다. {{site.data.keyword.vmwaresolutions_short}}는 {{site.data.keyword.cloud_notm}} 카탈로그의 인프라 솔루션으로 제공됩니다. 따라서 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 액세스하려면 **IBM ID**가 있어야 합니다. 

**IBM ID**를 사용하여 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 로그인하려면 **IBM ID**를 {{site.data.keyword.cloud_notm}} 계정과 연관시켜야 합니다. 처음 콘솔에 로그인하는 경우, 사용자는 기존 **IBM ID**를 {{site.data.keyword.cloud_notm}} 계정과 연관시키거나 **IBM ID**와 자동으로 연관된 새 {{site.data.keyword.cloud_notm}} 계정을 등록하도록 안내를 받습니다. 이 프로세스를 한 번만 수행해야 합니다.

**IBM ID**를 {{site.data.keyword.cloud_notm}} 계정과 연관시키는 데 문제점이 있는 경우 [Troubleshooting for accessing {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html)를 참조하십시오.

### IBM Cloud 계정

{{site.data.keyword.cloud_notm}} 계정은 IBM Cloud 서비스를 주문하고 사용하는 데 필요합니다. 청구 정보는 IBM Cloud 계정과 연관되어 있습니다. 따라서 {{site.data.keyword.vmwaresolutions_short}}의 배치 오퍼링을 주문하고 사용하려면 {{site.data.keyword.cloud_notm}} 계정이 있어야 합니다. 실제 및 가상 인프라의 비용과 결과 라이센스는 {{site.data.keyword.cloud_notm}} 계정에 비용이 청구됩니다. {{site.data.keyword.cloud_notm}} 계정이 충족해야 하는 요구사항에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정 요구사항](vmonic/slaccountrequirement.html)을 참조하십시오.

### IBM Cloud 인프라(SoftLayer) 계정

{{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정을 이전에는 IBM SoftLayer 계정이라고 했습니다. 

{{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정과 {{site.data.keyword.cloud_notm}} 계정을 링크하여 결합된 IaaS(Infrastructure as a Service) 및 PaaS(Platform as a Service) 리소스를 사용할 수 있습니다. 그리고 단일 로그인에서 IaaS 리소스와 PaaS 리소스에 액세스할 수 있습니다. 또한 계정을 링크하면 사용하는 모든 PaaS 및 IaaS 리소스에 대한 하나의 세금계산서가 사용자에게 제공됩니다. 

* {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 없는 경우에는 [IBM Cloud 인프라(SoftLayer) 계정 등록](../vmonic/signing_softlayer_account.html)의 프로시저에 따라 계정을 요청한 후에 [IBM ID 계정 링크](https://console.bluemix.net/docs/account/softlayerlink.html)의 프로시저에 따라 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정을 {{site.data.keyword.cloud_notm}} 계정과 링크하십시오. 
* 이미 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 있는 경우에는 [IBM ID 계정 링크](https://console.bluemix.net/docs/account/softlayerlink.html)의 프로시저에 따라 이를 {{site.data.keyword.cloud_notm}} 계정과 링크할 수 있습니다. 

## IBM Cloud for VMware Solutions 콘솔에 액세스

{{site.data.keyword.cloud_notm}} 카탈로그에서 콘솔에 액세스하려는 경우에는 [{{site.data.keyword.vmwaresolutions_short}} 콘솔 액세스](vmonic/loginmethod.html)를 참조하십시오.

### 관련 링크

* [{{site.data.keyword.vmwaresolutions_short}} 정보](vmonic/prod_overview.html)
* [Cloud Foundation 개요](sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 개요](vcenter/vc_vcenterserveroverview.html)
* [Fortinet on IBM Cloud](services/fsa_considerations.html)
* [Veeam on IBM Cloud](services/veeam_considerations.html)
* [Zerto on IBM Cloud](services/addingzertodr.html)

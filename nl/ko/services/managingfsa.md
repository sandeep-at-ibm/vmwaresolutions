---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance on IBM Cloud 관리
{: #managingfsa}

FortiGate Security Appliance on {{site.data.keyword.cloud}} 서비스가 설치된 후 FortiGate 콘솔에서 FSA의 방화벽 규칙을 관리하고 구성할 수 있습니다.

인터넷을 통해 {{site.data.keyword.cloud_notm}} 인프라의 외부 관리 데이터베이스와 통신하기 위해 관리 컴포넌트(예: Zerto Virtual Manager)에서 시작되는 아웃바운드 HTTPS(TCP 포트 443) 통신을 허용하도록 FSA 방화벽 규칙이 정의되어 있는지 확인해야 합니다. 아웃바운드 HTTPS(TCP 포트 443) 통신은 인스턴스에 있는 관리 서비스 VMware NSX Edge Services Gateway(ESG)의 공인 IP 주소에서 시작됩니다.
{:important}

## FortiGate 300 Series 콘솔에 액세스
{: #managingfsa-access-console}

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 관리하려면 다음 방법 중 하나를 사용하여 FortiGate® 300 Series 콘솔에 액세스해야 합니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 인증 정보를 사용하여 FortiOS Web Client에 로그인하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 인증 정보를 사용하여 SSH 연결을 통해 콘솔에 액세스하십시오.

자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)를 참조하십시오.

## 관련 링크
{: #managingfsa-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [fortinet.com 웹 사이트](https://www.fortinet.com/)
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2)

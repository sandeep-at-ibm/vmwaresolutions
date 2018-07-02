---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# FortiGate Security Appliance on IBM Cloud 관리

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 후 FortiGate 콘솔에서 FSA의 방화벽 규칙을 관리하고 구성할 수 있습니다.

**중요**: FSA 방화벽 규칙이 인터넷을 통해 IBM Cloud 인프라의 외부 관리 데이터베이스와 통신하기 위해 관리 컴포넌트(예: IBM CloudDriver 가상 머신 또는 Zerto Virtual Manager)로 시작되는 아웃바운드 HTTPS(TCP 포트 443) 통신을 허용하도록 정의되어 있는지 확인해야 합니다. 아웃바운드 HTTPS(TCP 포트 443) 통신은 인스턴스에 있는 관리 서비스 VMware NSX Edge Services Gateway(ESG)의 공인 IP 주소에서 시작됩니다.

## FortiGate 300 Series 콘솔에 액세스

FortiGate Security Appliance on {{site.data.keyword.cloud}} 서비스를 관리하려면 다음 방법 중 하나를 사용하여 FortiGate® 300 Series 콘솔에 액세스해야 합니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 신임 정보를 사용하여 FortiOS Web Client에 로그인하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 신임 정보를 사용하여 SSH 연결을 통해 콘솔에 액세스하십시오.

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)

## 관련 링크

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 개요](fsa_considerations.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [fortinet.com 웹 사이트](https://www.fortinet.com/)
* [Fortinet 기술 문서](http://docs.fortinet.com/fortigate/admin-guides)

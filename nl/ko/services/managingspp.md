---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: SPP management console, apply SPP updates, login SPP console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# IBM Spectrum Protect Plus on IBM Cloud 관리
{: #managingspp}

## IBM Spectrum Protect Plus 관리 콘솔에 액세스
{: #managingspp-console}

{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스를 관리하려면 다음 단계를 완료하여 IBM Spectrum Protect Plus 관리 콘솔에 액세스해야 합니다.
1. {{site.data.keyword.cloud_notm}} 인프라 VPN 또는 점프 서버를 사용하여 IBM Spectrum Protect Plus 가상 머신(VM)의 IP 주소에 대한 액세스를 허용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}에 대한 서비스 세부사항 페이지에서 IP 주소를 찾을 수 있습니다.
2. IBM Spectrum Protect Plus 관리 콘솔에 액세스하려면 IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}에 대한 서비스 세부사항 페이지에서 **IBM Spectrum Protect Plus 콘솔 보기**를 클릭한 후 동일한 서비스 세부사항 페이지에 나열된 인증 정보를 사용하여 로그인하십시오.

## IBM Spectrum Protect Plus on IBM Cloud에 업데이트 적용
{: #managingspp-updates}

사용자는 IBM Spectrum Protect Plus가 항상 최신 버전으로 업데이트되어 있도록 유지보수해야 합니다. [IBM Spectrum Protect Plus 지원](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus){:external}에서 필수 업데이트를 다운로드하십시오.

자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)를 참조하십시오.

## IBM Spectrum Protect Plus VM의 운영 체제 업데이트
{: #managingspp-update-os}

IBM Spectrum Protect Plus VM의 운영 체제를 업데이트하려면 **루트** 사용자로 로그인해야 합니다. **루트** 사용자 비밀번호는 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}에 대한 서비스 세부사항 페이지에 있는 비밀번호와 동일합니다.

## 관련 링크
{: #managingspp-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations){:new_window}
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/){:external}
* [How to configure IBM Spectrum Protect Plus to offload to {{site.data.keyword.cloud_notm}} Object Storage](https://developer.ibm.com/recipes/tutorials/how-to-configure-ibm-spectrum-protect-plus-to-offload-to-ibm-cloud-object-storage/){:external}
* [IBM Spectrum Protect Plus 문서](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server Hybridity networking, networking components, networking Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}

# vCenter Server with Hybridity Bundle 인스턴스에 대한 네트워킹 고려사항
{: #vc_hybrid_networkingonvcenterserver}

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스에 대한 자세한 네트워킹 고려사항 및 요구사항은 다음 정보를 검토하십시오. 인스턴스가 올바르게 작동하도록 요구사항을 충족하는지 확인하십시오.

## vCenter Server with Hybridity Bundle 인스턴스에 대한 네트워킹 컴포넌트
{: #vc_hybrid_networkingonvcenterserver-networking-components}
{: faq}

vCenter Server with Hybridity Bundle 인스턴스에 포함된 네트워킹 컴포넌트를 검토하려면 [vCenter Server with Hybridity Bundle 인스턴스의 기술 스펙](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs)을 참조하십시오.

## 방화벽 고려사항
{: #vc_hybrid_networkingonvcenterserver-firewall-considerations}
{: faq}

방화벽을 사용 중인 경우에는 {{site.data.keyword.IBM}} CloudDriver VSI(Virtual Server Instance) 및 SDDC Manager 가상 머신(VM)의 모든 통신에 대한 규칙을 구성해야 합니다. 이러한 규칙은 모든 프로토콜이 `10.0.0.0/8` 및 `161.26.0.0/16`의 IP 주소에서 통신할 수 있도록 허용해야 합니다. 이러한 방화벽의 예로는 NSX DFW(Distributed Firewall) 또는 Vyatta 방화벽이 있습니다.

## 가상 머신에서 NSX 사용
{: #vc_hybrid_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

vCenter Server 인스턴스 배치 중에 VMware NSX는 인스턴스에서 주문되고, 설치되고, 라이센스가 부여되고, 구성됩니다. 또한 NSX Manager, NSX Controller 및 NSX Transport Zone이 설정되고 각 ESXi 서버가 NSX 컴포넌트로 구성됩니다.

또한 NSX Edge Services Gateway는 워크로드 가상 머신(VM)에서 사용할 수 있도록 배치됩니다. 자세한 정보는 [VM에서 고객 관리 NSX ESG를 사용하도록 네트워크 구성](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

## NSX 컴포넌트의 비밀번호 변경 시 고려사항
{: #vc_hybrid_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

NSX Manager, NSX Controller 및 NSX Edge의 비밀번호를 변경하기 전에 다음 고려사항을 검토하십시오.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에 있는 인스턴스의 **요약** 페이지에서 찾을 수 있는 NSX Manager의 비밀번호를 변경하지 마십시오.
* NSX Controller의 비밀번호를 변경할 수 있습니다. NSX Controller의 비밀번호를 변경하는 방법에 대한 지시사항은 [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html){:external}를 참조하십시오.
* 고객 관리 VMware NSX Edge Services Gateway(ESG)의 비밀번호 및 SSH 설정을 변경할 수 있습니다. 관리 VMware NSX Edge Services Gateway(ESG) 및 관련 Distributed Logical Router의 비밀번호를 변경하지 마십시오.

## 관련 링크
{: #vc_hybrid_networkingonvcenterserver-related}

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}
* [ NSX Edge Services Gateway ](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}
* [VMware HCX on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# vCenter Server 인스턴스에 대한 네트워킹 고려사항

vCenter Server 인스턴스에 대한 자세한 네트워킹 고려사항 및 요구사항은 다음 정보를 검토하십시오. 인스턴스가 올바르게 작동하도록 요구사항을 충족하는지 확인하십시오.

## vCenter Server 인스턴스에 대한 네트워킹 컴포넌트

vCenter Server 인스턴스에 포함된 네트워킹 컴포넌트를 검토하려면 [vCenter Server 개요](vc_vcenterserveroverview.html)의 _vCenter Server 기술 스펙_ 섹션을 참조하십시오.

## NSX 방화벽 고려사항

NSX DFW(Distributed Firewalls)를 사용 중인 경우 다음 요구사항을 검토하십시오.
* {{site.data.keyword.IBM}} CloudDriver 가상 머신(VM)에서 모든 통신의 규칙을 구성하여 모든 프로토콜이 `10.0.0.0/8` 및 `161.26.0.0/16`의 IP 주소에서 통신할 수 있도록 해야 합니다.
* IBM CloudDriver VM에서 모든 대상까지 HTTPS 트래픽에 허용하는 DFW 규칙을 작성해야 합니다.
* DFW 규칙은 VM 간의 트래픽을 차단하는 기타 규칙보다 우선이 되어야 합니다.

## 가상 머신에서 NSX 사용

vCenter Server 인스턴스 배치 중에 VMware NSX는 인스턴스에서 주문되고, 설치되고, 라이센스가 부여되고, 구성됩니다. 또한 NSX Manager, NSX Controller 및 NSX Transport Zone이 설정되고 각 ESXi 서버가 NSX 컴포넌트로 구성됩니다.

또한 NSX Edge Services Gateway는 워크로드 VM에서 사용하도록 배치됩니다. 자세한 정보는 [VM에서 고객 관리 NSX ESG를 사용하도록 네트워크 구성](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

## NSX 컴포넌트의 비밀번호 변경 시 고려사항

NSX Manager, NSX Controller 및 NSX Edge의 비밀번호를 변경하기 전에 다음 고려사항을 검토하십시오.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에 있는 인스턴스의 **요약** 페이지에서 찾을 수 있는 NSX Manager의 비밀번호를 변경하지 마십시오.
* NSX Controller의 비밀번호를 변경할 수 있습니다. NSX Controller의 비밀번호를 변경하는 방법에 대한 지시사항은 [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)를 참조하십시오.
* 고객 관리 VMware NSX Edge Services Gateway(ESG)의 비밀번호 및 SSH 설정을 변경할 수 있습니다. 관리 VMware NSX Edge Services Gateway(ESG) 및 관련 Distributed Logical Router의 비밀번호를 변경하지 마십시오.

## 관련 링크

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}

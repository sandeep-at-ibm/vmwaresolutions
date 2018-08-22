---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Cloud Foundation 인스턴스에 대한 네트워킹 고려사항

Cloud Foundation 인스턴스에 대한 자세한 네트워킹 고려사항 및 요구사항은 다음 정보를 검토하십시오. 인스턴스가 올바르게 작동하도록 요구사항을 충족하는지 확인하십시오.

## Cloud Foundation 인스턴스에 대한 네트워킹 컴포넌트

Cloud Foundation 인스턴스에 포함된 네트워킹 컴포넌트를 검토하려면 [Cloud Foundation 인스턴스의 기술 스펙](sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)을 참조하십시오. 

## NSX 방화벽 고려사항

NSX DFW(Distributed Firewalls)를 사용 중인 경우에는 IP 주소 `10.0.0.0/8` 및 `161.26.0.0/16`에서 모든 프로토콜이 통신할 수 있도록 {{site.data.keyword.IBM}} CloudDriver VSI(Virtual Server Instance) 및 SDDC Manager 가상 머신(VM)의 모든 모든 통신에 대한 규칙을 구성해야 합니다. 

## VM에서 VMware NSX 사용

Cloud Foundation 인스턴스 배치 중에 VMware NSX는 인스턴스에서 주문되고, 설치되고, 라이센스가 부여되고, 구성됩니다. 또한 NSX Manager, NSX Controller 및 NSX Transport Zone이 설정되고 각 ESXi 서버가 NSX 컴포넌트로 구성됩니다.

그러나 워크로드 VM이 서로 통신하고 인터넷에 액세스해야 하는 경우 VM의 사용을 위해 NSX를 구성해야 합니다.

NSX 설정 방법에 대한 정보는 다음을 참조하십시오.
* 기본(단일) Cloud Foundation 인스턴스에 대해서는 [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}에서 워크로드 VM에 대한 NSX 설정](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/)을 참조하십시오. 
* 다중 사이트 Cloud Foundation 인스턴스에 대해서는 [{{site.data.keyword.cloud_notm}}에서 사설 VMware 워크로드의 보안 연결](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html)을 참조하십시오. 

## NSX 컴포넌트의 비밀번호 변경 시 고려사항

NSX Manager, NSX Controller 및 NSX Edge의 비밀번호를 변경하기 전에 다음 고려사항을 검토하십시오.
* NSX Manager 비밀번호를 변경하지 마십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔에 있는 인스턴스의 **요약** 페이지에서 이 비밀번호를 찾을 수 있습니다.
* NSX Controller의 비밀번호를 변경할 수 있습니다. NSX Controller의 비밀번호를 변경하는 방법에 대한 지시사항은 [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)를 참조하십시오.
* 관리 VMware NSX Edge Services Gateway(ESG)의 비밀번호를 변경하지 마십시오.

### 관련 링크

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}

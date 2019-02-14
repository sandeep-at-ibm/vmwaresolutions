---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware 인스턴스에 대한 배치 후 고려사항

{{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server 및 VMware Cloud Foundation 오퍼링은 관리 서비스가 아닙니다. 사용자는 모든 소프트웨어 컴포넌트의 구성, 보안, 관리 및 모니터링에 책임이 있습니다. 솔루션에 대한 완전한 관리 액세스 권한을 사용하여, 다양한 도메인에서 중요한 기술, 관리 및 운영 전문 지식이 필요한 강력한 성능과 유연성을 제공합니다. {{site.data.keyword.cloud_notm}}에서 VMware 인스턴스를 관리하려면 온프레미스 인스턴스에 대한 계획과 동일한 계획 및 전문 지식이 필요합니다. VMware NSX 및 VMware vSAN과 같은 소프트웨어 정의 기술은 인스턴스 관리의 일부 측면을 크게 단순화하지만, 적절하게 관리 및 운영하기 위해서는 새로운 기술과 도구가 필요할 수 있습니다. {{site.data.keyword.cloud_notm}} 자동화된 VMware 배치의 성능, 속도 및 신뢰성을 적절한 운영 계획 및 테스트에 결합하면 빠르고 성공적인 탐색이 가능합니다.

다음 고려사항을 검토하여 인스턴스 배치 전후의 인스턴스 관리 및 운영에 대한 책임을 이해하십시오.

다음 목록은 완전하지 않습니다. 자세한 정보는 [IBM 관리 서비스](../../services/managing_imi.html)를 참조하십시오.
{:note}

## IBM Cloud 계정 액세스

{{site.data.keyword.cloud_notm}} 계정에 대한 액세스를 관리하려면, 팀의 다른 구성원이 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스에 액세스할 수 있도록 허용하십시오. 자세한 정보는 [서비스 및 리소스에 액세스하기 위한 사용자 초대](../../vmonic/iamuserinvite.html)를 참조하십시오.

## 제약사항

인스턴스에 대한 다음 제한사항을 잘 알고 있어야 합니다.

- [vCenter 아티팩트 변경의 영향](../../vcenter/vcenter_chg_impact.html)
- [네트워킹 고려사항 및 제한사항](../../vcenter/vc_networkingonvcenterserver.html)
- [자주 묻는 질문(FAQ)](../../vmonic/faq.html)

## 네트워크 디자인 및 연결

다음 단계를 완료하여 {{site.data.keyword.cloud_notm}} 네트워크 및 VMware 관리 컴포넌트에 대한 액세스를 관리하고 {{site.data.keyword.cloud_notm}} 네트워크 토폴로지를 계획하십시오.

- [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/vpn-access) 또는 [{{site.data.keyword.cloud_notm}} Direct-Link 연결](https://www.ibm.com/cloud/direct-link)을 사용하여 인스턴스 관리 엔드포인트에 액세스하십시오.
- 인스턴스 내에서 공용 네트워크 연결에 대한 전략을 설계하십시오. 옵션에는 샘플 고객 VMware NSX Edge Services Gateway(ESG), 게이트웨이 어플라이언스(예: Vyatta 및 FortiGate) 및 {{site.data.keyword.cloud_notm}} 네트워크 또는 DirectLink를 통해 액세스한 자체 네트워크에 배치된 프록시 서버가 포함됩니다.
- [{{site.data.keyword.cloud_notm}} 휴대용 IP 주소](https://console.cloud.ibm.com/docs/infrastructure/subnets/getting-started.html)를 사용하여 {{site.data.keyword.cloud_notm}} VLAN에 또는 [고유 IP 주소를 사용하여 NSX 논리 스위치(VXLANs)](../nsx/nsx_overview.html)에 워크로드를 배치할지 계획하십시오. NSX SDN(Software-Defined Networking)을 사용하면 강력한 유연성을 제공하여 {{site.data.keyword.cloud_notm}}에서 워크로드 네트워크를 관리하고 보안을 설정할 수 있습니다.
- NSX ESG, [IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance) 및 DirectLink 피어링을 사용하여 워크로드(네트워크 주소 변환, 가상 사설망(VPN), 라우팅)에 대한 연결을 계획하십시오.
- 교차 vCenter NSX를 구현하는 경우 로컬 워크로드를 배치하기 전에 로컬 세그먼트 ID 범위가 겹치지 않는지 확인하십시오.

## 보안 계획 및 기록

기업, 산업 및 규제 표준을 충족하도록 VMware 인스턴스 및 워크로드의 보안, 암호화 및 모니터링에 대한 책임이 있습니다. 다음 단계를 완료하여 적절한 보안을 설정하십시오.

- {{site.data.keyword.vmwaresolutions_short}} 콘솔에 표시되는 모든 비밀번호를 변경하고 자체 비밀번호 관리 시스템을 사용하십시오. IBM은 진행 중인 자동화 및 지원에 필요한 개별 사용자 ID를 보유하고 있습니다.
- 모든 컴포넌트에서 복잡도 및 만료 기간과 같은 비밀번호 정책을 검토하십시오.
- 모든 컴포넌트에서 암호화 설정을 검토하십시오.
- 적절한 실제 또는 가상 방화벽 솔루션(예: NSX DFW(Distributed Firewall), NSX ESG, [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) 및 [IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance))을 계획 및 구현하십시오.
- 적절한 애플리케이션 로드 밸런싱 및 보안 솔루션(예: [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html))을 계획 및 구현하십시오.
- 적절한 보안 정보 및 이벤트 관리(SIEM) 솔루션(예: [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence))을 계획 및 구현하십시오.
- 적절한 취약성 스캔을 계획하고 구현하십시오.
- [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html)와 같은 솔루션을 사용하여 인스턴스에 대한 적절한 변경 관리, 승인, 감사 및 액세스 제어를 계획 및 구현하십시오.

## 사용자 정의

다음 단계를 완료하여 기본 VMware 인스턴스 설치를 요구사항에 맞게 사용자 정의하십시오.

- 자체 인증 기관(CA)을 사용하여 vCenter, VMware Platform Services Controller(PSC) 및 NSX Manager와 같은 컴포넌트의 인증서를 생성하십시오.
- 배치된 서비스를 구성하십시오. 예를 들어, 다음과 같습니다.
  - HyTrust CloudControl on {{site.data.keyword.cloud_notm}}의 경우, AD 통합, 액세스 제어, SMTP(Simple Mail Transfer Protocol) 설정 및 규제 준수 정책을 구성하십시오.
  - Zerto on {{site.data.keyword.cloud_notm}}의 경우, NAT(Network Address Translator) 순회가 지원되지 않으므로 Zerto VRA(Virtual Replication Appliance) 통신의 IP 주소 지정 및 라우팅을 계획하십시오. 적절한 주소 지정과 라우팅을 위해 VRA의 터널링 또는 재배치를 고려하십시오.
  - Veeam on {{site.data.keyword.cloud_notm}} 및 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}와 같은 백업 서비스의 경우, 백업 작업을 구성하고, 선택적으로 추가 스토리지를 구성하고, 모니터링 경보를 구성하십시오.
  - F5 on {{site.data.keyword.cloud_notm}} 및 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}와 같은 네트워킹 및 보안 서비스의 경우, 네트워크 토폴로지 및 기타 요구사항에 따라 네트워크 인터페이스, 인증서, 고가용성(HA) 구성 및 규칙을 구성하십시오.

## Active Directory

적절한 싱글 사인온(SSO) 구성 및 관리를 위해 다음 단계를 완료하십시오.

- Active Directory(AD) 서버 업데이트 및 다시 부팅 스케줄을 구성하십시오.
- vSphere 클러스터에 AD 서버를 배치하는 옵션을 선택한 경우 규제 준수 및 가용성을 보장하기 위해 Microsoft Windows 라이센싱 및 서버 활성화를 제공하십시오.
- 인스턴스와 온프레미스 AD 서버 간에 상호 신뢰를 구축하십시오.
- 해당하는 경우 NSX VPN을 AD SSO와 통합하십시오.
- ESXi 호스트를 AD SSO와 통합하십시오.

## 유지보수 계획

소프트웨어 유지보수에 대한 적절한 계획을 위해 다음 단계를 완료하십시오.

- 프록시를 통해 [VUM(VMware Update Manager)을 설정](../vum/vum-intro.html)하여 VMware 업데이트를 가져오십시오.
- 해당되는 경우, 프록시를 통해 vSAN을 설정하여 vSAN HCL(Hardware Compatibility List) 데이터베이스를 유지보수하십시오.
- VUM에서 지원하지 않는 VMware 컴포넌트에 대해 정기적인 유지보수를 계획하십시오. (예: VMware vCenter, PSC 및 NSX).
- vSphere EVC(Enhanced vMotion Compatibility) 구성을 검토하십시오. 현재 버전의 vSphere에서 사용자 하드웨어 레벨에 대한 EVC를 지원하지 않는 경우 클러스터가 EVC 사용으로 구성되지 않을 수 있습니다.
- Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}} 및 F5 on {{site.data.keyword.cloud_notm}}와 같은 추가 기능 서비스에 대해 정기적인 유지보수를 계획하십시오.

## 모니터링

인스턴스 및 인스턴스 컴포넌트에 대한 모니터링을 위해 다음 솔루션을 계획하고 구현해야 합니다.

- 모든 인스턴스 구성요소에 대한 로그 전달 또는 콜렉션 및 적절한 로그 보유를 포함하는 로깅 서버
- 필요에 따라 SMTP 서버 및 SMS(Short Message Service) 게이트웨이의 구성을 포함하는 경보 인프라
- 호스트, 드라이브, 관리 소프트웨어 및 네트워크의 사전 모니터링
- vSAN 모니터링(해당되는 경우)
- 용량 모니터링 및 계획. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스에 [클러스터를 추가 및 제거](../../vcenter/vc_addingviewingclusters.html)하고 [호스트를 추가 및 제거](../../vcenter/vc_addingremovingservers.html)할 수 있습니다.
- 백업 인프라 및 백업 작업 모니터링

## 비즈니스 연속성 및 가용성

VMware 인스턴스가 {{site.data.keyword.cloud_notm}}의 Bare Metal Server에서 실행 중입니다. 고가용성 및 비즈니스 연속성을 위한 적절한 계획을 작성하려면 다음 단계를 완료하십시오.

- 요구사항에 대해 vSphere HA 및 vSphere DRS(Distributed Resource Scheduler) 구성을 검토하십시오.
- 요구사항에 대해 네트워크 및 스토리지 입출력 제어 구성을 검토하십시오.
- 요구사항에 대해 가상 머신 시작 순서를 구성하십시오.
- 필요에 따라 관리 및 워크로드에 대한 리소스 풀을 구성하십시오.
- [인스턴스 관리 컴포넌트](solution_backingup.html) 및 워크로드 둘 다를 위한 백업 솔루션을 계획하고, 구현하고, 모니터링하십시오.
- 여러 인스턴스, 여러 클러스터, vCenter HA 및 PSC HA의 가능성을 포함하여 인스턴스 관리의 고가용성을 계획하십시오.
- [Zerto Disaster Recovery](../../services/addingzertodr.html), [Veeam backup and replication](../../services/veeam_considerations.html) 및 [IBM Spectrum Protect Plus](../../services/spp_considerations.html)와 같은 솔루션을 사용하여 워크로드의 비즈니스 연속성을 계획하십시오.

## 스토리지 계획

용량 계획 외에도 다음을 완료하여 스토리지 구성이 성능 및 가용성 요구사항을 충족하는지 확인하십시오.

- 스토리지 성능은 RAID 구성 및 디스크 스트라이핑, 네트워크 구성, 블록 크기, 네트워크 연결 스토리지의 구성된 IOPS(Input/output Operations Per Second), VM 하드웨어 구성 및 스토리지 연결 방법, 클러스터링 및 복제 방법, 스토리지 정책 사용(예: 암호화, 중복 제거 및 압축)을 포함하는 다양한 요인에 따라 달라집니다. 스토리지 성능 요구를 충족시키도록 구성을 테스트 및 조정하는 시간을 계획하십시오.
- vSAN 스토리지 정책 검토
  - RAID-1은 RAID-5과 비교할 때 짧아진 재빌드 시간과 같은 연속 장애 발생 간격이 짧아지고 성능이 향상되었습니다. 그러나 RAID-5에 스토리지 오버헤드가 적습니다.
  - RAID-6은 듀얼 장애를 보호하지만 최소 6개의 호스트가 필요합니다(RAID-5의 경우 4개 호스트 필요).
- vSAN 클러스터에 스토리지를 더 추가하려면 클러스터에 새 호스트를 추가하거나 {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지를 대신 추가해야 합니다. 기존 호스트에 디스크 추가는 현재 지원되지 않습니다.
- 추가적인 {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지를 클러스터에 마운트하는 경우, 아키텍처 안내를 따르고 `SDDC-DPortGroup-NFS` 포트 그룹 주소를 사용하여 스토리지에 대한 호스트 라우트를 구성해야 합니다. 호스트 자체가 아니라 스토리지에 이러한 주소에 권한을 부여해야 합니다. 자세한 정보는 [연결된 스토리지 인프라 관리](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing)를 참조하십시오.

또한, 예제로 IBM Spectrum Protect Plus를 사용하여 [VMware 클러스터에 Endurance 스토리지를 추가](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)하는 방법을 보여주는 developerWorks 지침도 참조하십시오.

### 관련 링크

* [솔루션 개요](solution_overview.html)
* [디자인 개요](design_overview.html)
* [용량 스케일링](solution_scaling.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 컴포넌트 백업

사용자는 관리 인프라 및 워크로드의 백업과 가용성을 포함하여 모든 소프트웨어 컴포넌트의 구성, 관리 및 모니터링에 대한 책임이 있습니다.

솔루션의 일부로서 선택적으로 {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 또는 Veeam on {{site.data.keyword.cloud_notm}} 추가 기능 서비스를 배치할 수 있습니다. Veeam 및 IBM Spectrum Protect Plus는 관리 컴포넌트를 백업하기 위한 요구사항의 충족에 도움이 될 수 있습니다.

이러한 추가 기능 서비스는 {{site.data.keyword.cloud_notm}} Endurance 스토리지와 함께 배치됩니다. 서비스는 관리 컴포넌트 및 워크로드를 백업하는 데 도움이 됩니다. [IBM Spectrum Protect Plus 아키텍처 개요](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} 및 [Veeam 아키텍처 개요](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window}는 배치의 계획 및 크기 조정에 관한 유용한 지침을 제공합니다. 또한 Veeam 배치를 위한 [관리 서비스](https://console.bluemix.net/infrastructure/vmware-solutions/console/gettingstarted/veeam/vcs/managed)를 요청할 수 있습니다.

서로 다른 솔루션 컴포넌트에서는 백업을 위한 서로 다른 전략이 필요합니다. 일부 컴포넌트는 이미지 레벨 백업을 사용하여 보호되며, 기타 컴포넌트는 구성 및 데이터에 대한 파일 기반 백업을 사용하여 보호됩니다.

## 파일 기반 백업을 위한 파일 서버

VMware vCenter Server, PSC(Platform Services Controller) 및 VMware NSX 등의 일부 컴포넌트는 해당 구성이 파일 서버로 백업되도록 요구합니다.

이러한 백업을 호스팅하려면 다음 단계를 사용하여 Linux 파일 서버를 클러스터에 배치해야 합니다.

1. {{site.data.keyword.cloud_notm}} 인프라에서 사설 포터블 서브넷을 주문하고 시스템 컴포넌트와 동일한 VLAN에서 이를 찾으십시오. 이는 호스트에 대한 관리 IP 주소가 상주하는 사설 VLAN입니다.
2. {{site.data.keyword.cloud_notm}} 사설 미러에서 [Ubuntu Server 18.04 LTS](http://mirrors.service.softlayer.com/ubuntu-releases/ubuntu-server/bionic/daily-live/current/){:new_window} 등의 VMware 관리 데이터 저장소로 운영 체제 이미지를 업로드하십시오.
3. 이전에 주문한 개인 휴대용 IP 주소를 사용하여 관리 포트 그룹의 클러스터에 이 가상 머신(VM)을 배치하십시오. VM이 AD/DNS 서버를 지시하도록 구성되어 있는지 확인하고, 선택적으로 VM을 하위 도메인의 DNS에 추가하십시오.
4. 이 서버에서 루트가 아닌 백업 사용자 ID를 작성하고, 모든 필수 서비스가 파일 전송에 대해 구성되고 시작되었는지 확인하십시오. 예: FTP 또는 SSH.
5. 이 VM이 Veeam 또는 IBM Spectrum Protect Plus 관리 백업 작업에 포함되어 있는지 확인하십시오.

## vCenter 파일 기반 백업

VMware vCenter Server 및 PSC는 다양한 프로토콜을 사용하여 [데이터베이스 및 구성을 파일 서버로 내보내기 위한 어플라이언스 관리 사용자 인터페이스 및 API](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window}를 제공합니다. VMware에는 vCenter Server Appliance 및 PSC에서 직접 [cron 작업으로서 주기적으로 실행](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window}하도록 이를 구성하는 방법의 예가 문서화되어 있으며, 이는 용도에 맞게 수정이 가능합니다.

이 기술을 사용하여 vCenter Server Appliance 및 PSC를 둘 다 별도로 백업해야 합니다. VMware에서 문서화한 고려사항과 제한사항을 숙지하고 이에 대한 계획을 세우십시오. 또한 파일 서버에서 파일 백업의 정기적인 순환과 만료에 대해서도 계획하십시오. 참고로, VMware에서 백업 위치가 비어 있는 폴더임을 요구하므로 사용자는 각 후속 백업 작업을 위해 위치를 비워 두도록 백업 순환이나 자동화에 대한 계획을 수립해야 합니다.

## NSX 파일 기반 백업

모든 NSX 컴포넌트의 적절한 백업은 장애 발생 시에 해당 작업 상태로 시스템을 복원하는 데 매우 중요합니다. 이 디자인에서는 NSX 관리자 백업 기능을 통해 NSX 백업을 구성하도록 요구합니다. 이러한 목적을 위해 사용자는 파일 서버로 [백업을 정기적으로 수행하도록 NSX 관리자를 구성](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}할 수 있습니다. 파일 서버나 해당 데이터가 올바르게 백업되었는지 확인하고 이전 NSX 백업의 회전을 확인하십시오.

## 관리 가상 머신의 이미지 기반 백업

인스턴스를 배치하고 IBM Spectrum Protect Plus 서비스 또는 Veeam 백업 서비스를 배치한 후 관리 가상 머신에 대한 백업을 구성하십시오. 최소한 7일의 일별 백업으로 다음 VM의 백업을 계획하십시오.

* 존재하는 경우, VMware SDDC Manager
* 존재하는 경우, Active Directory 서버
* 파일 백업 서버

이러한 가상 머신을 백업할 수 있도록 충분한 Veeam 또는 IBM Spectrum Protect Plus 라이센스의 할당을 계획하고, VM에 대해 최소한 2TB의 백업 스토리지를 계획하십시오.

## 추가 기능 서비스

인스턴스에 추가 기능 솔루션 컴포넌트를 배치하는 경우에는 관리 백업 전략의 일부로서 이러한 컴포넌트의 백업에 대해서도 계획해야 합니다.

* Zerto Virtual Replication: ZVM(Zerto Virtual Manager) 시스템은 {{site.data.keyword.cloud_notm}} VSI(Virtual Server Instance)로서 배치되며 해당 백업은 Veeam 또는 IBM Spectrum Protect Plus에 의해 지원되지 않습니다. 재해 복구 전략에서 사이트 장애 복구를 수행하지 않는 ZVM 복구를 요구하는 경우에는 선호하는 Windows 백업 솔루션을 사용하여 ZVM을 백업하고 복원해야 합니다.
* F5 BIG-IP: F5에서는 사용자가 파일 서버로 경로 지정할 수 있는 [F5 구성의 파일 기반 백업](https://support.f5.com/csp/article/K13132){:new_window}을 권장합니다.
* FortiGate Security Appliance 또는 VM: Fortinet에서는 사용자가 파일 서버로 경로 지정할 수 있는 [FortiGate 구성의 파일 기반 백업](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}을 권장합니다.
* HyTrust Cloud Control 및 Data Control: HyTrust에서는 HyTrust 서버 어플라이언스의 이미지 및 파일 기반 백업을 둘 다 지원합니다. 자세한 정보는 HyTrust 관리 안내서를 참조하십시오.
* VMware HCX: HCX 어플라이언스 관리 인터페이스를 사용하면 vCenter Server Appliance와 유사한 HCX 관리자 구성의 파일 기반 백업을 작성하고 다운로드할 수 있습니다.

## 추가 고려사항

AD/DNS 서버를 {{site.data.keyword.cloud_notm}} VSI(Virtual Server Instance)로서 배치하도록 선택한 경우에는 Veeam 또는 IBM Spectrum Protect Plus를 사용하여 이를 백업할 수 없습니다. 이 경우에는 백업과 복원 오퍼레이션을 위한 선호하는 Windows 백업 솔루션을 사용하거나 VMware 클러스터 내의 AD/DNS VM을 사용하여 인스턴스를 배치하도록 계획해야 하며, 이는 Veeam 또는 IBM Spectrum Protect Plus로 백업이 가능합니다.

VMware vCenter 6.5u2 이상에서, VMware는 데이터베이스 무결성을 보장하기 위해 백업 시간 중에 데이터베이스에 대한 통합된 일시중단 및 재개 스크립트로 이미지 기반 백업을 사용하여 vCenter Postgres 데이터베이스의 백업을 지원합니다. VMware 인스턴스를 vCenter 6.5u2로 업그레이드하는 경우에는 파일 기반 백업을 사용하는 대신에 Veeam 또는 IBM Spectrum Protect Plus를 사용하여 vCenter Server 및 PSC를 백업하도록 선택할 수 있습니다. 이를 수행하는 경우에는 Veeam 또는 IBM Spectrum Protect Plus 일시정지 기능을 사용하여 데이터베이스 무결성을 보장해야 합니다.

## 백업에서 복원

관리 백업을 복원하는 경우 다음과 같은 몇 가지 특수 고려사항이 있습니다.

* vCenter 및 PSC의 경우, VMware는 새 가상 어플라이언스를 배치하고 백업으로부터 구성을 복원할 수 있는 설치 프로그램을 제공합니다.
* 백업에서 어플라이언스를 복원할 때 설치 프로그램은 사용자가 제공하는 백업 정보를 기반으로 어플라이언스의 유형(vCenter Server 또는 PSC)을 감지합니다.
* 호스트 중 하나에 직접 배치하므로, 사용자는 분배 스위치 또는 포트 그룹에 배치하지 못할 수 있습니다. 복구된 어플라이언스를 배치하기 위해 임시 표준 스위치 및 포트 그룹을 작성하고 VM에 대한 네트워크 연결을 제공하기 위해 vmnic 중 하나를 임시로 이 스위치로 마이그레이션해야 할 수 있습니다. 배치 후에는 VM을 분배 포트 그룹에 마이그레이션하고 vmnic를 dvSwitch로 리턴할 수 있습니다.
* NSX의 경우에는 백업에서 구성을 복원하기 전에 NSX Manager 및 제어기를 다시 배치해야 할 수 있습니다.
* vCenter 백업 및 복원에 대한 VMware 고려사항과 제한사항을 잘 숙지하고 있는지 확인하십시오.

## 요약

적절한 계획을 통해 VMware 인스턴스가 성공적으로 해당 관리 컴포넌트를 유실하고 이를 복구함을 보장할 수 있습니다. 반드시 백업 작업의 성공과 백업 데이터의 가용성을 정기적으로 모니터하고, 관리 인프라와 워크로드 모두에 대해 정기적으로 백업 및 복원 계획을 테스트하십시오.

### 관련 링크

* [솔루션 개요](solution_overview.html)
* [디자인 개요](design_overview.html)
* [용량 스케일링](solution_scaling.html)

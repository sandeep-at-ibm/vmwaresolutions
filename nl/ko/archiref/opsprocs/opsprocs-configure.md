---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-07"

---

# 구성 태스크
{: #opsprocs-configure}

vCenter Server 인스턴스가 프로비저닝된 후 시스템 관리자가 엔터프라이즈의 요구로 초기 환경을 사용자 조정하도록 실행하고 향후 서비스 요구사항에 응답해야 할 수 있는 많은 구성 태스크가 있습니다. 

구성 태스크는 다음과 같습니다.

* 인스턴스 및 클러스터 지침
* 가상 머신(VM) 프로시저
* vCenter 프로시저
* vSphere ESXi 호스트 프로시저
* 스토리지 프로시저
* 네트워크 프로시저

## 인스턴스 및 클러스터 지침
{: #opsprocs-configure-instance}

표 1. vCenter Server 인스턴스 및 클러스터

| 제목 |설명 |
|---|---|
| 이름 지정 규칙  | 첫 번째 태스크 중 하나는 vCenter Server 인스턴스에 대한 이름 지정 규칙을 채택하는 것입니다. 조직에 사용되는 기존 이름 지정 규칙을 확장하거나 이름 지정 규칙을 작성할 수 있습니다. 자세한 정보는 [VMware Validated Design 4.1의 이름 지정 규칙](https://docs.vmware.com/en/VMware-Validated-Design/4.1/com.vmware.vvd.sddc-upgrade.doc/GUID-FCA126F1-E429-454E-B3BA-226525742DC1.html){:new_window}을 참조하십시오. vCenter Server 인스턴스에서 이름 지정 규칙을 채택하거나 이름을 변경하기 전에 [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact){:new_window}을 참조하십시오.|
| vCenter Server 인스턴스에 연결  | 프로비저닝한 후 vCenter에 연결하십시오. 초기에 수행할 두 가지 메소드가 있습니다. 인터넷을 사용하여 점프박스에 연결한 후 사 설 네트워크를 사용하여 점프박스에서 vCenter로 연결할 수 있도록 "점프박스" 서버를 배치할 수 있습니다. 두 번째 메소드는 사용자 위치에서 {{site.data.keyword.cloud_notm}} Private 네트워크(대역외 관리 및 vCenter 액세스를 허용)로의 VPN 연결인 {{site.data.keyword.cloud_notm}} VPN을 사용하는 것입니다. 자세한 정보는 [가상 사설망(VPN) 시작하기](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started)를 참조하십시오. |
| 이름 분석 구성 | vCenter에서 기능을 사용하려면 vCenter Server 컴포넌트에 대한 이름 분석을 워크스테이션 또는 점스박스(연결 메소드에 따라 달라짐)에 추가하십시오. /etc/hosts 또는 c:\Windows\System32\Drivers\etc\hosts 파일에는 PSC(Platform Services Controller), vCenter 및 vSphere ESXi 호스트에 대한 항목이 필요합니다. 자세한 정보는 [VMware vSphere Web Client를 사용하여 OVF 파일 배치](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_deploy_ovf#trbl_deploy_ovf){:new_window}를 참조하십시오. |
| RBAC | vSphere 환경에서 공통 태스크에 필요한 권한에 대한 정보는 [공통 태스크에 필요한 권한](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4D0F8E63-2961-4B71-B365-BBFA24673FDB.html){:new_window}을 참조하십시오. |
| 사용자 정의 인증 기관 서명 인증서 사용 | [vSphere 6.x Machine SSL 인증서를 사용자 정의 인증 기관 서명 인증서로 대체(2112277)](https://kb.vmware.com/s/article/2112277){:new_window}를 참조하십시오. |
| vSphere 모니터링 구성  | vSphere는 전체 vSphere 컴포넌트에서 이벤트를 추적하는 사용자 구성 가능 이벤트 및 알람 서브시스템을 포함하고 로그 파일 및 vCenter 데이터베이스에 데이터를 저장합니다. 이벤트는 vSphere 오브젝트에서 발생하는 사용자의 레코드 또는 시스템 조치입니다. 세 가지 유형의 이벤트 즉, 정보, 경고 및 오류가 있습니다. 알람은 이벤트, 조건 세트 또는 vSphere 오브젝트의 상태에 대한 응답으로 활성화되는 알림입니다. 알람의 심각도 레벨은 정상(초록색), 경고(노란색) 및 경보(빨간색)입니다. 알람 조치는 알람(예: 이메일 알림이 전송됨)에 대한 응답으로 발생하는 오퍼레이션입니다. vSphere 모니터링의 구성 및 사용 방법에 대한 정보는 [이벤트, 알람 및 자동화된 조치 모니터링](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}을 참조하십시오. |
| 클러스터 추가, 보기 및 삭제 | vCenter Server 인스턴스가 vSphere ESXi 호스트의 클러스터와 함께 배치되었습니다. 더 많은 클러스터를 인스턴스에 추가하여 컴퓨팅 및 스토리지 용량을 확장할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters){:new_window}를 참조하십시오. |
| vCenter Server 용량 |비즈니스 요구사항에 따라 vSphere ESXi 서버 또는 네트워크 파일 시스템(NFS) 스토리지를 추가하거나 제거하여 VMware vCenter Server 인스턴스의 용량을 확장하거나 축소할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers){:new_window}를 참조하십시오. |
| vCenter Server 인스턴스 서비스 | vCenter Server 인스턴스가 배치된 후 재해 복구, 심각도 또는 백업 솔루션과 같은 추가적인 서비스를 추가할 수 있습니다. 이 서비스가 더 이상 필요하지 않은 경우 인스턴스에서 이를 제거할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices){:new_window}를 참조하십시오. |
| vCenter Server 인스턴스 업데이트 | vCenter Server 인스턴스에 업데이트를 적용하는 방법에 대한 정보는 [ vCenter Server 인스턴스에 IBM 관리 컴포넌트 업데이트 적용](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_applyingupdates#vc_applyingupdates)을 참조하십시오. vCenter Server 인스턴스에 패치 및 업데이트를 적용하는 이 프로세스는 관리 컴포넌트에만 자동화됩니다. VMware 제품 업데이트를 수동으로 적용하는 시스템 관리자에 대한 정보는 [vCenter Server on IBM Cloud with Hybridity Bundle 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-hybridity-intro#vcs-hybridity-intro){:new_window}를 참조하십시오. |
| 다중 사이트 구성 |다중 사이트 구성 기능은 기본 사이트와 최대 일곱 개의 보조 사이트로 허브 및 스포크 토폴로지를 사용합니다. {{site.data.keyword.cloud_notm}} 인스턴스에 대한 다중 사이트 구성의 구성에 대한 정보는 [vCenter Server on IBM Cloud 인스턴스에 대한 다중 사이트 구성](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite#vc_multisite){:new_window}을 참조하십시오. 다중 사이트 구성에서 vCenter Server 인스턴스를 삭제하기 위한 단계에 대한 정보는 [다중 사이트 구성에서 vCenter Server 인스턴스 삭제](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance_multi#vc_deletinginstance_multi){:new_window}를 참조하십시오. |
| VMware Update Manager 사용 | 배치되면 시스템 관리자가 VMware 제품을 업데이트합니다. 시스템 관리자가 vCenter Server 인스턴스에서 VUM을 사용할 수 있는 방법에 대한 정보는 [VMware Update Manager 소개](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}를 참조하십시오. |
| 핵심 vCenter Server Instance 컴포넌트 백업 | 시스템 관리자는 관리 인프라 및 워크로드의 백업과 가용성을 포함하여 vCenter Server 인스턴스의 모든 소프트웨어 컴포넌트의 구성, 관리 및 모니터링에 책임이 있습니다. 솔루션의 일부로 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 또는 Veeam on {{site.data.keyword.cloud_notm}} 추가 기능 서비스를 선택적으로 배치할 수 있습니다. Veeam 및 IBM Spectrum Protect Plus는 관리 컴포넌트를 백업하기 위한 요구사항의 충족에 도움이 될 수 있습니다. 백업 메커니즘 및 백업할 핵심 컴포넌트에 대한 정보는 [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)을 참조하십시오. |
| VMware 제품에 대한 진단 정보 수집 | VMware 기술 지원은 지원 요청이 처리될 때 정기적으로 진단 정보를 요청합니다. 이 진단 정보에는 제품별 로그, 구성 파일 및 상황에 적합한 데이터가 포함되어 있습니다. VMware Knowledgebase 문서에 대한 URL 및 이 정보 수집을 위한 세부적인 단계별 태스크에 대한 정보는 [VMware 제품에 대한 진단 정보 구성 수집(1008524)](https://kb.vmware.com/s/article/1008524?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오. VMware NSX Edge 디바이스에 필요한 진단 정보 수집의 프로세스에 대한 정보는 [VMware NSX Edge에 대한 진단 정보 수집(2079380)](https://kb.vmware.com/s/article/2079380?lang=en_US#q=Collecting%20diagnostic%20information%20for%20VMware%20NSX%20Edge%20){:new_window}을 참조하십시오. |

## VM 프로시저
{: #opsprocs-configure-vm}

표 2. VM 프로시저

| 제목	|설명 |
|---|---|
| VM 작성 | 새 VM 작성에 대한 정보는 [새 가상 머신 마법사로 가상 머신 작성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-AE8AFBF1-75D1-4172-988C-378C35C9FAF2.html?hWord=N4IghgNiBcIMICcCmYAuSAEYMDUCWCqArpBgLJgDGAFngHaYDueq1GrmAcko7gcaQo16mAOp4AXmAQATEAF8gA)을 참조하십시오. |
| VM 구성 | VM 하드웨어 구성에 대한 정보는 [가상 머신 하드웨어 구성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4AB8C63C-61EA-4202-8158-D9903E04A0ED.html){:new_window}을 참조하십시오. |
| VM에 게스트 OS 설치 | VM에 게스트를 설치하는 프로세스에 대한 정보는 [게스트 운영 체제 설치](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-90E7F734-D699-4603-B222-AF4DE84459C7.html){:new_window}를 참조하십시오. |
| 스냅샷 작성 | 스냅샷은 스냅샷 작성 시 전체 VM 상태를 캡처합니다. VM 전원이 켜져 있거나 꺼져 있거나 일시중단된 경우 스냅샷을 작성할 수 있습니다. 자세한 정보는 [VMware Host Client에서 스냅샷 작성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.html.hostclient.doc/GUID-A0D8E8E7-629B-466D-A50C-38705ACA7613.html){:new_window}을 참조하십시오. |
| 스냅샷 되돌리기 | 스냅샷 시작 시 이전 상태로 VM 상태 복원에 대한 정보는 [스냅샷 복원](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E0080795-C2F0-4F05-907C-2F976433AC0D.html){:new_window}을 참조하십시오. |
| VM 및 템플리트 제거와 추가 | vCenter 인벤토리에서 VM 및 VM 템플리트를 제거하거나 디스크에서 VM 및 VM 템플리트를 삭제하는 데 대한 정보는 [VM 및 VM 템플리트에서 제거와 등록](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-376174FE-F936-4BE4-B8C2-48EED42F110B.html){:new_window}을 참조하십시오. |
| VM/도구 업데이트 | VM을 호환성의 상위 레벨 및 도구의 상위 버전으로 업그레이드하는 데 대한 정보는 [가상 머신 업그레이드](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE77B0A9-F8FF-4785-BEAD-B6F04EE04492.html){:new_window}를 참조하십시오. |
| 디스크 추가	| 디스크를 기존 VM으로 추가하는 데 대한 정보는 [가상 머신에 하드 디스크 추가](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-79116E5D-22B3-4E84-86DF-49A8D16E7AF2.html){:new_window}를 참조하십시오. |
| 디스크 축소 | 디스크를 기존 VM으로 축소하는 데 대한 정보는 [VMware ESX 및 ESXi에 대한 가상 디스크 확장, 줄이기 및 축소(1002019)](https://kb.vmware.com/s/article/1002019){:new_window}를 참조하십시오. |
| 디스크 확장	| VM용 기존 디스크의 크기를 확장하는 데 대한 정보는 [가상 디스크 구성 변경](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E1D541D1-DF96-467A-89B7-E84F83B2563D.html){:new_window}을 참조하십시오. |
| 핫 마이그레이션 | 동일한 클러스터에서 vSphere 호스트 간 VM의 vMotion 수행 방법에 대한 정보는 [가상 머신 관리](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-B7023DD7-F790-4DF8-89B4-FF09DA3DBFB1.html?hWord=N4IghgNiBcIBYHsAuACAtgSwOYCcxIFMUA3NEAXyA){:new_window}를 참조하십시오. |
| 콜드 마이그레이션 | vCenter Server 인스턴스 간 VM 마이그레이션에 대한 정보는 [전원이 꺼지거나 일시중단된 가상 머신 마이그레이션](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8DE930E-8079-4AC0-AEC2-B6EA1604F4E3.html){:new_window}을 참조하십시오. |
| VM 제거 | VM 제거에 대한 정보는 [vCenter Server 또는 데이터 저장소에서 VM 또는 VM 템플리트 제거](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-27E53D26-F13F-4F94-8866-9C6CFA40471C.html){:new_window}를 참조하십시오. |
| 디스크 제거 | VM에서 디스크 제거에 대한 정보는 [가상 머신에서 하드 디스크 제거](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.webaccess.doc_41/configuring_virtual_machine_options_and_resources/t_remove_an_existing_hard_disk.html){:new_window}를 참조하십시오. |
| VM Tools | VM Tools 업데이트를 위한 프로세스에 대한 정보는 [기준선 작성 및 인벤토리 오브젝트에 연결](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines)을 참조하십시오. |
| 가상 디스크 형식 결정 및 씬 프로비저닝 형식에서 Thick 프로비저닝 형식으로 가상 디스크 변환 | VM 디스크가 씬 프로비저닝 형식에서 가상 디스크로 작성된 경우 VM 디스크를 Thick 프로비저닝 형식으로 변환하는 프로세스에 대한 정보는 [가상 디스크 형식 결정 및 씬 프로비저닝 형식에서 Thick 프로비저닝 형식으로 가상 디스크 변환](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8F50BEC-F575-4AB1-BC77-D9A13CDBDCF7.html){:new_window}을 참조하십시오. |
| AD/DNS 서버 OS 업데이트  |Microsoft Active Directory(AD)/DNS(Domain Name Server)는 업데이트만 다운로드하도록 자동으로 설정됩니다. 자세한 정보는 [Windows 업데이트 자동 설치](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_limitations#trbl_limitations-windows-update)를 참조하십시오. |

## vCenter 프로시저
{: #opsprocs-configure-vcenter}

표 3. vCenter 프로시저

| 제목 |설명 |
|---|---|
| VCSA 백업 | 자세한 정보는 [vCenter Server Appliance 6.7 파일 기반 백업 및 복원의 단계별 절차](https://blogs.vmware.com/vsphere/2018/05/vcenter-server-appliance-6-7-file-based-backup-and-restore-walkthroughs.html){:new_window}를 참조하십시오. |
| VSCA/PSC 패치 | 자세한 정보는 [vCenter Server Appliance 및 Platform Services Controller Appliance 패치](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-043EF6BD-78F7-412F-837F-CBDF844F850C.html){:new_window}를 참조하십시오. |
| VCSA 서비스 중지, 시작 또는 다시 시작 | 문제점 해결 및 유지보수 목적으로 VMware vCenter Server Appliance(VCSA) 서비스의 상태를 변경해야 하는 경우도 있습니다. 자세한 정보는 [VMware vCenter Server Appliance 6.x 서비스 중지, 시작 또는 다시 시작(2109887)](https://kb.vmware.com/s/article/2109887?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오. |
| VCSA용 백업 및 복원 옵션 개요 |자세한 정보는 [vCenter Server 6.x의 백업 및 복원 옵션 개요(2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}를 참조하십시오. |
| vCenter 이메일 알림 구성 | 특정 조건이 이미 정의된 알람 및 사용자 정의가 작성된 알람에 트리거되는 경우 이메일 주소로 전송될 이메일 알림 구성에 대한 정보는 [vCenter Server 알람에 대한 이메일 경보 구성(2123925)](https://kb.vmware.com/s/article/2123925?lang=en_US){:new_window}을 참조하십시오. |

## vSphere ESXi 호스트 프로시저
{: #opsprocs-configure-host}

표 4. vSphere ESXi 호스트 프로시저

| 제목 |설명 |
|---|---|
| vSphere 호스트 유지보수 | 업그레이드 또는 실제 디바이스 대체와 같은 유지보수 태스크가 실행되어야 하는 경우 호스트가 유지보수 모드로 배치됩니다. 호스트는 시스템 관리자 요청의 결과로서만 유지보수 모드로 전환되거나 유지됩니다. 유지보수 모드로 전환되는 호스트에서 실행되는 VM은 다른 호스트로 마이그레이션되거나(DRS를 통해 수동으로 또는 자동으로) 종료되어야 합니다. 자세한 정보는 [유지보수 모드로 호스트 배치](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html?hWord=N4IghgNiBcIG4GUAOALApgJzQAgBIHsBnAF2wFkwBLAO2LWrGoGM0QBfIA){:new_window}를 참조하십시오. |
| vSphere ESXi 호스트 추가 | 자세한 정보는 [vCenter Server 인스턴스에 ESXi 서버 추가](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}를 참조하십시오.
| vSphere ESXi 호스트 제거 |	자세한 정보는 [원격 ESXi 서버에 대한 프로시저](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-procedure){:new_window}를 참조하십시오. |
| 베어메탈 서버 펌웨어 패치 |자세한 정보는 [내 베어메탈 서버에 날짜가 지난 펌웨어가 있는 경우](/docs/bare-metal?topic=bare-metal-bm-faq#what-if-my-bare-metal-server-has-out-of-date-firmware-)를 참조하십시오. |
| vSphere ESXi 호스트 패치 |vSphere ESXi 호스트 및 기타 vCenter Server 인스턴스 컴포넌트를 업데이트하기 위한 VUM(VMware Update Manager) 사용에 대한 정보는 [VMware Update Manager 소개](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)를 참조하십시오. |
| 호스트 네트워크 연결 테스트	| vSphere ESXi 호스트의 실제 네트워크 어댑터와 실제 스위치 간의 네트워크 링크가 작동되며 사용 가능한지 확인하는 방법에 대한 자세한 정보는 [네트워크 링크 확인(1003724)](https://kb.vmware.com/s/article/1003724?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오. |
| ESXi에서 네트워크/스토리지 펌웨어 및 드라이버 버전 결정 | 자세한 정보는 [ESXi 4.x 이상에서 네트워크/스토리지 펌웨어 및 드라이버 버전 결정(1027206)](https://kb.vmware.com/s/article/1027206?lang=en_US#q=network%20interface%20card%20error){:new_window}을 참조하십시오. |
| ESXi에서 네트워크 및 TCP/UDP 포트 연결 문제 해결 | 자세한 정보는 [ESX/ESXi에서 네트워크 및 TCP/UDP 포트 연결 문제 해결(2020669)](https://kb.vmware.com/s/article/2020669?lang=en_US#q=network%20interface%20card%20error){:new_window}을 참조하십시오. |

## 스토리지 프로시저
{: #opsprocs-configure-storage}

표 5. 스토리지 프로시저

| 제목 |설명 |
|---|---|
| {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지 추가 |기존 클러스터에 {{site.data.keyword.cloud_notm}} Endurance NFS 공유 추가에 대한 정보는 [vCenter Server 인스턴스에 NFS 스토리지 추가](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances)를 참조하십시오. |
| {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지 제거 |기존 클러스터에서 {{site.data.keyword.cloud_notm}} Endurance NFS 공유 제거에 대한 정보는 [vCenter Server 인스턴스에서 NFS 스토리지 제거](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-nfs-storage)를 참조하십시오.
| {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지 확장 | {{site.data.keyword.cloud_notm}} Endurance NFS 공유에 더 많은 용량 추가에 대한 정보는 [블록 스토리지 용량 확장](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity)을 참조하십시오. |
| {{site.data.keyword.cloud_notm}} Endurance NFS 스토리지 축소 | {{site.data.keyword.cloud_notm}} Endurance NFS 공유에서 용량 축소에 대한 정보는 [블록 스토리지 용량 확장](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity)을 참조하십시오. |
| vSAN 정책 우수 사례 조언 | 자세한 정보는 [vSAN 정책 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure#design_virtualinfrastructure-storage-policy){:new_window}을 참조하십시오. |
| vSAN 상태 검사 사용	| 자세한 정보는 [vSAN 온라인 상태 워크플로우 사용](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vsan#vum-updating-vsan-enable-vsan-workflow){:new_window} 및 [vSAN 상태 검사 정보(2114803)](https://kb.vmware.com/s/article/2114803){:new_window}를 참조하십시오. |
| 암호화 사용 |	암호화를 사용으로 설정하기 위해 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 사용에 대한 정보는 [KMIP for VMware on IBM Cloud 개요](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations)를 참조하십시오. VM 암호화 사용에 대한 정보는 [가상 머신 암호화](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.security.doc/GUID-E6C5CE29-CD1D-4555-859C-A0492E7CB45D.html){:new_window}를 참조하십시오. vSAN 클러스터에서 데이터를 보호하기 위해 저장 데이터 암호화 사용에 대한 정보는 [vSAN 클러스터에서 암호화 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-F3B2714F-3406-48E7-AC2D-3677355C94D3.html){:new_window}을 참조하십시오.|
| vSAN 스토리지 추가 | 기존 vSAN 클러스터에 더 많은 vSphere ESXi 호스트 추가에 대한 정보는 [vCenter Server 인스턴스에 ESXi 서버 추가](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}를 참조하십시오. 더 많은 호스트를 추가하면 클러스터에서 CPU, RAM 및 스토리지가 늘어납니다. vSAN 기술에 대한 자세한 정보는 [vSAN 클러스터 확장](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-666D9839-2726-4936-8C0F-94476ECE0606.html){:new_window}을 참조하십시오. |
| vSAN 스토리지 제거 | vSAN 클러스터에서 스토리지 제거에 대한 정보는 [vCenter Server 인스턴스에서 ESXi 서버 제거](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing){:new_window}를 참조하십시오. 호스트를 제거하면 클러스터에서 CPU, RAM 및 스토리지가 줄어듭니다. |
| 기본 vSAN 알람 사용 | 기본 vSAN 알람은 클러스터, 호스트 및 기존 vSAN 라이센스를 모니터하는 데 사용될 수 있습니다. 이 알람은 알람에 해당하는 이벤트가 활성화되거나 알람에 지정된 하나 또는 모든 조건이 충족되면 자동으로 트리거됩니다. 조건을 편집하거나 기본 알람을 삭제할 수 없습니다. 사용자 요구사항에 특정한 알람을 구성하려면 vSAN에 대한 사용자 정의 알람을 작성하십시오. vSAN 이벤트를 위한 vCenter Server 알람 작성을 참조하십시오. 클러스터, 호스트를 모니터하고, 새 이벤트를 분석하고, 전체 클러스터 상태를 평가하기 위해 알람, 이벤트 모니터링, 기존 알람 설정 편집 및 기본 vSAN 알람 사용에 대한 정보는 [vSAN 기본 알람 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-E7885CDE-654D-4732-A5FE-31D0AB2B2F57.html){:new_window}을 참조하십시오. |
| SIOC 사용 | 기본적으로 SIOC(Storage IO Control)가 사용 안함으로 설정되어 있습니다. 데이터 저장소에서 VM에 대한 나쁜 성능을 경험한 경우 스토리지 리소스에 대한 우선순위를 지정하는 데 도움이 필요하면 SIOC를 사용으로 설정할 수 있습니다. 모든 VM에서 적정한 양의 스토리지 리소스를 가져오는지 확인하기 위해 스토리지 경합이 발생할 때 SIOC만 활성화합니다. VM 스토리지 정책을 사용하고 해당 정책을 VM 또는 VMDK로 지정하면 이를 사용할 수 있습니다. 자세한 정보는 [스토리지 I/O 리소스 관리](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-7686FEC3-1FAC-4DA7-B698-B808C44E5E96.html){:new_window}를 참조하십시오. |
| 데이터 저장소 클러스터 구성 | 데이터 저장소 클러스터는 공유 리소스 및 공유 관리 인터페이스가 포함된 데이터 저장소의 콜렉션입니다. 클러스터는 호스트에 대한 것이고 데이터 저장소 클러스터는 데이터 저장소에 대한 것입니다. 데이터 저장소 클러스터를 작성할 때 vSphere Storage DRS를 사용하여 스토리지 리소스를 관리할 수 있습니다. 데이터 저장소를 데이터 저장소 클러스터에 추가하면 데이터 저장소의 리소스가 데이터 저장소 클러스터의 리소스 일부가 됩니다. 데이터 저장소 클러스터를 사용하여 스토리지 리소스를 집계하면 데이터 저장소 클러스터 레벨에서 리소스 할당 정책을 지원할 수 있습니다. 자세한 정보는 [데이터 저장소 클러스터 작성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-598DF695-107E-406B-9C95-0AF961FC227A.html){:new_window}을 참조하십시오. |

## 네트워크 프로시저
{: #opsprocs-configure-networks}

표 6. 네트워크 프로시저

| 제목 |설명 |
|---|---|
| 네트워크 고려사항 | 자세한 정보는 [vCenter Server 인스턴스에 대한 네트워킹 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver){:new_window}을 참조하십시오. |
| HCX을 위한 계획 |VMware HCX(Hybrid Cloud Services)를 사용하면 vSphere 소프트웨어 정의 데이터 센터(SDDC)의 개별 인스턴스를 통해 다양한 네트워크 유형을 통합할 수 있습니다. HCX는 온프레미스 및 클라우드 제공자 경계를 넘어 다중 인스턴스, 다중 사이트, vSphere 배치를 확장하려는 중에 발생할 수 있는 보안, 호환성 및 성능 문제를 해결하도록 설계되었습니다. 자세한 정보는 [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)를 참조하십시오. |
| 초기 NSX 구성 | vCenter Server 인스턴스에 대한 배치의 일부로 샘플 고객 네트워크는 사설 서브넷, 공용 서브넷, NSX 논리 스위치, Distributed Logical Router로 구성되어 사용 가능하며, NSX Edge 어플라이언스는 네트워크 주소 변환을 수행하도록 배치되고 구성됩니다. 사용자의 VM에 맞게 이 샘플 고객 네트워크를 구성하는 단계는 [VM에서 고객 관리 NSX ESG를 사용하도록 네트워크 구성](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_esg_config#vc_esg_config){:new_window}을 참조하십시오. |
| 논리 스위치 추가 | 논리 스위치는 사용자가 VM에 연결할 수 있는 네트워크 연결을 제공한다는 점에서 VLAN과 유사합니다. 그런 다음 VM이 동일한 논리 스위치에 연결된 경우 VXLAN을 통해 서로 통신할 수 있습니다. 논리 스위치를 추가하는 경우 빌드 중인 특정 토폴로지에 유의해야 합니다. 자세한 정보는 [논리 스위치 추가](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}를 참조하십시오. |
| DLR 추가 | DLR(Distributed Logical Router)은 연결된 논리 스위치 간(동쪽-서쪽 트래픽)을 라우트하는 가상 어플라이언스입니다. 자세한 정보는 [Distributed Logical Router 추가](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-E825C0C7-F4CC-4B26-90AF-A2167AC519DB.html){:new_window}를 참조하십시오. |
| ESG 추가 | ESG(External Services Gateway)는 실제 네트워크와 논리 네트워크 간(북쪽-남쪽 트래픽)을 라우트하는 가상 어플라이언스입니다. 자세한 정보는 [Edge Services Gateway 추가](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-B9A97F20-4996-4E16-822C-0B98DDE70571.html){:new_window}를 참조하십시오. |
| NSX Edge 방화벽 규칙 구성 | Edge 방화벽은 방화벽, NAT(Network Address Translation), 사이트 간 VPN 및 SSL VPN을 포함한 주변 보안 기능을 제공하도록 북쪽-남쪽 트래픽을 모니터합니다. 관리 및/또는 업링크 인터페이스의 방화벽 규칙만 적용할 수 있습니다. 자세한 정보는 [NSX Edge 방화벽 규칙 관련 작업](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-178B11B8-FEB1-49B8-B6FF-D069C41EEB32.html){:new_window}을 참조하십시오. |
| 분산 방화벽 | 분산 방화벽은 VM에 대한 네트워크 액세스 제어를 제공하는 하이퍼바이저 커널에 임베드된 방화벽입니다. 데이터 센터, 클러스터, VM 이름, IP, VLAN(DVS 포트-그룹), VXLAN(논리 스위치), 보안 그룹 및 Active Directory의 사용자 그룹 ID와 같은 VMware vCenter 오브젝트를 기반으로 한 액세스 제어 정책을 작성합니다. 방화벽 규칙은 VM이 vMotion되는 상태에서도 일관성 있는 액세스 제어를 제공하도록 각 VM의 vNIC 레벨에서 강제 실행됩니다. 자세한 정보는 [분산 방화벽](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-95600C1C-FE9A-4652-821B-5BCFE2FD8AFB.html){:new_window}을 참조하십시오. |
| NAT 규칙 구성  | NSX Edge는 여러 소스 또는 대상 IP 주소를 VM 또는 VM 그룹에 지정하도록 NAT(Network Address Translation) 서비스를 제공합니다. NAT 서비스 구성은 SNAT(Source NAT) 규칙과 DNAT(Destination NAT) 규칙으로 분리됩니다. 자세한 정보는 [NAT 규칙 관리](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}를 참조하십시오. |
| NSX 로드 밸런서 구성 | NSX Edge 로드 밸런스는 고가용성 서비스를 사용으로 설정하고 다중 VM 사이에서 네트워크 트래픽 로드를 분배합니다. 로드 분배가 사용자에 대해 투명하게 수행되는 방식으로 다중 VM 사이에서 수신 서비스 요청을 균등하게 분배합니다. 로드 밸런싱은 최적의 리소스 활용을 달성하고, 처리량을 최대화하고, 응답 시간을 최소화하고, 과부하를 방지하는 데 도움이 됩니다. NSX Edge는 최대 계층 7까지 로드 밸런싱을 제공합니다. 로드 밸런싱을 위해 외부 또는 공용 IP 주소를 내부 VM 세트에 맵핑합니다. 외부 로드 밸런서는 외부 IP 주소에 대한 TCP, UDP, HTTP 또는 HTTPS 요청을 허용하고 사용할 내부 서버를 결정합니다. 포트 80은 HTTP용 기본 포트이며 포트 443은 HTTPS용 기본 포트입니다. NSX에는 사용 가능한 두 가지 유형의 로드 밸런싱 서비스 즉, 외팔(one-armed) 모드 또는 인라인 모드(투명 모드)가 있습니다. 자세한 정보는 [논리 로드 밸런서](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-152982CF-108F-47A6-B86A-0F0F6A56D628.html){:new_window}를 참조하십시오. |
| NSX 비밀번호 변경 | 자세한 정보는 [방화벽 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver#vc_networkingonvcenterserver-firewall-considerations)을 참조하십시오. |
| Juniper vSRX 어플라이언스 배치 | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스는 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances 쌍을 사용자 환경에 배치합니다. 그러나 이 서비스가 사용자에게 적합하지 않은 경우, 필요에 따라 자체 서드파티 솔루션을 구현하고 vSRX 게이트웨이를 vCenter Server 인스턴스에 추가할 수 있습니다. 자세한 정보는 [VMware vSphere Web Client로 vSRX 설치](https://www.juniper.net/documentation/en_US/vsrx/topics/task/installation/security-vsrx-vsphere-client-installing.html)(/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)]{:new_window}를 참조하십시오. |
| Palo Alto VM-Series 방화벽 배치 | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스는 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances 쌍을 사용자 환경에 배치합니다. 그러나 이 서비스가 사용자에게 적합하지 않은 경우, 필요에 따라 자체 서드파티 솔루션을 구현할 수 있습니다. vCenter Server 인스턴스에 Palo Alto VM-Series 방화벽 추가에 대한 정보는 [ESXi 서버에서 VM-Series 방화벽 설정](https://docs.paloaltonetworks.com/vm-series/8-0/vm-series-deployment/set-up-a-vm-series-firewall-on-an-esxi-server.html#)(/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)]{:new_window}을 참조하십시오. |
| Cisco Firepower 어플라이언스 배치  | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스는 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances 쌍을 사용자 환경에 배치합니다. 그러나 이 서비스가 사용자에게 적합하지 않은 경우, 필요에 따라 자체 서드파티 솔루션을 구현할 수 있습니다. vCenter Server 인스턴스에 Cisco Firepower 어플라이언스 추가에 대한 정보는 [VMware vSphere Web Client 또는 vSphere Hypervisor를 사용하여 Firepower Threat Defense Virtual 배치](https://www.cisco.com/c/en/us/td/docs/security/firepower/quick_start/vmware/ftdv/ftdv-vmware-qsg.html#17970)(/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)]{:new_window}를 참조하십시오. |
|Direct Link | vCenter Server 인스턴스 배치 후 시스템 관리자는 {{site.data.keyword.cloud_notm}} 관리 VPN을 통해 인스턴스에 연결할 수 있습니다. 그런 다음 시스템 관리자는 사용자의 워크로드에 적합한 인터넷 액세스를 구성할 수 있습니다. 그러나 사용자는 인터넷이 아닌 직접 연결을 사용하려고 할 수 있습니다. {{site.data.keyword.cloud_notm}} Direct Link는 전 세계 위치에서 사용 가능한 {{site.data.keyword.cloud_notm}} Network의 네 가지 오퍼링 스위트입니다. 각각은 고객이 공용 인터넷을 사용하지 않고도 원격 네트워크 환경과 {{site.data.keyword.cloud_notm}} 배치 간에 직접적인 개인용 연결을 작성할 수 있도록 합니다. 일반적으로, 이러한 오퍼링은 하이브리드 워크로드, 교차 제공자 워크로드, 대형 또는 빈번한 데이터 전송, 사설 워크로드를 지원하거나 {{site.data.keyword.cloud_notm}} 환경의 관리를 용이하게 하기 위해 구현됩니다. 자세한 정보는 [IBM Cloud Direct Link 시작하기](/docs/infrastructure/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link#get-started-with-ibm-cloud-direct-link){:new_window}를 참조하십시오. 사설 네트워크만 사용하여 액세스할 수 있는 vCenter Server 인ㅅ턴스에 대한 정보는 [공용 또는 사설 네트워크](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-public-private-network){:new_window}를 참조하십시오. |
| 웹 프록시 배치 |	VMware Server 인스턴스가 배치되면 vCenter Server Appliance(VCSA)에는 vSAN 상태 검사의 업데이트를 사용으로 설정할 수 있도록 하는 VMware 저장소에 대한 직접적인 액세스 권한이 제공되지 않습니다. 이 저장소에 대한 액세스를 허용하기 위한 Squid 웹 프록시 배치에 대한 정보는 [초기 구성](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config-install-cfg-squid)을 참조하십시오. 이 프로시저는 다른 공급업체의 기타 프록시 애플리케이션과도 관련이 있습니다. |
| 방화벽 로깅 | NSX Edge 및 분산 방화벽은 감사 로그, 규칙 메시지 로그 및 시스템 이벤트 로그와 같은 로그 파일을 생성하고 저장합니다. 방화벽을 사용으로 설정한 각 클러스터마다 Syslog 서버를 구성해야 합니다. 자세한 정보는 [방화벽 로그](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-6F9DC53E-222D-464B-8613-AB2D517CE5E3.html){:new_window}를 참조하십시오. Operations Management in {{site.data.keyword.cloud_notm}}에는 Syslog 서버의 역할을 수행하는 vRealize Log Insights가 포함됩니다. |
| NSX 로깅 및 시스템 이벤트 |NSX 컴포넌트의 Syslog 서버 구성에 대한 정보 및 시스템 이벤트, 알람, 감사 로그 및 기술 지원 로그 수집에 대한 정보는 [NSX 로깅 및 시스템 이벤트](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.logging.doc/GUID-3F08DC2E-2D82-4C89-8829-EF1EA0160B13.html){:new_window}를 참조하십시오. |
| HCX 온프레미스 배치| 자세한 정보는 [온프레미스 VMware HCX on IBM Cloud 인스턴스에 대한 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations#standalone_considerations){:new_window}을 참조하십시오. |
| HCX 검사 | HCX on {{site.data.keyword.cloud_notm}} 서비스는 온프레미스 데이터 센터의 네트워크를 {{site.data.keyword.cloud_notm}}로 원활하게 확장하며, 이를 통해 변환이나 변경 없이 {{site.data.keyword.cloud_notm}} 간에 VM을 마이그레이션할 수 있습니다. HCX Cloud Management 콘솔 액세스 및 HCX on {{site.data.keyword.cloud_notm}}에 업데이트 적용에 대한 자세한 정보는 [VMware HCX on IBM Cloud 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx#managing-vmware-hcx-on-ibm-cloud)를 참조하십시오. |


## 관련 링크
{: #opsprocs-configure-links}

* [VMware vSphere 문서](https://docs.vmware.com/en/VMware-vSphere/index.html){:new_window}
* [NSX 설치 안내서](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}
* [NSX 관리 안내서](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-B5C70003-8194-4EC3-AB36-54C848508818.html){:new_window}
* [VMware vSAN 관리 안내서](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-AEF15062-1ED9-4E2B-BA12-A5CE0932B976.html){:new_window}
* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

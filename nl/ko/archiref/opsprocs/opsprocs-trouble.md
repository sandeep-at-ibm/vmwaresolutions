---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# 문제점 해결
{: #opsprocs-trouble}

vCenter Server 인스턴스의 문제점을 해결하려면 시스템 관리자는 문제의 증상을 식별하고, 영향을 주는 솔루션 컴포넌트를 판별하고, 수정사항 또는 임시 해결책을 조사 및 제안하고, 수정사항을 테스트해야 합니다.

* 증상 식별 - 가능한 수 많은 원인으로 인해 인스턴스의 성능이 저하되거나 성능이 유실될 수 있습니다. 효율적인 문제점 해결의 첫 번째 단계는 잘못된 점을 정확하게 식별하는 것입니다. 이 증상은 vSphere 이벤트 및 알람, Operations Management in {{site.data.keyword.cloud}}에서 보고되거나 사용자 중 하나의 서비스 데스크를 통해 보고될 수 있습니다.
* 영향을 받는 컴포넌트 격리 - 문제의 증상을 식별한 후 영향을 주고 문제의 원인이 될 수 있는 소프트웨어 또는 하드웨어 컴포넌트를 식별하고 포함되지 않는 해당 컴포넌트를 식별해야 합니다. {{site.data.keyword.cloud_notm}}의 vCenter 오퍼레이션 관리와 같은 도구는 이 단계를 지원합니다.
* 수정사항 또는 임시 해결책 제안 - 컴포넌트를 격리한 증상을 이해한 후 가능성 있는 수정사항 및 임시 해결책을 조사할 수 있습니다. 시스템 관리자는 IBM ServiceNow 및 VMware Knowledgebase를 비롯한 이 문서의 문제점 해결 시나리오를 포함하여 {{site.data.keyword.cloud_notm}} Portal도 사용합니다. 또한 많은 위키 및 블로그가 도움이 될 수 있습니다. 보다 빠른 해결을 위해 Operations Management in {{site.data.keyword.cloud_notm}}에는 식별된 문제에 대한 다수의 조치방안이 포함됩니다.
* 가능한 솔루션 테스트 - 문제의 증상, 관련된 컴포넌트 및 수정사항/임시 해결책을 제안한 컴포넌트를 알게 되면 문제가 해결될 때까지 시스템 관리자가 솔루션을 체계적으로 테스트합니다.

 \vSphere는 전체 vSphere 환경에서 발생하는 이벤트를 추적하는 사용자 구성 가능 이벤트 및 알람 서브시스템을 포함하고 로그 파일 및 vCenter 데이터베이스에 데이터를 저장합니다. 이 서브시스템을 통해 시스템 관리자가 경보가 트리거되는 조건을 지정할 수도 있습니다. 알람은 시스템 조건이 변경됨에 따라 경고에서 보다 심각한 경보로 상태를 변경하고 시스템 관리자 팀에 이메일 발송과 같은 목적으로 자동화된 알람 조치를 트리거할 수 있습니다. 이 기능은 특정 이벤트 또는 조건이 특정 인벤토리 오브젝트 또는 오브젝트 그룹에 대해 발생하는 경우에 알림을 받거나 즉각적인 조치를 취하려고 할 때 유용합니다.

Operations Management on {{site.data.keyword.cloud_notm}} 아키텍처에 통합된 도구와 같은 추가 도구는 증상 식별, 영향을 받은 컴포넌트 격리 및 수정사항 또는 임시 해결책 제안에 대한 더 큰 지원을 제공합니다.

## 가이드라인
{: #opsprocs-trouble-guidelines}

다음 지침은 {{site.data.keyword.vmwaresolutions_short}} 문제를 해결하기 위한 우수 사례로 간주됩니다.
* 체계적으로 문제점 해결에 접근하십시오.
* 가용성, 활용도 또는 구성에 관련된 증상입니다.
 *  가용성 - 이 증상은 하드웨어 및 소프트웨어 컴포넌트의 가용성에 관련되어 있으며 응답 없음이 특징입니다. 고가용성 디자인은 이 문제가 워크로드 및 사용자에 직접 영향을 주지 않도록 이 문제를 마스킹하기도 합니다.
 * 활용도 - 이 증상은 용량 및 성능에 관련되어 있으며 느린 실행 또는 로드 불가능이 특징입니다. 사전 예방적으로 용량을 관리하면 이 문제가 크게 감소됩니다.
 * 구성 - 이 문제는 일반적으로 새 서비스의 프로비저닝에서 발견되거나 변경사항을 적용하는 데 따른 결과입니다. 올바르지 않은 설정은 가용성 또는 활용도 증상으로 표시될 수 있습니다. 예를 들어, 올바르지 않은 IP 주소는 가용성 문제로 표시되지만 가상 머신(VM) RAM을 너무 낮게 설정하면 활용도 증상이 발생합니다.
* 문제를 환경의 컴포넌트로 분리해 보십시오.
* 단계를 추적할 수 있도록 적어 두십시오.
* 소프트웨어 버전을 이해하고 문서화하십시오.
* VIP 및 NAT 주소를 포함하여 서브넷 및 IP 주소 사용량을 문서화하십시오.
* 네트워크의 다이어그램을 보유하십시오. 많은 수의 실제(언더레이) 및 논리(오버레이) 계층을 표시하는 다이어그램이 필요합니다.
* 환경에 대한 최신 변경사항을 이해하십시오.
* 수정사항의 영향을 조사하십시오. 관리 인터페이스를 스스로 잠그지 마십시오.
* 다시 로드하거나 재설정해야 하는 경우 모든 핵심 컴포넌트의 백업이 있는지 확인하십시오.
* 동시에 둘 이상의 항목을 변경하지 마십시오.
* 각 변경사항 및 해당 결과를 문서화하십시오.
* 지원 요청을 여는 경우 신중하게 문서화하고 적절한 정보를 제공해야 합니다. 발견하는 증상을 결함을 명확히 하고 결함이 있다고 판단되는 컴포넌트를 식별하십시오. 올바른 용어를 사용하는지 확인하십시오. 단어 선택 시 혼란이나 모호성을 최소화하십시오.
* vSphere ESXi 및 vCenter Server 구성 파일은 시스템의 동작을 제어하고 해당 위치를 이해합니다. 대부분의 구성 파일 설정은 설치 중에 수행되지만 설치 후에 수정될 수 있습니다.
* 로그 파일은 커널 및 여러 서비스 시스템과 서비스에서 생성되는 메시지를 캡처합니다. vSphere ESXi 및 vCenter 서비스는 개별 로그 파일을 유지보수합니다. 위치와 액세스 방법을 이해합니다.
* 진단에 도움이 되도록 인기 있는 시스템 관리 도구의 사용 방법을 이해하십시오.

자세한 정보는 [문제점 해결 가이드라인 KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}을 참조하십시오.

## 로그 파일을 사용한 문제점 해결
{: #opsprocs-trouble-logs}

로그 파일은 문제를 해결하기 위한 최상의 정보 소스입니다. 그러나 로그 파일 수 및 각 로그 항목의 방대한 양은 문제 해결을 어렵게 만듭니다. [로그 파일을 사용한 문제점 해결 KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window}에서는 VMware 환경에 있는 이 로그 파일의 위치에 대한 세부사항을 제공합니다. 로그 파일의 수 및 각 로그 항목의 방대한 수로 인해, 이벤트 로그의 캡처와 분석을 지원하려면 Operations Management on {{site.data.keyword.cloud_notm}}의 도구를 고려해야 합니다.

## 공통 시나리오 문제점 해결
{: #opsprocs-trouble-common}

영향을 받는 컴포넌트를 격리하는 데 도움이 되도록 공통 시나리오 문제점 해결에 대한 이 문서는 다음과 같이 분류되어 있습니다.

* 가상 머신 - 이 문제점 해결 주제에서는 VM의 가능성 있는 문제에 대한 지침을 제공합니다.
* 호스트 - 이 문제점 해결 주제에서는 vSphere ESXi 호스트 문제에 대한 지침을 제공합니다.
* 클러스터 - 이 문제점 해결 주제에서는 가용성 및 리소스 관리에 대한 지침을 제공합니다.
* 스토리지 - 이 문제점 해결 주제에서는 vSAN 및 NFS 스토리지 문제 해결에 대한 지침을 제공합니다.
* 네트워크 - 이 문제점 해결 주제에서는 네트워크 문제 해결에 대한 지침을 제공합니다.
* vCenter - 이 문제점 해결 주제에서는 vCenter 문제 해결에 대한 지침을 제공합니다.
* 라이센스 - 이 문제점 해결 주제에서는 라이센스 문제 해결에 대한 지침을 제공합니다. 이는 일반적으로 {{site.data.keyword.cloud_notm}}에 자체 라이센스를 가져오는 클라이언트와 관련됩니다.

### 가상 머신
{: #opsprocs-trouble-common-vm}

표 1. 가상 머신 문제점 해결

| 제목 |설명 |
|---|---|
| 일반 VM 문제 해결 |자세한 정보는 [가상 머신 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}을 참조하십시오. |
| VM 성능 문제 |VM 성능 문제(예: 게스트 OS가 느리게 부팅함, 애플리케이션 성능이 저하됨, 애플리케이션 실행에 오랜 시간이 걸림 또는 애플리케이션이 응답하지 않음) 증상의 문제점 해결에 대한 정보는 [ESX/ESXi 가상 머신 성능 문제 해결(2001003)](https://kb.vmware.com/s/article/2001003){:new_window}을 참조하십시오. |
| 사용되지 않는 VM 복구 | 사용되지 않는 VM(vCenter 데이터베이스에 존재하는 VM이지만 vSphere ESXi 호스트에서 인식되지 않음) 복구에 대한 정보는 [Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}을 참조하십시오. |
| VM의 전원이 켜지지 않음 | 자세한 정보는 [전원이 켜지지 않는 가상 머신 문제점 해결(2001005)](https://kb.vmware.com/s/article/2001005){:new_window}을 참조하십시오. |
| 템플리트에서 복제하거나 배치한 후 VM의 전원이 켜지지 않음 | [VMware 문서](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window}에서는 템플리트에서 복제되거나 배치된 후 VM에 영향을 주는 문제를 다룹니다. |
| VMware Tools가 유효하지 않거나 설치되어 있지 않음 - VMware Tools는 VM에 설치되어야 하고 최신 상태로 유지되어야 합니다. | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window}에서는 이 태스크에 대한 지침을 제공합니다. |
| 이전 VM 네트워크 디바이스 | VM 네트워크 디바이스가 최신 네트워크 성능을 유지하지 않음에 따라 애플리케이션 성능에 영향을 줄 수 있습니다. 새 가상 네트워크 디바이스 및 드라이버에 대한 자세한 정보는 [가상 머신에 적합한 네트워크 어댑터 선택(1001805)](https://kb.vmware.com/s/article/1001805){:new_window}을 참조하십시오. |
| 가상 머신 메모리 한계 | 일반적으로 메모리 한계가 적용됩니다. 그러나 게스트 OS가 필요한 메모리에 액세스할 수 없으면 게스트 OS 내의 애플리케이션의 성능이 저하될 수 있습니다. 이 문제 해결에 대한 자세한 정보는 [리소스 할당 설정 구성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}을 참조하십시오. |
| VM 스냅샷 | 스냅샷은 유용하지만 VM 스냅샷의 양과 수명은 VM의 성능에 직접적인 영향을 줍니다. 이 문제 해결에 대한 정보는 [스냅샷 통합](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}을 참조하십시오. |
| VM 로깅 | 로깅이 올바르게 구성되어 있지 않으면 스냅샷의 용량에 부정적인 영향을 줄 수 있습니다. 이 문제 해결에 대한 정보는 [게스트 운영 체제에 대한 로깅 레벨 구성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}을 참조하십시오. |
| 네트워크 연결 문제 해결 | 증상에는 VM이 네트워크 연결에 실패함 또는 단일 VM으로의 네트워크 연결 또는 단일 VM에서의 네트워크 연결 없음이 포함될 수 있습니다. 이 문제 해결에 대한 정보는 [가상 머신 네트워크 연결 문제 해결(1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오.  |
| 다중 가상 CPU로 인해 성능 문제가 발생하는지를 판별함  | VM이 다중 CPU로 구성될 때 경험하는 성능 문제 해결에 대한 정보는 [다중 가상 CPU로 인해 성능 문제가 발생하는지를 판별함(1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오. 여기에는 데이터를 VM에서 또는 VM으로 데이터를 복사할 때 전송 속도가 느려지거나, 백업 작업이 제한시간을 초과하거나 속도가 느려지거나, VM 성능이 저하되는 문제가 포함될 수 있습니다.  |
| VM의 전원이 꺼지거나 다시 시작됨  | 문제 해결에 대한 정보는 [가상 머신의 전원이 꺼지거나 다시 시작되는 이유를 판별함(1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}을 참조하십시오. |
| 하나 이상의 VM 응답 시간이 느려짐 | vSphere ESXi 호스트에 대한 성능 문제 격리에 대한 정보는 [ESX/ESXi 가상 머신 성능 문제 해결(2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}을 참조하십시오. 성능 문제는 CPU 제한조건, 메모리 과다 할당, 스토리지 대기 시간 또는 네트워크 대기 시간으로 인해 발생할 수 있습니다. |

### vSphere ESXi 호스트
{: #opsprocs-trouble-common-host}

표 2. 일반적인 vSphere ESXi 호스트 문제점 해결

| 제목 |설명 |
|---|---|
| ESXI 명령 | vSphere의 명령행 인터페이스, ESXi Shell 명령 및 vCLI(VMware® vSphere Command Line Interface) 명령의 개요는 [vSphere Command-Line Interface 시작하기](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}를 참조하십시오. |
| vSphere HA 호스트 상태 | vCenter가 호스트의 오류 조건을 표시하는 vSphere HA 호스트 상태를 보고하는 경우 이 문제로 인해 실패 후 vSphere HA에서 VM을 다시 시작할 수 없음에 따라 수정되어야 합니다. 자세한 정보는 [vSphere HA 호스트 상태 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}을 참조하십시오. |
| vSphere ESXi 호스트가 응답하지 않음 상태에 있음 | 응답하지 않음, 연결이 끊어짐으로 표시되는 vSphere ESXi 호스트 또는 vCenter에서 사용 불가능으로 표시되는 호스트의 VM에 대한 정보는 [ESX/ESXi 호스트가 응답하지 않고 비활성으로 표시됨(1019082)](https://kb.vmware.com/s/article/1019082){:new_window}을 참조하십시오. |
| VM의 전원이 켜져 있는 경우 `File not found` 오류가 표시됨 | 유실된 가상 디스크 디스크립터 파일(VMDK) 다시 작성에 대한 정보는 [유실된 가상 머신 디스크 디스크립터 파일 다시 작성(1002511)](https://kb.vmware.com/s/article/1002511){:new_window}을 참조하십시오. |
| VM 성능 문제 | vSphere ESXi 호스트에 대한 성능 문제 격리에 대한 정보는 [ESX/ESXi 가상 머신 성능 문제 해결(2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}을 참조하십시오. 성능 문제는 CPU 제한조건, 메모리 과다 할당, 스토리지 대기 시간 또는 네트워크 대기 시간으로 인해 발생할 수 있습니다. |
| 베어메탈 서버의 작동이 중지됨 | vSphere ESXi가 실행되는 베어메탈 서버가 응답하지 않거나 작동 중지된 경우 {{site.data.keyword.cloud_notm}} 관리 UI 또는 콘솔에 로그온하고 상태를 확인하십시오. 필요한 경우 베어메탈 서버에 대한 지원을 받도록 사례를 여십시오. 자세한 정보는 [지원 사례 관련 작업](/docs/get-support?topic=get-support-open-case#open-case){:new_window}을 참조하십시오. |
| vSphere ESXi 호스트가 연결이 끊어져 있거나 응답하지 않음 상태에 있음  | 자세한 정보는 [응답하지 않음 상태에 있는 ESXi/ESX 호스트 문제점 해결(1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}을 참조하십시오. |
| PSOD(Purple Screen of Death)  | PSOD(Purple Screen of Death)는 커널 패닉이며 vSphere ESXi 커널(vmkernel)이 복구할 수 없는 이벤트 또는 오류에 대한 응답으로 이 안전 조치를 트리거하고 실행을 계속하면 서비스 및 VM에 대한 위험이 높아짐을 의미합니다. 패닉이 발생하고 vSphere ESXi 호스트가 충돌하면 모든 VM이 호스팅된 상태에서 함께 실행되는 모든 서비스가 종료됩니다. VM이 정상적으로 종료되지 않고 갑자기 전원이 꺼집니다. 호스트가 클러스터의 일부이고 HA를 구성한 경우 이 VM은 클러스터의 다른 호스트에서 다시 시작됩니다. 자세한 정보는 [Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}을 참조하십시오. |

### 스토리지
{: #opsprocs-trouble-common-storage}

표 3. 일반적인 스토리지 문제점 해결

| 제목 |설명 |
|---|---|
| 스토리지 문제점 해결 | 느린 성능, 예측할 수 없는 실패, 디스크 손상 또는 VM 손상에 대한 자세한 정보는 [VMware 제품을 사용하는 경우 스토리지 문제 해결(2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}을 참조하십시오. |
| vSAN 문제점 해결 | 자세한 정보는 [vSAN에서 실패 처리](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}를 참조하십시오.  |
| vSAN 디스크 실패 | 실패한 디스크 식별 방법 및 요청 대체 방법에 대한 자세한 정보는 [VMware vSAN 디스크 그룹에서 하드 디스크/자기 디스크 실패(2077185)](https://kb.vmware.com/s/article/2077185){:new_window}를 참조하십시오. |
| vSAN 상태 문제 지우기 |VMware vSphere Web Client 모니터 페이지에서 vSAN 상태 문제와 관련된 경보 및 경고가 표시될 수 있습니다. 이러한 문제 지우기에 대한 정보는 [Virtual SAN 상태 경보 및 경고](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}를 참조하십시오.|
| vSAN 다시 밸런싱 | 디스크가 상태 검사에서 클러스터가 올바르게 밸런싱되어 있지 않고 다른 디스크의 공간 사용량은 낮은 반면 공간 사용량이 높은 디스크가 있음을 표시하는 오류를 보고하는 경우 사전 예방적 다시 밸런싱을 실행해야 합니다. 이는 vSAN 클러스터에서 오브젝트의 다시 밸런싱을 수동으로 시작합니다. vSAN 사전 예방적 다시 밸런싱 및 적용 가능한 시기에 대한 자세한 정보는 [vSAN 사전 예방적 다시 밸런싱(2149809)](https://kb.vmware.com/s/article/2149809){:new_window}을 참조하십시오. |
| vSAN 상태 테스트 시작 | vSAN에 문제가 있다고 의심되는 경우 클러스터 컴포넌트가 예상대로 작동하는지 확인하기 위해 상태 테스트를 시작할 수 있습니다. VM 작성 테스트를 실행하면 클러스터의 각 호스트마다 VM이 작성된 후 삭제됩니다. 이 태스크가 성공적이면 클러스터 컴포넌트가 예상대로 작동하고 클러스터가 기능을 수행합니다. 그런 다음 네트워크 성능 테스트가 수행되어 연결 문제를 발견하고 진단하며 호스트 간의 네트워크 대역폭이 적절한지 확인합니다. 자세한 정보는 [사전 예방적 테스트](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}를 참조하십시오. |
| vSAN 성능 모니터링 | 자세한 정보는 [vSAN 성능 모니터링](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}을 참조하십시오. 성능 차트는 클러스터, 호스트, 실제 디스크, VM 및 가상 디스크에 사용 가능합니다. |
| vSAN 문제점 해결 | 자세한 정보는 [실패 처리 및 vSAN 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}을 참조하십시오. |


### 네트워크
{: #opsprocs-trouble-common-network}

표 4. 일반적인 네트워크 문제점 해결

| 제목 |설명 |
|---|---|
| NSX Edge/var/log는 활성 에지에 가득 찼음 | 에지 디스크의 여유 공간이 없다는 경보가 발행되고 /var/log 파티션이 가득 차 있음을 발견한 경우의 임시 해결책에 대한 정보는 [NSX Edge/var/log가 활성 에지에서 가득 참(50108355)](https://kb.vmware.com/s/article/50108355){:new_window}을 참조하십시오.  |
| HCX 대역폭 테스트  | HCX에 네트워크 대역폭 문제가 있는 경우 HCX 터널 내에 사용 가능한 대역폭을 찾기 위해 `perftest`를 사용하는 데 대한 정보는 [HCX에서 Perftest를 실행하는 단계(56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}를 참조하십시오. 각 `perftest`에 대한 양방향 테스트가 수행됩니다. 게이트웨이 쌍의 경우 하나는 OnPrem라고 하는 소스 데이터 센터 내에 있고 다른 하나는 {{site.data.keyword.cloud_notm}}에 있습니다. `perftest` 처리량의 작동 방식은 발신자가 링크를 유지할 수 있는 만큼 빠르게 전송하도록 하는 것입니다. 따라서 각 테스트에서 "전송자" 비율이 "수신자" 비율보다 더 높아짐을 알게 됩니다. "수신자" 비율 값을 단방향 처리량 결과로 간주할 수 있습니다. |
|HCX 문제점 해결 |자세한 정보는 [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)을 참조하십시오. |
| HCX 동기화 상태는 0%의 진행상태와 0바이트를 표시하며 상태 오류가 발생함 | 자세한 정보는 [HCX 복제본이 동기화 상태로 0%의 진행상태와 0바이트를 표시하며 상태 오류가 발생함(56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}을 참조하십시오. |
| VM 네트워크 성능이 나쁨 | VM 가상 NIC 설정을 검토하십시오. VMware는 성능을 위해 설계된 최신 Paravirtualized NIC이므로 VM용 VMXNET 3 가상 NIC를 권장합니다. VMXNET 3의 호환성을 확인하고 지원되는 경우 추가 네트워크 성능을 위해 가상 NIC를 변경하십시오. 자세한 정보는 [네트워킹 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}을 참조하십시오. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

표 5. 일반적인 vCenter 문제점 해결

| 제목 |설명 |
|---|---|
| 가상 머신 콘솔 액세스 |자세한 정보는 [Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}을 참조하십시오. |
| 새 vCenter Server 인증서가 로드하도록 표시되지 않음 | 기본 vCenter Server 인증서 대체 후 새 인증서가 로드하도록 표시되지 않을 수 있습니다. 자세한 정보는 [새 vCenter Server 인증서가 로드하도록 표시되지 않음](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}을 참조하십시오. |
| vCenter Server가 관리 호스트에 연결할 수 없음 | 기본 vCenter Server 인증서 대체되고 시스템을 다시 시작한 후 vCenter Server가 관리 호스트에 연결할 수 없습니다. 자세한 정보는 [vCenter Server가 관리 호스트에 연결할 수 없음](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}을 참조하십시오. |
| 사용자 정의 SSL 인증서를 사용할 때 vSphere HA를 구성할 수 없음 | 사용자 정의 SSL 인증서를 설치한 후 vSphere High Availability(HA)가 실패되도록 시도하십시오. 자세한 정보는 [사용자 정의 SSL 인증서를 사용할 때 vSphere HA를 구성할 수 없음](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}을 참조하십시오. |

### 라이센스
{: #opsprocs-trouble-common-licenses}

표 6. 일반적인 라이센스 문제점 해결

| 제목 |설명 |
|---|---|
| 호환되지 않거나 올바르지 않은 라이센스 구성 |자세한 정보는 [호스트 라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}을 참조하십시오. |
| VM의 전원이 켜지지 않음 | vSphere ESXi 호스트에서 VM 전원을 켤 수 없거나 ``The 60-day evaluation period of the host is expired or the license of the host is expired`` 메시지를 수신하는 경우 라이센스 문제가 있을 수 있습니다. 자세한 정보는 [가상 머신의 전원을 켤 수 없음](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}을 참조하십시오. |
| 기능이 사용 불가능하거나 구성을 변경할 수 없음  | 자세한 정보는 [기능을 구성하거나 사용할 수 없음](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}을 참조하십시오.  |


## 관련 링크
{: #opsprocs-trouble-links}

* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [vSphere 문제점 해결 개요](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:new_window}
* [로그를 사용한 vSphere 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [로그 수집 지원](https://kb.vmware.com/s/article/1010705){:new_window}
* [이벤트, 알람 및 자동화된 조치 모니터링](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere 시스템 로그 파일](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

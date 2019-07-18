---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-02"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 알람
{: #opsprocs-alarms}

## 소개
{: #opsprocs-alarms-intro}

vSphere에는 vSphere 환경에서 발생하는 이벤트를 추적하고 이 정보를 사용할 수 있도록 하는 이벤트 및 알람 서브시스템이 포함됩니다. 이 서브시스템에서는 다음 용어가 사용됩니다.

### 이벤트
{: #opsprocs-alarms-events}

이벤트는 호스트 및 가상 머신(VM)과 같은 vCenter의 오브젝트에서 발생하는 시스템 또는 사용자 조치의 레코드입니다. 이벤트 데이터에는 생성자, 발생 시기 및 이벤트 유형과 같은 이벤트 정보에 대한 세부사항이 포함됩니다. vSphere Web Client에서 이벤트 데이터는 모니터 탭에 표시됩니다.

이벤트는 다음과 같이 분류됩니다.
* 오류 - 시스템에서 발생하는 복구 불가능한 문제점을 표시하고 프로세스 또는 오퍼레이션을 종료합니다.
* 경고 - 시스템에 미치는 잠재적인 위험성이 있으며, 이 위험성은 해결되어야 함을 표시합니다. 이 이벤트는 프로세스 또는 오퍼레이션을 종료하지 않습니다.
* 정보 - 사용자 또는 시스템 오퍼레이션이 완료되었음을 설명합니다.
* 감사 - 감사 로그 데이터에는 조치의 개념, 사용자, 발생 시점 및 사용자의 IP 주소에 대한 정보가 포함되어 있습니다.

### 알람
{: #opsprocs-alarms-alarms}

알람은 이벤트, 조건 세트 또는 인벤토리 오브젝트의 상태에 대한 응답으로 활성화되는 알림입니다.

알람 정의는 vSphere Client의 다음 요소로 구성됩니다.
* 이름 및 설명 - 식별 레이블 및 설명을 제공합니다.
* 대상 - 모니터되는 오브젝트의 유형을 정의합니다.
* 알람 규칙 - 알람을 트리거하고 알림 심각도를 정의하는 이벤트, 조건 또는 상태를 정의합니다. 또한 트리거된 알람에 대한 응답으로 발생하는 오퍼레이션도 정의합니다.
* 마지막 수정 날짜 - 정의된 알람에 대해 마지막으로 수정된 날짜입니다.

알람의 심각도 레벨은 다음과 같습니다.
* 보통 - 초록색입니다.
* 경고 - 노란색입니다.
* 경보 - 빨간색입니다.

### 알람 정의
{: #opsprocs-alarms-def}

알람 정의는 인벤토리에서 선택된 오브젝트와 연관되며 정의에 지정된 인벤토리의 유형을 모니터합니다.

알람 정의는 다음 요소로 구성됩니다.
* 이름 및 설명 - 식별 레이블 및 설명을 제공합니다.
* 알람 유형 - 모니터되는 오브젝트의 유형을 정의합니다.
* 트리거 - 알람을 트리거하고 알림 심각도를 정의하는 이벤트, 조건 또는 상태를 정의합니다.
* 임계값(보고) - 알람이 트리거되기 전에 실행되어야 하는 조건 및 상태 트리거에 대한 더 많은 제한사항을 제공합니다.
* 조치 - 트리거된 알람에 대한 응답으로 발생하는 오퍼레이션도 정의합니다. VMware는 인벤토리 오브젝트 유형에 특정한 사전 정의된 조치 세트를 제공합니다.
* 알람 조치 - 알람 조치는 트리거에 대한 응답으로 발생하는 오퍼레이션입니다. 예를 들어, 알람이 트리거될 때 한 명 이상의 관리자에게 전송되는 이메일 알림이 사용자에게 제공될 수 있습니다.
* 수신확인 트리거 알람 - 알람을 수신확인한 후 알람 조치가 중단됩니다. 알람은 선택 취소되지 않거나 수신확인 시 재설정됩니다. 알람을 수신확인하면 문제의 소유권을 가져오고 있음을 다른 사용자가 알게 됩니다.
* 트리거된 알람 재설정 - vCenter가 정상 상태를 식별하는 이벤트를 검색하지 않는 경우 이벤트로 트리거되는 알람은 정상 상태로 다시 설정되지 않을 수 있습니다. 해당 경우 알람을 수동으로 재설정하십시오.
* 사전 구성된 vSphere 알람 - vSphere 이벤트 및 알람 서브시스템에는 vSphere 인벤토리 오브젝트의 오퍼레이션을 모니터하는 많은 기본 알람이 있습니다. 이 알람에 대한 조치만 설정해야 합니다.

## 알람 설정 워크플로우
{: #opsprocs-alarms-setup-workflow}

VMware는 다음 표에서 설명되는 사전 구성된 vCenter 알람을 제공하지만 해당 알람은 vCentre Web Client 내에서만 표시될 조치로 설정됩니다. IBM 지침에는 SMTP 서버 세부사항을 구성한 후 시스템 관리자 팀에게 알람이 쇄도하지 않도록 처음에만 다음 알람에 대해 시스템 관리자에게 이메일을 발송하도록 경보 조치를 설정하는 내용이 있습니다. 자세한 정보는 [알람 조치로 이메일 전송](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-1F940DAF-933B-44B7-A200-7A11B5D3E3D5.html){:new_window}을 참조하십시오.

설정 알람 워크플로우는 다음과 같습니다.
* SMTP 서버 세부사항을 구성합니다.
* 클러스터, 호스트, 데이터 저장소 및 중요 가상 어플라이언스(VCSA, PSC, NSX Manager 및 NSX Controller)에 대한 경보 조치를 구성합니다.
  * 클러스터 - VMware 고가용성 오류입니다.
  * 호스트 - CPU 상태, 메모리 상태, 스토리지 상태, 하드웨어 상태 즉, 전압, 온도 또는 전원 상태 변경입니다.
  * 데이터 저장소 - 디스크 여유 공간이 부족합니다.
  * 중요 가상 어플라이언스 - CPU 사용량, 메모리 사용량, 디스크 대기 시간입니다.
* 사전 예방적 일별 태스크 사용:
  * 전송된 경보 검토 - 정말 필요합니까?
  * 전송되지 않은 경보 검토 - 이 경보에 대해 알고 있어야 합니까?
  * 메트릭 검토 - 메트릭이 올바릅니까? 예를 들어, 기준선을 이해하고 있는 경우 CPU 사용량이 90%가 아닌 75%로 설정되어야 합니까?
  * 자체 알람을 구성해야 합니까?
  * 가상 머신을 포함해야 합니까?

##  일반적인 알람 워크플로우
{: #opsprocs-alarms-alarm-workflow}

설정된 후, 알람이 트리거되었을 때 일반적으로 시스템 관리자가 도입하는 알람 워크플로우의 예는 다음과 같습니다.

1. 이전 절에서 설명된 대로, 호스트에는 CPU 사용량을 모니터하도록 설정된 알람이 있고 알람에는 알람이 트리거될 때 관리자에게 이메일을 발송하기 위한 알람 조치가 있습니다.
3. 관리자에게 이메일을 발송하는 알람을 트리거하여 호스트 CPU 사용량이 급증합니다.
4. 문제점이 해결되고 있음을 다른 관리자에게 알리고, 알람이 추가 이메일 메시지를 전송하지 않도록 관리자 중 한 명이 vCenter에 로그인하고 트리거된 알람을 수신확인합니다. 그러나 알람은 계속해서 시스템에 표시됩니다.
5. 관리자가 CPU 급증의 원인을 찾고 정정합니다.
6. 알람이 자동으로 재설정됩니다.

## 사전 구성된 알람 - 표준
{: #opsprocs-alarms-preconfigured-std}

다음 표에서는 이 항목에 대해 설명합니다.

* 알람 이름 - vCenter에 표시되는 알람의 이름입니다.
* 지침 - 이 알람의 사용에 대한 IC4V 지침입니다.
* 자세한 정보 - 트리거된 후 이 알람에 대한 해결을 지원하도록 IBM 또는 VMware에서 추가 정보를 확인할 수 있습니다.

표 1. 사전 구성된 알람

| 알람 이름 | 지침 |자세한 정보 |
|---|---|---|
| 호스트 연결 및 전원 상태 | 응답하지 않음 또는 대기로 설정되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [초록색에서 빨간색으로 변경되는 호스트 연결 상태에 대한 알람이 자주 발생함(1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| 호스트 CPU 사용량 | 5분 동안 호스트 CPU 사용량이 90%보다 큰 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012707 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=342e3d6adbc5730030c93a1b7c961976){:new_window} |
| 호스트 메모리 사용량 | 5분 동안 호스트 메모리 사용량이 95%보다 큰 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012712 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=30110ee2db49730030c93a1b7c96194f){:new_window} |
| 가상 머신 CPU 사용량 | 5분 동안 중요한 어플라이언스에 대한 VM CPU 사용량이 90%보다 큰 경우에 이메일을 한 번 발송하도록 구성합니다. | [가상 머신 CPU 사용량 알람(2057830)](https://kb.vmware.com/s/article/2057830){:new_window} |
| 가상 머신 메모리 사용량 | 5분 동안 중요한 어플라이언스에 대한 VM 메모리 사용량이 90%보다 큰 경우에 이메일을 한 번 발송하도록 구성합니다. | [가상 머신 메모리 사용량 알람(2057846)](https://kb.vmware.com/s/article/2057846){:new_window} |
| 디스크에 대한 데이터 저장소 사용량 | vSAN의 경우 데이터 저장소 사용량이 70%보다 크면 이메일을 발송하고, 비vSAN의 경우 데이터 저장소 사용량이 85%보다 큰 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012713 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=ddb3422edb89730030c93a1b7c9619f6){:new_window} |
| 가상 머신 CPU 준비 시간 | 5분 동안 중요한 어플라이언스에 대한 VM CPU 준비 시간이 2000ms보다 긴 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012718 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=7056426adb0d730030c93a1b7c9619e6){:new_window} |
| 가상 머신 총 디스크 대기 시간 | 5분 동안 VM 총 디스크 대기 시간이 30ms보다 긴 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012729 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=15dddea2db857300d5a971198c961995){:new_window} |
| 가상 머신 디스크 명령이 취소됨 | 초기에 설정하지 마십시오. 두 번째 단계에서 중요한 어플라이언스를 고려하십시오. | 추가 정보 없음 |
| 가상 머신 디스크가 재설정됨 | 초기에 설정하지 마십시오. 두 번째 단계에서 중요한 어플라이언스를 고려하십시오. | 추가 정보 없음 |
| 라이센스 인벤토리 모니터링 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} 및 [ESXi 6.x 및 vCenter Server 6.x 라이센싱](https://kb.vmware.com/s/article/2107538){:new_window} |
| 라이센스 사용자 임계값 모니터링 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 라이센스 용량 모니터링 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 호스트 라이센스 에디션이 vCenter Server 라이센스 에디션과 호환되지 않음 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [호스트 라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window} |
| 보조 VM을 시작하는 중에 제한시간이 초과됨 * | VMware Fault Tolerance를 모니터하므로 구성되지 않습니다. vCenter Server 인스턴스에 권장되지 않습니다. | [보조 VM을 시작하는 중에 제한시간이 초과됨(2064169)](https://kb.vmware.com/s/article/2064169){:new_window} |
| 보조 VM에 대한 호환 가능 호스트가 없음 | VMware Fault Tolerance를 모니터하므로 구성되지 않습니다. vCenter Server 인스턴스에 권장되지 않습니다. | 추가 정보 없음 |
| 가상 머신 결함 허용 상태가 변경됨 | VMware Fault Tolerance를 모니터하므로 구성되지 않습니다. vCenter Server 인스턴스에 권장되지 않습니다. | 추가 정보 없음 |
| 가상 머신 결함 허용 vLockStep 간격 상태가 변경됨 | VMware Fault Tolerance를 모니터하므로 구성되지 않습니다. vCenter Server 인스턴스에 권장되지 않습니다. | 추가 정보 없음 |
| 호스트 프로세서 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 메모리 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 하드웨어 팬 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 하드웨어 전압 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 하드웨어 온도 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 하드웨어 전원 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다.| [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 하드웨어 시스템 보드 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 배터리 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다.| [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 기타 호스트 하드웨어 오브젝트 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 스토리지 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 IPMI 시스템 이벤트 로그 상태 |영향을 주는 서비스가 아니므로 구성되지 않습니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 베이스 보드 제어기 상태 | 모니터가 초록색에서 빨간색으로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 호스트 오류 * | 모니터가 오류로 변경되는 경우에 이메일을 한 번 발송하도록 구성합니다. | [IBM 지원 센터에 문의](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 가상 머신 오류 * | 중요한 어플라이언스에 대해 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [가상 머신 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window} |
| 호스트 연결 실패 * | 이벤트가 호스트에 연결할 수 없음, 네트워크 오류 또는 호스트에 연결할 수 없음, 제한시간 초과 또는 호스트 연결이 끊어짐이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [초록색에서 빨간색으로 변경되는 호스트 연결 상태에 대한 알람이 자주 발생함(1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| 관리되지 않은 워크로드가 SIOC 사용 데이터 저장소에서 발견됨 |영향을 주는 서비스가 아니므로 구성되지 않습니다. | [관리되지 않는 워크로드가 SIOC를 실행 중인 데이터 저장소에서 발견됨(1020651)](https://kb.vmware.com/s/article/1020651){:new_window} |
| 씬 프로비저닝된 볼륨 용량 임계값을 초과함 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| 데이터 저장소 기능 알람 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| VASA 제공자 연결 끊기 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| VASA 제공자 인증서 만기 알람 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| VM 스토리지 규제 준수 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [VM 스토리지 준수 알람(2061940)](https://kb.vmware.com/s/article/2061940){:new_window} |
| 데이터 저장소 규제 준수 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [데이터 저장소 관련 작업](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-3CC7078E-9C30-402C-B2E1-2542BEE67E8F.html){:new_window} |
| VASA 제공자에 대한 CA 인증서 및 CRL을 새로 고치는 데 실패함 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| 충분하지 않은 vSphere HA 장애 복구 리소스 | 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [Knowledge - KB0012739 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=fe1f0beedb8db300d5a971198c96191a){:new_window} |
| vSphere HA 장애 복구 진행 중 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSphere HA 마스터 에이전트를 찾을 수 없음 | HA 마스터 에이전트를 찾을 수 없거나 이와 통신할 수 없는 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere 가용성 정보](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.avail.doc/GUID-63F459B7-8884-4818-8872-C9753B2E0215.html){:new_window} |
| vSphere HA 호스트 상태  | 호스트의 vSphere HA 에이전트에 오류가 발생하거나, vSphere HA가 네트워크 격리 호스트를 발견하거나, vSphere HA가 네트워크 격리 호스트를 발견하거나, vSphere HA가 네트워크 파티셔닝 호스트를 발견하거나, vSphere HA가 호스트 장애를 발견한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere HA 호스트 상태 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window} |
| vSphere HA 가상 머신 장애 복구에 실패함 | 중요한 어플라이언스에 대해 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere HA 클러스터 작성 및 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA 가상 머신 모니터링 조치 | 중요한 어플라이언스에 대해 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere HA 클러스터 작성 및 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA 가상 머신 모니터링 오류 | 중요한 어플라이언스에 대해 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere HA 클러스터 작성 및 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA VM Component Protection이 가상 머신의 전원을 끌 수 없음 | 중요한 어플라이언스에 대해 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere HA 클러스터 작성 및 사용](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| 라이센스 오류 * | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 상태가 변경됨 * | 상태가 위험으로 변경될 때 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [호스트 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-6F6CE545-58FA-490B-8C8A-3CB8196CAEA8.html){:new_window} |
| 스토리지 DRS 권장사항 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [DRS 문제점 해결 정보](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| 스토리지 DRS가 호스트에서 지원되지 않음 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [DRS 문제점 해결 정보](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| 데이터 저장소 클러스터의 공간이 부족함 | 디스크 사용량이 85%를 초과할 때 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 인스턴스에 NFS 스토리지 추가](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances) |
| 데이터 저장소가 여러 데이터 센터에 있음 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [스토리지 DRS가 데이터 저장소에서 작동하지 않음](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-976F5B21-8C64-4C85-BE75-0D86655E32DD.html){:new_window} |
| vSphere Distributed Switch VLAN이 상태를 선택함 | vSphere Distributed Switc에서 구성된 VLAN이 실제 스위치로 모두 선택되지 않았을 때 위험한 경우에 이메일을 한 번 발송하도록 구성합니다. | [vSphere Web Client에서 vSphere Distributed Switch 상태 검사 사용(2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU가 상태를 일치시킴  | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSphere Web Client에서 vSphere Distributed Switch 상태 검사 사용(2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU가 상태를 지원함 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSphere Web Client에서 vSphere Distributed Switch 상태 검사 사용(2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch 팀 구성이 상태를 일치시킴 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSphere Web Client에서 vSphere Distributed Switch 상태 검사 사용(2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| 가상 머신 네트워크 어댑터 예약 상태 | 네트워크 어댑터 예약을 사용으로 설정한 경우에만 이메일을 발송하도록 구성합니다. | [가상 머신에 대한 대역폭 할당 구성](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-FECAC41A-2C7A-4AD6-B740-7D8D44BADB52.html){:new_window} |
| 가상 머신 통합 필요 상태 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [스냅샷을 사용하여 가상 머신 관리](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-CA948C69-7F58-4519-AEB1-739545EA94E5.html){:new_window} |
| 호스트 가상 플래시 리소스 상태 | 호스트 가상 플래시는 vCenter Server 인스턴스에서 지원되지 않습니다. | 추가 정보 없음 |
| 호스트 가상 플래시 리소스 사용량 | vCenter Server 인스턴스가 호스트 가상 플래시를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | [가상 플래시 리소스 정보](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-E69F0809-3B19-483A-B906-4CE397CE56D6.html){:new_window} |
| vSAN 호스트에서 VASA 공급업체 제공자의 등록/등록 해제 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | [VMware 호환성 안내서](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| 호스트에서 서드파티 IO 필터 스토리지 제공자의 등록/등록 해제에 실패함 | vCenter Server 인스턴스가 VASA 스토리지를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | [VMware 호환성 안내서](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| 서비스 제어 에이전트 상태 알람 | 컴포넌트 ID가 sca이고 새 상태가 빨간색인 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| ID 상태 알람 | 컴포넌트 ID가 identity이고 새 상태가 빨간색인 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vSphere Web Client 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [VMware vSphere 5.x/6.x Web Client 서비스에서 디버그 로깅 사용(2011485)](https://kb.vmware.com/s/article/2011485){:new_window} |
| ESX Agent Manager 상태 알람 | 컴포넌트 ID가 `eam`이고 새 상태가 `red`인 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 메시지 버스 구성 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| Cis 라이센스 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 인벤토리 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vCenter Server 상태 알람 | 컴포넌트 ID가 vpxd이고 새 상태가 빨간색인 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 데이터베이스 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 데이터 서비스 상태 알람 | 컴포넌트 ID가 vmware-dataservices-sca이고 새 상태가 빨간색인 경우에 이메일을 한 번 발송하도록 구성합니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| RBD 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vService Manager 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 성능 차트 서비스 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 컨텐츠 라이브러리 서비스 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 전송 서비스 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vSphere ESXi Dump Collector 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다.| [VMware ESXi Dump Collector 지원](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-F8773E25-BD6A-4A6C-A999-D58CB853BA8A.html){:new_window} |
| VMware vAPI Endpoint Service 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware System and Hardware Health Manager Service 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [로그를 사용한 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window} |
| VMware vSphere Profile-Driven Storage Service 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vFabric Postgres Service 상태 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 6.x 서비스의 중지, 시작 또는 다시 시작 방법(2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| ESXi 호스트 인증서 업데이트 실패 상태 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 및 ESXi 호스트 인증서 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi 호스트 인증서 상태 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 및 ESXi 호스트 인증서 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi 호스트 인증서 검증 실패 상태 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 및 ESXi 호스트 인증서 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| vSphere vCenter 호스트 인증서 관리 모드 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vCenter Server 및 ESXi 호스트 인증서 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| 루트 인증서 상태 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다.  | [vCenter Server 및 ESXi 호스트 인증서 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| GPU ECC 올바르지 않은 메모리 알람 | vCenter Server 인스턴스가 GPU를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| GPU ECC 올바른 메모리 알람 | vCenter Server 인스턴스가 GPU를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| GPU 열 조건 알람 | vCenter Server 인스턴스가 GPU를 지원하지 않으므로 vCenter Server 인스턴스에서 구성되지 않습니다. | 추가 정보 없음 |
| 네트워크 연결 유실 | 중요 이벤트 즉, 네트워크 연결 유실 또는 DVPort에 대한 네트워크 연결 유실이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [네트워킹 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 네트워크 업링크 중복성 유실 | 중요 이벤트 즉, 네트워크 중복성 유실 또는 DVPort에 대한 네트워크 중복성 유실이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다.| [네트워킹 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 네트워크 업링크 중복성 성능 저하 * | 중요 이벤트 즉, 네트워크 중복성 성능 저하 또는 DVPort에 대한 네트워크 중복성 성능 저하가 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [네트워킹 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| VMKernel NIC가 올바르게 구성되지 않음 * | 중요 이벤트 즉, `/Migrate/VMknic`에 지정된 올바르지 않은 `vmknic`가 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [네트워킹 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 스토리지에 연결할 수 없음 * | 중요 이벤트 즉, 스토리지 연결 유실, 스토리지 경로 중복성 유실, 스토리지 경로 중복성 성능 저하 또는 NFS 서버에 대한 연결 유실이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다.| [ESX/ESXi 호스트에서 Fibre Channel, iSCSI 및 NFS 스토리지 문제 식별(1003659)](https://kb.vmware.com/s/article/1003659){:new_window} |
| 마이그레이션 오류 * | 중요 이벤트 즉, VM을 마이그레이션할 수 없음, 마이그레이션 오류, 마이그레이션 호스트 오류, VM 또는 사용되지 않는 VM을 재배치할 수 없음이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [VM의 vMotion 또는 Storage vMotion이 오류와 함께 실패함: 마이그레이션이 100초의 최대 전환 시간을 초과함(2141355)](https://kb.vmware.com/s/article/2141355){:new_window} |
| 대기 종료 오류 | DPM의 사용이 권장되지 않음에 따라 vCenter Server 인스턴스에서 구성되지 않습니다. | VM이 더 적은 호스트에 마이그레이션되고 필요하지 않은 ESX 호스트의 전원이 꺼지므로 리소스 활용도가 낮은 기간 중에 vSphere Distributed Power Management(DPM)는 워크로드를 동적으로 통합하여 온프레미스 배치에서 절전을 제공합니다. IBM Cloud Bare Metal Server의 전원을 꺼서 전력 소비 절감이 실현될 수 없습니다. |

\*는 Stateless 알람을 의미합니다. vCenter는 Stateless 알람에서 데이터를 보존하지 않거나 컴퓨팅하지 않거나 상태를 표시하지 않습니다. Stateless 알람을 수신확인하거나 재설정할 수 없습니다.
{:note}

## 사전 구성된 알람 - vSAN
{: #opsprocs-alarms-preconfigured-vsan}

vSAN 클러스터가 있으면 다음 표에서 추가적으로 사전 구성된 알람이 적용됩니다.

* 알람 이름 - vCenter에 표시되는 알람의 이름입니다.
* 지침 - 이 알람의 사용에 대한 IC4V 지침입니다.
* 자세한 정보 - 트리거된 후 이 알람에 대한 해결을 지원하도록 IBM 또는 VMware에서 추가 정보를 확인할 수 있습니다.

표 2. 사전 구성된 알람 - vSAN

| 알람 이름 | 지침 |자세한 정보 |
|---|---|---|
| 호스트 플래시 용량이 라이센스 부여된 vSAN의 한계를 초과함 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 라이센스가 만료됨 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [라이센싱 문제점 해결](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| vSAN 호스트의 디스크에서 오류가 발생함 | vSAN 디스크에 영구적인 오류가 있는 경우에 이메일을 한 번 발송하도록 구성합니다. | [디바이스가 읽을 수 없거나 쓸 수 없을 때 vSAN 디바이스에 영구적인 오류가 발생함(2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
| vSAN 호스트의 디스크에서 오류가 발생함 | 중요 이벤트 즉, Virtual SAN 디바이스가 영구적인 실패 상태에 있음이 발생하는 경우에 이메일을 한 번 발송하도록 구성합니다. | [디바이스가 읽을 수 없거나 쓸 수 없을 때 vSAN 디바이스에 영구적인 오류가 발생함(2071075)](https://kb.vmware.com/s/article/2071075){:new_window} |
| vSAN 라이센스가 만료됨 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 라이센스에 대한 고려사항](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window} |
| vSAN 시간 제한 라이센스가 만료됨 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 라이센스에 대한 고려사항](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window} |
| vSAN 하드웨어 호환성 문제 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 검사 정보(2114803)](https://kb.vmware.com/s/article/2114803?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} |
| vSAN 상태 알람 `활성 멀티캐스트 연결 확인` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - 활성 멀티캐스트 연결 확인(2116296)](https://kb.vmware.com/s/article/2116296){:new_window} |
| vSAN 상태 알람 `고급 vSAN 구성이 동기화됨` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - 고급 vSAN 구성이 동기화됨(2107713)](https://kb.vmware.com/s/article/2107713){:new_window} |
| vSAN 상태 알람 `한 번의 추가 호스트 실패 후` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 경고 `한 번의 추가 호스트 실패 후`가 올바르지 않게 두 개의 노드 ROBO/확장된 클러스터에 보고됨(2150568)](https://kb.vmware.com/s/article/2150568?lang=en_US){:new_window} |
| vSAN 상태 알람 `모든 호스트 구성 단계` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 성능 서비스 - 모든 호스트 기여 상태 확인(2144400)](https://kb.vmware.com/s/article/2144400){:new_window} |
| vSAN 상태 알람 `모든 호스트에서 vSAN vmknic가 구성됨` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 네트워크 상태 - 모든 호스트에서 vSAN vmknic이 구성됨(2108062)](https://kb.vmware.com/s/article/2108062){:new_window} |
| vSAN 상태 알람 `모든 호스트에서 멀티캐스트 설정이 일치함` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 네트워크 상태  - 모든 호스트에서 멀티캐스트 설정이 일치함(2108092)](https://kb.vmware.com/s/article/2108092){:new_window} |
| vSAN 상태 알람 `모든 호스트에서 서브넷이 일치함` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 네트워크 상태 - 모든 호스트에서 서브넷이 일치함(2108066)](https://kb.vmware.com/s/article/2108066){:new_window} |
| vSAN 상태 알람 `기본(유니캐스트) 연결 확인(일반 Ping)` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 네트워크 상태 - 소형 Ping 테스트 호스트(연결 확인) 및 대형 Ping 테스트 호스트(MTU 검사)(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 상태 알람 `클러스터 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - vSAN 상태 서비스 설치(2109874)](https://kb.vmware.com/s/article/2109874){:new_window} |
| vSAN 상태 알람 `컴포넌트 메타데이터 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [컴포넌트 메타데이터 상태 검사가 올바르지 않은 상태 오류로 실패함(2145347)](https://kb.vmware.com/s/article/2145347){:new_window} |
| vSAN 상태 알람 `혼잡` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다.| [vSAN 상태 서비스 - 실제 디스크 상태 - 혼잡(2109255)](https://kb.vmware.com/s/article/2109255){:new_window} |
| vSAN 상태 알람 `제어기 디스크 그룹 모드가 인증된 VMware임` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN HCL 상태 - vSAN HCL의 SCSI 제어기(2109871)](https://kb.vmware.com/s/article/2109871){:new_window} |
| vSAN 상태 알람 `제어기 드라이버가 인증된 VMware임` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN HCL 상태 - 제어기 드라이버(2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 상태 알람 `제어기 펌웨어가 인증된 VMware임` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [다중 펌웨어 버전이 지원되는 경우 제어기 펌웨어 상태 검사 경고 발생(2150398)](https://kb.vmware.com/s/article/2150398){:new_window} |
| vSAN 상태 알람 `제어기가 ESXi 릴리스에 대해 인증된 VMware임` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN HCL 상태 - 제어기 릴리스 지원(2109262)](https://kb.vmware.com/s/article/2109262){:new_window} |
| vSAN 상태 알람 `CPU AES-NI가 호스트에서 사용 안함으로 설정됨` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 암호화 - CPU AES-NI 호스트 인에이블먼트 확인(2149499)](https://kb.vmware.com/s/article/2149499){:new_window} |
| vSAN 상태 알람 `현재 클러스터 상황` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 한계 상태 - 현재 클러스터 상황(2108740)](https://kb.vmware.com/s/article/2108740){:new_window} |
| vSAN 상태 알람 `고객 환경 향상 프로그램(CEIP)` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 온라인 상태 - CEIP 확인(2148866)](https://kb.vmware.com/s/article/2148866){:new_window} |
| vSAN 상태 알람 `데이터 상태` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 데이터 상태 - vSAN 오브젝트 상태(2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 상태 알람 `디스크 용량` | 경고 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 상태 - 디스크 용량(2108907)](https://kb.vmware.com/s/article/2108907){:new_window} |
| vSAN 상태 알람 `디스크 형식 버전` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 - 디스크 형식 버전(2146135)](https://kb.vmware.com/s/article/2146135){:new_window} |
| vSAN 상태 알람 `ESXi vSAN 상태 서비스 설치` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - 최신 vSAN 상태 서비스(2107705)](https://kb.vmware.com/s/article/2107705){:new_window} |
| vSAN 상태 알람 `홈 오브젝트` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN iSCSI 대상 서비스 - 홈 오브젝트(2147601)](https://kb.vmware.com/s/article/2147601){:new_window} |
| vSAN 상태 알람 `호스트 컴포넌트 한계` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 한계 - 호스트 컴포넌트(2146130)](https://kb.vmware.com/s/article/2146130){:new_window} |
| vSAN 상태 알람 `하드웨어 정보를 검색하는 호스트 문제` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - HCL 상태 - 하드웨어 정보를 검색하는 호스트 문제(2149290)](https://kb.vmware.com/s/article/2149290){:new_window} |
| vSAN 상태 알람 `호스트 유지보수 모드 및 사용 중지 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 호스트 유지보수 모드가 vSAN 노드 사용 중지 상태와 동기화됨(51464)](https://kb.vmware.com/s/article/51464){:new_window}|
| vSAN 상태 알람 `호스트가 VC에서 연결이 끊어짐` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - vCenter Server에서 호스트의 연결이 끊어짐(2108004)](https://kb.vmware.com/s/article/2108004){:new_window} |
| vSAN 상태 알람 `호스트 연결 문제가 있음` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다.  | [vSAN 상태 서비스 - 네트워크 상태 - 연결 문제가 있는 호스트(2108317)](https://kb.vmware.com/s/article/2108317){:new_window} |
| vSAN 상태 알람 `감시 호스트에서 올바르지 않은 선호 결함 도메인` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 감시 호스트에서 올바르지 않은 선호 결함 도메인(2130589)](https://kb.vmware.com/s/article/2130589){:new_window} |
| vSAN 상태 알람 `올바르지 않은 유니캐스트 에이전트` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 한계 - 올바르지 않은 유니캐스트 에이전트 테스트(2144398)](https://kb.vmware.com/s/article/2144398){:new_window} |
| vSAN 상태 알람 `iSCSI 대상 서비스` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN iSCSI 대상 서비스 - 네트워크 구성(2147602)](https://kb.vmware.com/s/article/2147602){:new_window} |
| vSAN 상태 알람 `한계 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `메모리 풀(힙)` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 상태 - 메모리 풀(2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 상태 알람 `메모리 풀(slab)` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 상태 - 메모리 풀(2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 상태 알람 `MTU 확인(패킷 크기가 대형인 Ping)` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - 소형 Ping 테스트 호스트(연결 확인) 및 대형 Ping 테스트 호스트(MTU 검사)(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 상태 알람 `다른 점검을 기반으로 한 멀티캐스트 평가` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 네트워크 상태 - 다른 확인을 기반으로 한 멀티캐스트 평가(2108318)](https://kb.vmware.com/s/article/2108318){:new_window} |
| vSAN 상태 알람 `네트워크 구성` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `네트워크 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `네트워크 대기 시간 확인` | 경고 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - 네트워크 대기 시간 확인(2149511)](https://kb.vmware.com/s/article/2149511){:new_window} |
| vSAN 상태 알람 `감시 호스트에서 청구되는 디스크 없음` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 감시 호스트에서 청구되는 디스크 없음(2130584)](https://kb.vmware.com/s/article/2130584){:new_window} |
| vSAN 상태 알람 `온라인 상태 연결` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 온라인 상태 - 인터넷 연결 확인(2149196)](https://kb.vmware.com/s/article/2149196){:new_window} |
| vSAN 상태 알람 `오퍼레이션 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `성능 데이터 콜렉션` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 테스트가 성능 서비스에서 실패함(2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 상태 알람 `성능 서비스 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 테스트가 성능 서비스에서 실패함(2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 상태 알람 `실제 디스크 컴포넌트 한계 상태` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 - 컴포넌트 한계(2146086)](https://kb.vmware.com/s/article/2146086){:new_window} |
| vSAN 상태 알람 `실제 디스크 상태 검색 문제` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 상태 - 실제 디스크 상태 검사 문제(2149291)](https://kb.vmware.com/s/article/2149291){:new_window} |
| vSAN 상태 알람 `실제 디스크 상태 - 메타데이터 상태` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 실제 디스크 상태 - 메타데이터 상태(2108690)](https://kb.vmware.com/s/article/2108690){:new_window} |
| vSAN 상태 알람 `선호되는 결함 도메인이 설정 해제됨` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 한계 - 선호 결함 도메인이 설정되지 않음(2130590)](https://kb.vmware.com/s/article/2130590){:new_window} |
| vSAN 상태 알람 `재동기화 오퍼레이션 조절` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - 재동기화 오퍼레이션 조절 확인(2149504)](https://kb.vmware.com/s/article/2149504){:new_window} |
| vSAN 상태 알람 `SCSI 제어기가 인증된 VMware임` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN HCL 상태 - 제어기 드라이버(2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 상태 알람 `서비스 런타임 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `사이트 대기 시간 상태` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스- 확장된 클러스터 - 사이트 대기 시간(2146133)](https://kb.vmware.com/s/article/2146133){:new_window} |
| vSAN 상태 알람 `소프트웨어 버전 호환성` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 - 소프트웨어 버전 호환성(2146134)](https://kb.vmware.com/s/article/2146134){:new_window} |
| vSAN 상태 알람 `공간 효율성 구성 일관성` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `공간 효율성 사용 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `상태 DB 오브젝트 충돌` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 성능 서비스 - 상태 DB 오브젝트에서 충돌 확인(2144405)](https://kb.vmware.com/s/article/2144405){:new_window} |
| vSAN 상태 알람 `상태 DB 오브젝트` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 성능 서비스 - 상태 DB 오브젝트 확인(2144403)](https://kb.vmware.com/s/article/2144403){:new_window} |
| vSAN 상태 알람 `상태 마스터 선출` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 성능 서비스 - 상태 마스터 선출 확인(2144408)](https://kb.vmware.com/s/article/2144408){:new_window} |
| vSAN 상태 알람 `확장된 클러스터 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `시간이 호스트 및 VC에서 동기화되지 않음` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - 호스트 및 VC에서의 시간 동기화(2149505)](https://kb.vmware.com/s/article/2149505){:new_window} |
| vSAN 상태 알람 `예기치 않은 결함 도메인 수` | vSAN이 확장된 경우에만 알람을 고려합니다.| [vSAN 상태 서비스 - 예기치 않은 결함 도메인 수(2130581)](https://kb.vmware.com/s/article/2130581){:new_window} |
| vSAN 상태 알람 `유니캐스트 에이전트 구성 불일치` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 한계 - 유니캐스트 에이전트 구성 불일치(2130580)](https://kb.vmware.com/s/article/2130580){:new_window} |
| vSAN 상태 알람 `유니캐스트 에이전트가 구성되지 않음` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 한계 - 유니캐스트 에이전트가 구성되지 않음(2130582)](https://kb.vmware.com/s/article/2130582){:new_window} |
| vSAN 상태 알람 `지원되지 않는 호스트 버전` | vSAN이 확장된 경우에만 알람을 고려합니다. | [VMware KB 문서](https://kb.vmware.com/s/article/2130583){:new_window} |
| vSAN 상태 알람 `vCenter 또는 호스트가 키 관리 서버에 연결되지 않음` | vSAN 암호화가 사용으로 설정된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 한계 - 지원되지 않는 호스트 버전(2130583)](https://kb.vmware.com/s/article/2149497){:new_window} |
| vSAN 상태 알람 `vCenter 상태가 인증됨` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - vCenter 상태가 인증됨(2150916)](https://kb.vmware.com/s/article/2150916){:new_window} |
| vSAN 상태 알람 `상세 모드` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [성능 서비스 - vSAN 상태 서비스의 상세 모드(51527)](https://kb.vmware.com/s/article/51527){:new_window} |
| vSAN 상태 알람 `vSAN 빌드 권장사항 엔진의 빌드 권장사항` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSphere Update Manager - vSAN 빌드 권장사항 엔진 상태(2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 상태 알람 `vSAN 빌드 권장사항 엔진 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSphere Update Manager - vSAN 빌드 권장사항 엔진 상태(2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 상태 알람 `vSAN 빌드 권장사항 엔진 상태` 구성 문제 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSphere Update Manager - vSAN 빌드 권장사항 엔진 상태(2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 상태 알람 `vSAN CLOMD 라이브` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 클러스터 상태 - CLOMD 라이브 확인(2109873)](https://kb.vmware.com/s/article/2109873){:new_window} |
| vSAN 상태 알람 `vSAN 클러스터 구성 일관성` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 클러스터 구성 일관성(2149506)](https://kb.vmware.com/s/article/2149506){:new_window} |
| vSAN 상태 알람 `vSAN 클러스터 파티션` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - vSAN 클러스터 파티션(2108011)](https://kb.vmware.com/s/article/2108011){:new_window} |
| vSAN 상태 알람 `vSAN 디스크 밸런스` | 경고 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 클러스터 상태 - vSAN 디스크 밸런스(2144278)](https://kb.vmware.com/s/article/2144278){:new_window} |
| vSAN 상태 알람 `vSAN HCL DB 자동 업데이트` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 하드웨어 호환성 - vSAN HCL DB 자동 업데이트(2146132)](https://kb.vmware.com/s/article/2146132){:new_window} |
| vSAN 상태 알람 `최신 vSAN HCL DB` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN HCL 상태 - 최신 vSAN HCL DB(2109870)](https://kb.vmware.com/s/article/2109870){:new_window} |
| vSAN 상태 알람 `vSAN HCL 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `최신 vSAN 상태 서비스` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - vSAN 빌드 권장사항 - 최신 vSAN 릴리스 카탈로그(58891)](https://kb.vmware.com/s/article/58891){:new_window} |
| vSAN 상태 알람 `vSAN 오브젝트 상태` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 데이터 상태 - vSAN 오브젝트 상태(2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 상태 알람 `vSAN 성능 서비스 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 성능 서비스 - 상태 확인(2149406)](https://kb.vmware.com/s/article/2149406){:new_window} |
| vSAN 상태 알람 `vSAN VM 상태` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| vSAN 상태 알람 `vSphere 클러스터 멤버가 vSAN 클러스터 멤버와 일치하지 않음` | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | [vSAN 상태 서비스 - 클러스터 상태 - vphere 및 vSAN 클러스터 멤버가 vSAN과 일치함(2149507)](https://kb.vmware.com/s/article/2149507){:new_window} |
| vSAN 상태 알람 `감시 호스트 결함 도메인의 구성이 잘못됨` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 감시 호스트 결함 도메인의 구성이 잘못됨(2130586)](https://kb.vmware.com/s/article/2130586){:new_window} |
| vSAN 상태 알람 `감시 호스트가 없음` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - 감시 호스트가 없음(2130585)](https://kb.vmware.com/s/article/2130585){:new_window} |
| vSAN 상태 알람 `vCenter 클러스터 내의 감시 호스트` | vSAN이 확장된 경우에만 알람을 고려합니다. | [vSAN 상태 서비스 - vCenter 클러스터 내의 감시 호스트(2130587)](https://kb.vmware.com/s/article/2130587){:new_window} |
| vMotion용 vSAN 상태 알람 `기본(유니캐스트) 연결 확인(일반 Ping)` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [VSAN 상태가 연결 오류를 표시함](https://developer.ibm.com/answers/questions/452172/vsan-health-shows-connectivity-errors/){:new_window} |
| vMotion용 vSAN 상태 알람 `MTU 확인(패킷 크기가 대형인 Ping)` | 중요 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. | [vSAN 상태 서비스 - 네트워크 상태 - 소형 Ping 테스트 호스트(연결 확인) 및 대형 Ping 테스트 호스트(MTU 검사)(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| VSAN 상태 서비스 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |
| 전체 상태 요약을 위한 vSAN 상태 서비스 알람 | 알림에 대한 필수 항목으로 간주되지 않습니다. 알람은 일일 사전 예방적 점검의 일부로 검토되었습니다. | 추가 정보 없음 |


## 사전 구성된 알람 - 하이브리디티 번들
{: #opsprocs-alarms-preconfigured-hcx}

하이브리디티 번들로 HCX가 설치되고 이를 통해 다음 추가 사전 구성된 알람이 작성됩니다.

표 3. 사전 구성된 알람 - HCX

| 알람 이름 | 지침 |자세한 정보 |
|---|---|---|
| 대량 마이그레이션 실패 | 마이그레이션이 관리되므로 알림에 대한 필수 항목으로 간주되지 않습니다. | [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) 및 [VMware HCX 문제점 해결](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}을 참조하십시오. |
| 콜드 마이그레이션 실패 | 마이그레이션이 관리되므로 알림에 대한 필수 항목으로 간주되지 않습니다. | [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) 및 [VMware HCX 문제점 해결](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}을 참조하십시오. |
| HCX 클라우드 데이터베이스 업그레이드 실패 | 업그레이드가 관리되므로 알림에 대한 필수 항목으로 간주되지 않습니다. | [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) 및 [VMware HCX 문제점 해결](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}을 참조하십시오. |
| HCX 엔터프라이즈 데이터베이스 업그레이드 실패 | 업그레이드가 관리되므로 알림에 대한 필수 항목으로 간주되지 않습니다. | [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) 및 [VMware HCX 문제점 해결](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}을 참조하십시오. |
| HCX 상호연결 터널 상태 | 중요 터널 상태가 작동 중지인 이벤트에 대해 이메일을 한 번 발송하도록 구성합니다. |[네트워크(WAN) 연결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting#hcxclient-troubleshooting-wan-connect)을 참조하십시오. |

## 이벤트 및 알람 프로시저
{: #opsprocs-alarms-procedures}

다음 표에서는 이벤트 및 알람에 대한 다수의 프로시저에 대해 설명합니다.

표 4. 이벤트 및 알람 프로시저

|제목 |설명 |
|---|---|
| 이벤트 보기  | 이벤트를 보려면 vCenter로 이동하고 인벤토리 오브젝트를 선택하십시오. **모니터** 탭, **태스크 및 이벤트** 및 **이벤트**를 클릭하십시오. 이벤트를 선택하여 세부사항을 확인하십시오. 필터를 사용하고 열 표제를 선택하여 목록을 정렬할 수 있습니다. |
| 이벤트 내보내기  | 이벤트를 내보내서 MS Excel에서 지원할 도구를 사용할 수 있습니다. 필요한 인벤토리 오브젝트를 선택하십시오. **모니터** 탭, **이벤트** 및 **내보내기** 아이콘을 클릭하십시오. **이벤트 내보내기** 창에서 내보낼 이벤트 유형을 지정하십시오. **CSV 보고서 생성**을 선택하고 **저장**을 클릭하십시오. 파일 이름 및 위치를 지정하고 파일을 저장하십시오. |
| 이벤트 보유  | 기본적으로 이벤트 보유는 30일로 설정됩니다. VMware vSphere Web Client에서 이 설정을 변경해야 합니다. **구성** 탭, **설정** 및 **일반**을 클릭하십시오. **편집**을 클릭하고 이벤트 보유를 필요한 기간(일)으로 변경한 후 **확인**을 클릭하십시오. |
| 트리거된 알람 보기  | 트리거된 알람을 보려면 vCenter로 이동하고 **알람** 분할창에서 **모두** 또는 **새로 작성**을 선택하십시오. 이 목록은 120초마다 새로 고쳐집니다. 선택한 인벤토리 오브젝트에서 트리거된 알람을 보려면 오브젝트를 선택하십시오. **모니터** 탭, **발행**을 클릭하고 **트리거된 알람**을 선택하십시오. |

## 관련 링크
{: #opsprocs-alarms-links}

* [vSphere 모니터링 및 성능](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-monitoring-performance-guide.pdf){:new_window}

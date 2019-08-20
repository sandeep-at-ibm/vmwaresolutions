---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker 이벤트
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션이 {{site.data.keyword.cloud_notm}}에서 {{site.data.keyword.vmwaresolutions_short}}와 상호작용하는 방법을 추적하십시오.

{{site.data.keyword.at_full_notm}}는 {{site.data.keyword.cloud_notm}}에서 서비스의 상태를 변경하는 사용자 시작 활동을 기록합니다. 이 서비스를 사용하여 비정상 활동 및 위험 조치를 조사하고 규정 감사 요구사항을 준수할 수 있습니다. 또한 발생 시 조치에 대한 경보를 받을 수 있습니다. 수집되는 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 준수합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)를 참조하십시오.

## 인스턴스 관리 이벤트 추적
{: #at-events-instance-mgmt}

{{site.data.keyword.vmwaresolutions_short}}에서 사용자 계정, 인스턴스, 클러스터 및 서비스를 관리하는 경우 이벤트가 생성되고 서비스가 프로비저닝된 위치에 있는 서비스의 인스턴스 또는 글로벌 도메인에 전송됩니다. 자세한 정보는 [글로벌 및 위치 기반 이벤트 모니터링](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)을 참조하십시오.

다음 표에는 관리 이벤트를 생성하고 Activity Tracker로 전송하는 조치가 제공됩니다.

| 조치                                   |설명 |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` |계정의 인프라 API 키가 업데이트됩니다. |
| `vmware-solutions.account-notification.update` | 계정의 알림 설정이 업데이트됩니다. |
| `vmware-solutions.instance-secure-data.wipe` | 인스턴스 보안 데이터가 삭제됩니다. |
| `vmware-solutions.instance-bss-account.migrate` |	인스턴스가 BSS 계정으로 마이그레이션됩니다. |
| `vmware-solutions.vcs.create` |vCenter Server 인스턴스가 작성됩니다. |
| `vmware-solutions.vcs.delete` |vCenter Server 인스턴스가 삭제됩니다. |
| `vmware-solutions.vcs-host.add` |호스트가 vCenter Server 인스턴스에 추가됩니다. |
| `vmware-solutions.vcs-host.remove` |호스트가 vCenter Server 인스턴스에서 제거됩니다. |
| `vmware-solutions.vcs.update` |vCenter Server 인스턴스가 업데이트됩니다. |
| `vmware-solutions.vcs-cluster.create` |클러스터가 vCenter Server 인스턴스에 대해 작성됩니다. |
| `vmware-solutions.vcs-cluster.delete` |클러스터가 vCenter Server 인스턴스에 대해 삭제됩니다. |
| `vmware-solutions.vcs-nsx-license.update` |NSX 라이센스가 vCenter 서버 인스턴스에 대해 업데이트됩니다. |
| `vmware-solutions.vcs-nfs-storage.add` |NFS 스토리지가 vCenter Server 인스턴스에 추가됩니다. |
| `vmware-solutions.vcs-nfs-storage.remove` |NFS 스토리지가 vCenter Server 인스턴스에서 제거됩니다. |
| `vmware-solutions.vcs-plan.update` |vCenter Server 인스턴스의 플랜이 업데이트됩니다. |
| `vmware-solutions.vss.create` |vSphere 인스턴스가 작성됩니다. |
| `vmware-solutions.vss.update` |vSphere 인스턴스가 업데이트됩니다. |
| `vmware-solutions.vss-template.remove` |vSphere 템플리트가 제거됩니다. |
| `vmware-solutions.service.create` |서비스가 작성됩니다. |
| `vmware-solutions.service.delete` |서비스가 삭제됩니다. |
{: caption="표 1. 관리 이벤트를 생성하는 조치에 대한 설명" caption-side="top"}

## KMIP for VMware on IBM Cloud 서비스에 대한 이벤트 추적
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 키를 관리하는 경우 이벤트가 생성되고 서비스가 프로비저닝된 위치에 있는 서비스의 인스턴스 또는 글로벌 도메인에 전송됩니다. 자세한 정보는 [글로벌 및 위치 기반 이벤트 모니터링](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)을 참조하십시오.

다음 표에는 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하고 전송하는 조치가 제공됩니다.

| 조치                                      |설명                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` |KMIP 키가 작성됩니다. |
| `vmware-solutions.kmip-key.retrieve` |KMIP 키가 검색됩니다. |
| `vmware-solutions.kmip-key-attributes.retrieve` |KMIP 키의 속성이 검색됩니다. |
| `vmware-solutions.kmip-key.activate` |KMIP 키가 활성화됩니다. |
| `vmware-solutions.kmip-key.revoke` |KMIP 키가 취소됩니다. |
| `vmware-solutions.kmip-key.destroy` |KMIP 키가 영구 삭제됩니다. |
{: caption="표 2. KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하는 조치에 대한 설명" caption-side="top"}

## 이벤트 표시 위치
{: #at-events-viewing}

이벤트는 **프랑크푸르트** 위치에서 사용 가능합니다.

위치당 하나의 {{site.data.keyword.at_full_notm}} 인스턴스만 있습니다. 이벤트를 보려면 **EU-DE** 위치에 있는 {{site.data.keyword.at_full_notm}} 서비스의 웹 UI에 액세스해야 합니다. 자세한 정보는 [IBM Cloud UI를 통해 웹 UI 실행](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2)을 참조하십시오.

## 관련 링크
{: #at-events-related}

* [인스턴스 프로비저닝](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [웹 UI로 이동](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

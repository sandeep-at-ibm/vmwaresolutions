---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-17"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker 이벤트
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션이 {{site.data.keyword.cloud_notm}}에서 {{site.data.keyword.vmwaresolutions_short}}와 상호작용하는 방법을 추적하십시오.

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.cloud_notm}}에서 서비스 상태가 변경된 사용자 시작 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 정보](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)를 참조하십시오.

## Activity Tracker 이벤트 테이블
{: #at-events-table}

활동 트래커 이벤트 테이블의 열에 대한 설명을 보려면 다음 표를 확인하십시오.

표 1. 활동 트래커 이벤트 테이블에 대한 설명

|열                |값 유형 |설명 |
|:----------------------|:-----------|:------------|
| Time                  |해당사항 없음        | 이벤트가 작성된 날짜 및 시간입니다. |
| initiator.name        | 문자열     | 조치를 시작한 사용자의 IBM ID입니다. |
| target_name           | 문자열     | 조치가 실행되는 리소스입니다. |
| target.typeURI        | 문자열     | 조치가 실행되는 대상의 UUID(Universally Unique Identifier)입니다. |
| action                | 문자열     | 이벤트를 트리거하는 조치입니다. 올바른 값은 `create`, `update` 및 `delete`입니다. |
| outcome               | 문자열     | 조치의 결과입니다. 값은 `success`, `failure` 또는 `pending`입니다. |
| reason_reasonCode     | 정수    | 결과의 이유 코드입니다. |
| initiator_host_address| 문자열     | 요청이 발생하는 IP 주소입니다. |

자세한 정보는 [활동 트래커 이벤트 필드](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event)를 참조하십시오.

## 인스턴스 관리 이벤트 추적
{: #at-events-instance-mgmt}

{{site.data.keyword.vmwaresolutions_short}}에서 사용자 계정, 인스턴스, 클러스터 및 서비스를 관리하는 경우 활동 트래커에서 이벤트가 생성되고 **계정 도메인**에 전송됩니다.

관리 이벤트를 생성하고 활동 트래커로 전송하는 조치를 보려면 다음 표를 확인하십시오.

표 2. 관리 이벤트를 생성하는 조치에 대한 설명

| 조치                                   |설명 | 결과 |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |	계정의 인프라 API 키가 업데이트됩니다.|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | 계정의 알림 설정이 업데이트됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | 인스턴스 보안 데이터가 삭제됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	인스턴스가 BSS 계정으로 마이그레이션됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |	vCenter Server 인스턴스가 작성됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` |	vCenter Server 인스턴스가 삭제됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |	호스트가 vCenter Server 인스턴스에 추가됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |	호스트가 vCenter Server 인스턴스에서 제거됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	|vCenter Server 인스턴스가 업데이트됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	|클러스터가 vCenter Server 인스턴스에 대해 작성됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	|클러스터가 vCenter Server 인스턴스에 대해 삭제됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	|NSX 라이센스가 vCenter 서버 인스턴스에 대해 업데이트됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	|하이브리디티 번들이 vCenter 서버 인스턴스에 대해 업그레이드됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	|하이브리디티 번들이 vCenter 서버 인스턴스에서 제거됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	|NFS 스토리지가 vCenter Server 인스턴스에 추가됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	|NFS 스토리지가 vCenter Server 인스턴스에서 제거됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	|vCenter Server 인스턴스의 플랜이 업데이트됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	|vSphere 인스턴스가 작성됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	|vSphere 인스턴스가 업데이트됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |	vSphere 템플리트가 제거됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	|서비스가 작성됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	|서비스가 삭제됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` |하이브리디티 번들이 `version`으로 업그레이드됩니다. |`pending`<br>`success`<br>`failure` |

## KMIP for VMware on IBM Cloud 서비스에 대한 이벤트 추적
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 키를 관리하는 경우 활동 트래커에서 이벤트가 생성되고 **계정 도메인**에 전송됩니다.

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하고 전송하는 조치를 보려면 다음 표를 확인하십시오.

표 3. KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하는 조치에 대한 설명

| 조치                                      |설명                               | 결과 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |	KMIP 키가 작성됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |	KMIP 키가 검색됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |	KMIP 키의 속성이 검색됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |	KMIP 키가 활성화됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |	KMIP 키가 취소됩니다. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |	KMIP 키가 영구 삭제됩니다. |`pending`<br>`success`<br>`failure` |

## 이벤트 표시 위치
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 **계정 도메인** 이벤트가 생성된 {{site.data.keyword.cloud_notm}} 지역에서 사용할 수 있는 {{site.data.keyword.cloudaccesstrailshort}}에서 사용 가능합니다.

## 관련 링크
{: #at-events-related}

* [활동 트래커 프로비저닝](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [{{site.data.keyword.cloud_notm}} 콘솔에서 Activity Tracker 대시보드로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

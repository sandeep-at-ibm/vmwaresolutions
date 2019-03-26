---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-12"

---

# Activity Tracker 이벤트
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션이 {{site.data.keyword.Bluemix_notm}}에서 {{site.data.keyword.vmwaresolutions_short}}와 상호작용하는 방법을 추적하십시오.

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.Bluemix_notm}}에서 서비스 상태가 변경된 사용자 시작 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)의 내용을 참조하십시오.

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
| `vmware-solutions.user_account.update`    | <ul><li>사용자 계정 업데이트 요청을 수신합니다.</li><li>사용자 계정 업데이트 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>알림 업데이트 요청을 수신합니다.</li><li>알림 업데이트 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>보안 데이터 삭제 요청을 수신합니다.</li><li>보안 데이터 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>bss 계정 마이그레이션 요청을 수신합니다.</li><li>bss 계정 마이그레이션 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>Cloud Foundation 인스턴스 삭제 요청을 수신합니다.</li><li>Cloud Foundation 인스턴스 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>Cloud Foundation 인스턴스에 ESXi 서버 추가 요청을 수신합니다.</li><li>Cloud Foundation 인스턴스에 ESXi 서버 추가 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>Cloud Foundation 인스턴스에 ESXi 서버 삭제 요청을 수신합니다.</li><li>Cloud Foundation 인스턴스에 ESXi 서버 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>Cloud Foundation 인스턴스에 대한 클러스터 작성 요청을 수신합니다.</li> <li>Cloud Foundation 인스턴스에 대한 클러스터 작성 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>Cloud Foundation 인스턴스에서 클러스터 삭제 요청을 수신합니다.</li><li>Cloud Foundation 인스턴스에서 클러스터 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>Cloud Foundation 인스턴스에 대한 업데이트 스케줄 요청을 수신합니다.</li><li>Cloud Foundation 인스턴스에 대한 업데이트 스케줄 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>vCenter Server 인스턴스 주문 요청을 수신합니다.</li><li>vCenter Server 인스턴스 주문 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>vCenter Server 인스턴스 삭제 요청을 수신합니다.</li><li>vCenter Server 인스턴스 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>vCenter Server 인스턴스에 ESXi 서버 추가 요청을 수신합니다.</li><li>vCenter Server 인스턴스에 ESXi 서버 추가 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>vCenter Server 인스턴스에서 ESXi 서버 삭제 요청을 수신합니다.</li><li>vCenter Server 인스턴스에서 ESXi 서버 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>vCenter Server 인스턴스에 대한 업데이트 스케줄 요청을 수신합니다.</li><li>vCenter Server 인스턴스에 대한 업데이트 스케줄 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>vCenter Server 인스턴스에 대한 클러스터 작성 요청을 수신합니다.</li><li>vCenter Server 인스턴스에 대한 클러스터 작성 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>vCenter Server 인스턴스에서 클러스터 삭제 요청을 수신합니다.</li> <li>vCenter Server 인스턴스에서 클러스터 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>VMware NSX 라이센스 업데이트 요청을 수신합니다.</li><li>VMware NSX 라이센스 업데이트 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드 요청을 수신합니다.</li><li>vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>vSphere cluster 클러스터 주문 요청을 수신합니다.</li><li>vSphere cluster 클러스터 주문 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>vSphere cluster 클러스터 업데이트 요청을 수신합니다.</li><li>vSphere cluster 클러스터 업데이트 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>vSphere 클러스터의 구성 요청을 수신합니다.</li><li>vSphere 클러스터의 구성 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>NetApp ONTAP Select 인스턴스 주문 요청을 수신합니다.</li><li>NetApp ONTAP Select 인스턴스 주문 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>NetApp ONTAP Select 인스턴스 삭제 요청을 수신합니다.</li><li>NetApp ONTAP Select 인스턴스 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>서비스의 구성 업데이트 요청을 수신합니다.</li><li>서비스의 구성 업데이트 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>인스턴스의 서비스 주문 요청을 수신합니다.</li><li>인스턴스의 서비스 주문 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>인스턴스에서 서비스 삭제 요청을 수신합니다.</li><li>인스턴스에서 서비스 삭제 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>기존 vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드 요청을 수신합니다.</li><li>기존 vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.service.deploy` | 인스턴스에 서비스를 배치하는 조치가 실행됩니다. | `success` |
| `vmware-solutions.service.undeploy` | 인스턴스에 서비스를 제거하는 조치가 실행됩니다. | `success` |

## KMIP for VMware on IBM Cloud 서비스에 대한 이벤트 추적
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 키를 관리하는 경우 활동 트래커에서 이벤트가 생성되고 **계정 도메인**에 전송됩니다.

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하고 전송하는 조치를 보려면 다음 표를 확인하십시오.

표 3. KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대한 이벤트를 생성하는 조치에 대한 설명

| 조치                                      |설명                               | 결과 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>키 작성 요청을 수신합니다.</li><li>키 작성 요청에 응답합니다.</li></ul> | <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>키의 컨텐츠 가져오기 요청을 수신합니다.</li><li>키의 컨텐츠 가져오기 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>키의 속성 가져오기 요청을 수신합니다.</li><li>키의 속성 가져오기 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>키 활성화 요청을 수신합니다.</li><li>키 활성화 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>키 취소 요청을 수신합니다.</li><li>키 취소 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>키 영구 삭제 요청을 수신합니다.</li><li>키 영구 삭제 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스의 버전 찾기 요청을 수신합니다.</li><li>KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스의 버전 찾기 요청에 응답합니다.</li></ul> |  <ul><li>`pending`</li><li>`success` 또는 `failure`</li></ul> |

## 이벤트 표시 위치
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 **계정 도메인** 이벤트가 생성된 {{site.data.keyword.Bluemix_notm}} 지역에서 사용할 수 있는 {{site.data.keyword.cloudaccesstrailshort}}에서 사용 가능합니다.

## 관련 링크
{: #at-events-related}

* [활동 트래커 프로비저닝](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [{{site.data.keyword.cloud_notm}} 콘솔에서 Activity Tracker 대시보드로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

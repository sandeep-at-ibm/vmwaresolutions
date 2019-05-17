---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 연결된 스토리지에 대한 구성 및 설정
{: #storage-settings}

이 디자인은 NFS v3을 통해서만 공유 스토리지 연결을 지원합니다. NFS v4 및 v4.1은 지원되지 않습니다.

이 디자인용으로 연결된 스토리지는 vCenter Server 솔루션과 동일한 {{site.data.keyword.CloudDataCent_notm}}에서 사용 가능한 {{site.data.keyword.cloud_notm}} 스토리지로 제한됩니다. 또한 데이터 저장소에 저장된 모든 가상 디스크는 기본적으로 씬 프로비저닝됩니다.
{:note}

아키텍처는 공유에 연결하기 위해 {{site.data.keyword.cloud_notm}} 스토리지의 DNS 이름을 사용하여 NFS v3 데이터 저장소가 연결됨을 지정합니다. NFS 공유는 vCenter Server 클러스터의 모든 호스트에 연결되며 Storage DRS가 사용되는 데이터 저장소 클러스터에 위치합니다.

## vSphere Storage DRS(Distributed Resource Scheduler)
{: #storage-settings-vsphere-storage-drs}

Storage DRS를 사용하여 데이터 저장소 클러스터의 집계된 리소스를 관리할 수 있습니다. Storage DRS가 사용되는 경우 데이터 저장소 클러스터의 데이터 저장소에서 영역 및 I/O 리소스를 밸런싱하기 위해 가상 머신(VM) 디스크 배치 및 마이그레이션에 대한 권장사항을 제공합니다.

Storage DRS를 켜면 다음 기능을 사용할 수 있습니다.
* 데이터 저장소 클러스터 내 데이터 저장소 간 영역 로드 밸런싱
* 데이터 저장소 클러스터 내 데이터 저장소 간 I/O 로드 밸런싱
* 영역 및 I/O 워크로드에 따른 가상 디스크의 초기 배치.

이 디자인에서 Storage DRS는 자동화 레벨이 **완전히 자동화됨**으로 설정된 상태로 사용됩니다. 결과적으로 데이터 클러스터에서 리소스 사용을 최적화하기 위해 파일이 자동으로 마이그레이션됩니다. 클러스터가 완전히 자동화되어 있으므로 다른 모든 Storage DRS 옵션은 **클러스터 설정 사용**으로 설정됩니다.

## NFS v3에 대한 Storage DRS 런타임 설정
{: #storage-settings-drs-nfs3}

Storage DRS의 적극성은 I/O 대기 시간 및 사용되는 영역의 임계값을 지정하여 판별됩니다. Storage DRS는 데이터 저장소 클러스터에서 데이터 저장소에 대한 리소스 사용 정보를 수집합니다. vCenter Server는 이 정보를 사용하여 데이터 저장소에 가상 디스크 배치를 위한 권장사항을 생성합니다.

낮은 적극성 레벨이 데이터 저장소 클러스터에 설정되면 Storage DRS는 필요한 경우에만 Storage vMotion 마이그레이션을 권장합니다. 예를 들어 I/O 로드, 영역 사용량 또는 불균형이 높은 경우 Storage DRS는 마이그레이션을 권장합니다. 높은 적극성 레벨이 데이터 저장소 클러스터에 설정된 경우에는 Storage DRS는 데이터 저장소 클러스터에 영역 또는 I/O 로드 밸런싱을 통한 이점이 있을 때마다 마이그레이션을 권장합니다.

다음 임계값 카테고리는 데이터 저장소 클러스터에서 사용 가능합니다.

* 영역 활용: Storage DRS는 데이터 저장소의 영역 활용 백분율이 vSphere Web Client에서 설정한 임계값보다 클 때 권장사항을 생성하거나 마이그레이션을 수행합니다.
* I/O 대기 시간: Storage DRS는 데이터 저장소에 대해 하루 동안 측정된 90번째 백분위수 I/O 대기 시간이 임계값보다 클 때 권장사항을 생성하거나 마이그레이션을 수행합니다.

이 디자인에서 Storage DRS 런타임 설정이 사용되며 임계값은 각 기본값으로 유지됩니다. 워크로드 I/O 요구사항 및 대기 시간 감도에 따라 이러한 값을 변경하십시오.

다음 표에는 VMware vSphere Web Client의 설정이 표시됩니다.

표 1. Storage DRS 런타임 설정

|설정       |값  |
|:--------------- |:------ |
| SDRS 권장사항에 대한 I/O 메트릭 사용 | 선택됨 |
| 활용 영역 | 선택됨, 80%로 설정됨 |
| I/O 대기 시간 임계값 | 15ms |

vSphere Web Client에서 이러한 설정을 구성하는 데 대한 자세한 정보는 [vSphere Web Client에서 Storage DRS 런타임 규칙 설정](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html)을 참조하십시오.

## NFS v3에 대한 Storage I/O 제어
{: #storage-settings-io-control-nfs-v3}

SIOC((Storage I/O Control)가 환경에서 사용으로 설정되어 있는 경우, 단일 VM에 대한 디바이스 큐 길이를 변경합니다. 디바이스 큐 길이를 변경하면 모든 VM에 대한 스토리지 배열 큐가 스토리지 큐의 같은 공유 및 조절로 줄어듭니다. SIOC는 리소스가 제한되고 스토리지 I/O 대기 시간이 정의된 임계값보다 높은 경우에만 사용됩니다.

SIOC가 스토리지 디바이스가 혼잡하거나 제한된 경우를 판별하려면 정의된 임계값이 필요합니다. 여러 스토리지 유형에 대한 혼잡 임계값 대기 시간은 서로 다릅니다. 이 디자인은 임계값 대기 시간인 10밀리초를 권장하며 구현합니다.

개별 VM에 대한 개별 가상 디스크를 제한하거나 SIOC와의 여러 공유를 허용할 수 있습니다. 디스크 수를 제한하고 여러 공유를 허용하면 획득한 파일 스토리지 볼륨 IOPS 수의 워크로드로 환경을 일치시키고 조절할 수 있습니다. 한계는 IOPS로 설정되며 다른 가중치 또는 공유를 설정할 수 있습니다.

**높음**(2,000개 공유)으로 설정된 가상 디스크 공유는 I/O에 대해 **보통**(1,000개 공유)으로 설정된 디스크의 두 배를 수신하고 **낮음**(500개 공유)으로 설정된 디스크의 4배를 수신합니다. **보통**은 모든 VM의 기본값이므로 필요한 VM에 대한 **보통** 설정을 조정해야 합니다.

## NFS v3에 대한 추가 스토리지
{: #storage-settings-additional-storage-nfs-v3}

부족한 영역 또는 많은 대기 시간으로 인해 환경에 스토리지를 추가해야 하는 경우 콘솔에서 다른 NFS 공유를 주문할 수 있습니다. 공유를 주문한 후에는 내보내기를 클러스터의 vSphere ESXi 호스트에 연결하고 스토리지 클러스터에 배치하십시오. 스토리지 클러스터에 효율적이고 원활하게 새 NFS 공유를 배치하면 스토리지 레벨 마이그레이션 없이도 환경과 연관된 스토리지를 스케일 확장할 수 있습니다.

## 고급 구성 매개변수
{: #storage-settings-adv-config-param}

이 디자인은 {{site.data.keyword.cloud_notm}}에서 권장하는 고급 구성 매개변수를 추가합니다. 따라서 {{site.data.keyword.cloud_notm}} NFS 공유에 연결된 각 vSphere ESXi 호스트에 다음 매개변수가 설정됩니다.

표 2. NFS 고급 구성 매개변수

|매개변수       |값  |
|:--------------- |:------ |
| Net.TcpipHeapSize |32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures |10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout |5 |
| NFS.MaxQueueDepth | 64 |

## 관련 링크
{: #storage-settings-related}

* [솔루션 개요](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 명세서
{: #vc_bom}

VMware vCenter Server 인스턴스에 대한 BOM(Bill of Materials) 정보를 검토하십시오.

## vCenter Server 인스턴스에 대한 VLAN BOM
{: #vc_bom-vlans}

다음 표에는 vCenter Server VLAN에 대한 BOM 정보의 세부사항이 있습니다.

표 1. vCenter Server 인스턴스의 VLAN에 대한 BOM

|VLAN       |유형       |세부사항       |
|:---------- |:---------- |:------------- |
|VLAN1     |공인, 기본 |공용 네트워크 액세스를 위한 실제 ESXi 서버에 지정됩니다. 초기 배치 후에 사용되지 않습니다. 인터넷 액세스에 사용 가능합니다. |
|VLAN2     |사설 A, 기본 |{{site.data.keyword.cloud}}에 의해 실제 ESXi 서버에 지정됩니다. VMware vSphere 관리 트래픽에 대한 관리 인터페이스에서 사용됩니다.<br><br>관리 컴포넌트로 작동하는 가상 머신(VM)에 지정됩니다.<br><br>VMware NSX VTEP(VXLAN Tunnel Endpoint)에 지정됩니다. |
|VLAN3     |사설 B, 포터블 |VMware vSAN에 지정됩니다(사용된 경우).<br><br>VMware NFS에 지정됩니다(사용된 경우).<br><br>VMware vSphere vMotion에 지정됩니다. |

## vCenter Server 인스턴스에 대한 소프트웨어 BOM
{: #vc_bom-software}

다음 표에는 vCenter Server 소프트웨어 컴포넌트에 대한 BOM 정보의 세부사항이 있습니다.

표 2. vCenter Server 인스턴스의 소프트웨어 컴포넌트에 대한 BOM

|제조업체  |컴포넌트                      |버전       |
|:------------- |:------------------------------ |:------------- |
|VMware       |vSphere ESXi                    | 6.5 Update P3(6.5.0-10884925 빌드) |
|VMware       |vCenter Server Appliance        | 6.5 U2d(6.5.0-10964411 빌드) |
|VMware       |Platform Services Controller    | 6.5 U2d(6.5.0-10964411 빌드) |
|VMware       |vSAN                            |6.6.1        |
|VMware       |NSX for vSphere                 | 6.4.1        |
|Microsoft    |Windows Server Standard 에디션 |2012R2       |

VMware vSAN은 선택적 컴포넌트입니다.
{:note}

## ESXi 서버의 고급 구성 설정
{: #vc_bom-esxi-server-advance-config}

ESXi 서버에 적용되는 고급 구성 설정의 개요에 대해서는 아래 표를 검토하십시오. 이러한 설정은 vCenter Server 인스턴스가 V2.2 이상에 배치되는지 또는 V2.1 이하에서 V2.2 이상으로 업그레이드되는지에 따라 달라집니다.

이 설정은 새 인스턴스 V2.2 이상에서 새 인스턴스 및 새 클러스터에 적용됩니다. 이 설정은 V2.1 이하의 기존 인스턴스 또는 V2.2 이상으로 업그레이드된 기존 인스턴스의 새 클러스터에 적용되지 않습니다.

표 3. vCenter Server 인스턴스 및 클러스터에 대한 ESXi 서버 고급 구성 설정

|구성 설정 |V2.2 이상에 새로 배치된 경우  |V2.1 이전에서 업그레이드된 경우 |
|:------------- |:------------- |:------------- |
|최대 볼륨 |**MaxVolumes** = 256 |두 **/NFS/MaxVolumes** 및 **/NFS41/MaxVolumes** = 256 |
|하트비트 최대 실패 |**HeartbeatMaxFailures** = 10 |설정되지 않음 |
|하트비트 빈도 |**HeartbeatFrequency** = 12 |설정되지 않음 |
|하트비트 제한시간 |**HeartbeatTimeout** = 5 |설정되지 않음 |
|최대 큐 길이 |**MaxQueueDepth** = 64 |설정되지 않음 |
|큐 전체 샘플 크기 |**QFullSampleSize** = 32 |**/Disk/QFullSampleSize** = 32 |
|큐 전체 임계값 |**QFullThreshold** = 8 |**/Disk/QFullThreshold** = 8 |
|TCP/IP 힙 크기 |**TcpipHeapSize** = 32 |설정되지 않음 |
|최대 TCP/IP 힙 |**TcpipHeapMax** = 1536 |설정되지 않음 |

**참고:**
* 서비스가 ESXi 서버에서 기본 NFS 마운트 수보다 더 많은 NFS 마운트를 사용할 수 있으므로 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스에 **MaxVolumes** 설정이 필요합니다.
* 구성 설정에 대한 **설정되지 않음** 값은 새 설정이 자동으로 적용되지 않음을 나타내며, ESXi 서버를 다시 부팅해야 하므로 중단이 발생할 수 있습니다.

  모든 인스턴스의 일관성과 스토리지 확장에 필요한 충분한 지원을 허용하기 위해 **설정되지 않음** 구성 설정을 새 값으로 변경하는 것이 좋습니다. IBM은 모든 {{site.data.keyword.vmwaresolutions_short}} V2.2 이상 릴리스의 새 설정에 대해서만 테스트하도록 계획하고 있습니다.

  자세한 정보는 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi host](https://kb.vmware.com/s/article/2239)를 참조하십시오.

## NSX 및 포트 그룹 구성 설정
{: #vc_bom-nsx-port-group-config}

다음 표에서 vCenter Server 인스턴스에 대한 VMware NSX 및 포트 그룹 구성 설정의 개요와 릴리스 간의 차이점을 검토하십시오.

이 설정은 새 인스턴스 V2.2 이상에서 새 인스턴스 및 새 클러스터에 적용됩니다. 이 설정은 V2.1 이하의 기존 인스턴스 또는 V2.2 이상으로 업그레이드된 기존 인스턴스의 새 클러스터에 적용되지 않습니다.

표 4. vCenter Server 인스턴스에 대한 NSX 및 포트 그룹 구성 설정

|구성 설정 |V2.1 이전  |V2.2 이상 |   
|:------------- |:------------- |:------------- |
|NSX VXLAN 클러스터 팀 정책 |장애 복구 |로드 밸런스 - SRCID |
|NSX VXLAN 클러스터 VTEP |1 |2 |
|기본 인스턴스를 위한 세그먼트 ID 풀 |6000 - 8000 |6000 - 7999 |  
|후속 보조 인스턴스를 위한 세그먼트 ID 풀 |6000 - 8000 |다중 사이트 구성의 이전 종료 범위 + 1에서 다중 사이트 구성의 이전 종료 범위 + 2000 |  
|포트 그룹 SDDC-DPortGroup-VSAN(적용 가능한 경우) |**활성 업링크**가 **uplink1**로 설정되고 **대기 업링크**가 **uplink2**로 설정됨 |**활성 업링크**가 **uplink2**로 설정되고 **대기 업링크**가 **uplink1**로 설정됨 |  
|포트 그룹 SDDC-DPortGroup-Mgmt |**포트 바인딩**이 **Ephemeral - 바인딩 없음**으로 설정되고 **로드 밸런싱**이 **원래 가상 포트를 기반으로 한 라우트**로 설정됨 |**포트 바인딩**이 **정적 바인딩**으로 설정되고 **로드 밸런싱**이 **실제 NIC 로드를 기반으로 한 라우트**로 설정됨 |  
|포트 그룹 SDDC-DPortGroup-External |**포트 바인딩**이 **Ephemeral - 바인딩 없음**으로 설정됨 |**포트 바인딩**이 **정적 바인딩**으로 설정됨 |

## 네트워크 MTU 구성 설정
{: #vc_bom-network-mtu-config}

vSphere 클러스터는 두 개의 vDS(vSphere Distributed Switch)를 사용합니다(하나는 공용 네트워크 연결용이고 다른 하나는 사설 네트워크 연결용).

사설 네트워크 연결은 크기가 9000인 점보 프레임 최대 전송 단위(MTU)를 사용하도록 구성되며, 이는 저장 작업 및 VMware vMotion 등에서 발생하는 대규모 데이터 전송의 성능을 향상시킵니다. 이 값은 VMware 내에서 및 {{site.data.keyword.cloud_notm}}에 의해 허용되는 최대 MTU입니다.

V2.1 이상에서 공용 네트워크 연결은 크기가 1500인 표준 이더넷 MTU를 사용합니다. 이 1500 설정은 유지해야 하며, 변경되면 인터넷 패킷의 단편화가 발생할 수 있습니다.

다음 표에서 vCenter Server 인스턴스의 배치 버전(V2.1 이상 또는 V2.0 이하)에 따라 공용 및 사설 DVS(Distributed Virtual Switch)에 적용되는 네트워크 MTU 구성 설정의 개요를 검토하십시오.

표 5. 인스턴스 버전에 따른 vCenter Server 인스턴스 및 클러스터의 MTU 구성 설정

| vDS |V2.1 이상  |V2.0 이하(또는 V2.0 이하에서 업그레이드됨) |
|:-------------- |:-------------- |:------------- |
|공용 스위치  |1500(기본값) |9000(점보 프레임) |
|사설 스위치 |9000(점보 프레임) |9000(점보 프레임) |

이 설정은 새 인스턴스 및 V2.1 이상으로 배치된 인스턴스의 새 클러스터에 적용됩니다. 또한 이 설정은 V2.1 이상으로 업그레이드된 인스턴스에서 교차 {{site.data.keyword.CloudDataCents_notm}}의 새 클러스터에도 적용됩니다.

V2.0 이하의 기존 인스턴스 또는 V2.1 이상으로 업그레이드된 기존 인스턴스의 경우, 이 설정은 동일한 {{site.data.keyword.CloudDataCent_notm}}의 새 클러스터에는 적용되지 않습니다.

V2.0 이하로 배치된 인스턴스의 경우에는 공용 스위치 MTU 설정을 1500으로 업데이트하는 것이 좋습니다.

### 공용 스위치 MTU 설정 업데이트
{: #vc_bom-procedure-update-public-switch-mtu-setting}

공용 스위치의 MTU 설정을 업데이트하려면 VMware vSphere Web Client에서 다음 단계를 완료하십시오.
1. vDS를 마우스 오른쪽 단추로 클릭하고 **설정 편집**을 클릭하십시오.
2. **특성 탭**에서 **고급** 옵션을 선택하십시오.
3. **최대 MTU** 값이 1500으로 설정되었는지 확인하십시오.

   vDS의 MTU 크기가 변경되면 연결된 업링크(실제 NIC)의 작동이 중지되었다가 재개됩니다. 따라서 해당 업링크를 사용 중인 VM에서 잠시 동안의 가동 중단이 발생합니다. 따라서 MTU 설정 업데이트는 스케줄된 작동 중단 동안 수행하도록 계획하는 것이 좋습니다.
   {:note}

## 관련 링크
{: #vc_bom-related}

* [빌드 번호 및 VMware ESXi와 ESX(2143832)의 버전](https://kb.vmware.com/s/article/2143832)
* [빌드 번호 및 VMware vCenter Server(2143838)의 버전](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [vCenter Server 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server 인스턴스 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)

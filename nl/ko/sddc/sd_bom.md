---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Cloud Foundation 명세서

VMware Cloud Foundation 인스턴스에 대한 BOM(Bill of Materials) 정보를 검토하십시오.

## Cloud Foundation 인스턴스에 대한 VLAN BOM

다음 표에는 Cloud Foundation VLAN에 대한 BOM 정보의 세부사항이 있습니다.

표 1. Cloud Foundation 인스턴스의 VLAN에 대한 BOM

|VLAN      |유형      |세부사항      |
|:----------|:----------|:-------------|
|VLAN1     |공인, 기본 |공용 네트워크 액세스를 위한 실제 ESXi 서버에 지정됩니다. 초기 배치 후에 사용되지 않습니다. 인터넷 액세스에 사용 가능합니다. |
|VLAN2     |사설 A, 기본 |{{site.data.keyword.cloud}}에 의해 실제 ESXi 서버에 지정됩니다. VMware vSphere 관리 트래픽에 대한 관리 인터페이스에서 사용됩니다.<br><br>관리 컴포넌트로 작동하는 가상 머신(VM)에 지정됩니다.<br><br>VMware NSX VTEP(VXLAN Tunnel Endpoint)에 지정됩니다. |
|VLAN3     |사설 B, 포터블 |VMware vSAN에 지정됩니다(사용된 경우).<br><br>VMware NFS에 지정됩니다(사용된 경우).<br><br>VMware vSphere vMotion에 지정됩니다. |

## Cloud Foundation 인스턴스에 대한 소프트웨어 BOM

다음 표에는 Cloud Foundation 소프트웨어 컴포넌트에 대한 BOM 정보의 세부사항이 있습니다.

표 2. Cloud Foundation 인스턴스의 소프트웨어 컴포넌트에 대한 BOM

|제조업체 |컴포넌트                                |버전      |
|:-------------|:-----------------------------------------|:-------------|
|VMware       |vSphere ESXi                             | 6.5 Update EP11(6.5.0-10719125 빌드) |
|VMware       |vCenter Server Appliance                 | 6.5 U2c(6.5.0-9451637 빌드) |
|VMware       |Platform Services Controller             | 6.5 U2c(6.5.0-9451637 빌드) |
|VMware       |vSAN                                     |6.6.1        |
|VMware       |NSX for vSphere                          | 6.4.1        |
|VMware       |SDDC Manager                             |2.4          |
|Microsoft    |Windows Server Standard 에디션(64비트) |2012R2       |

## ESXi 서버의 고급 구성 설정

ESXi 서버에 적용되는 고급 구성 설정의 개요에 대해서는 아래 표를 검토하십시오. 설정은 Cloud Foundation 인스턴스가 이전(V2.1 이하) 릴리스에서 V2.2 이상에 배치(또는 업그레이드)되었는지에 따라 다릅니다.

표 3. Cloud Foundation 인스턴스 및 클러스터에 대한 ESXi 서버 고급 구성 설정

|구성 설정 |V2.2 이상에 새로 배치된 경우  |V2.1 이전에서 업그레이드된 경우 |   
|:------------- |:------------- |:------------- |
|TCP/IP 힙 크기 |**TcpipHeapSize** = 32 |설정되지 않음 |
|최대 TCP/IP 힙 |**TcpipHeapMax** = 1536 |설정되지 않음 |  
|최대 볼륨 |**MaxVolumes** = 256 |두 **/NFS/MaxVolumes** 및 **/NFS41/MaxVolumes** = 256 |  
|하트비트 최대 실패 |**HeartbeatMaxFailures** = 10 |설정되지 않음 |  
|하트비트 빈도 |**HeartbeatFrequency** = 12 |설정되지 않음 |  
|하트비트 제한시간 |**HeartbeatTimeout** = 5 |설정되지 않음 |
|최대 큐 길이 |**MaxQueueDepth** = 64 |설정되지 않음 |
|큐 전체 샘플 크기 |**QFullSampleSize** = 32 |**/Disk/QFullSampleSize** = 32 |
|큐 전체 임계값 |**QFullThreshold** = 8 |**/Disk/QFullThreshold** = 8 |

### 참고

* 서비스가 ESXi 서버에서 기본 NFS 마운트 수보다 더 많은 NFS 마운트를 사용할 수 있으므로 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스에 **MaxVolumes** 설정이 필요합니다.
* 구성 설정에 대한 **설정되지 않음** 값은 새 설정이 자동으로 적용되지 않음을 나타내며, ESXi 서버를 다시 부팅해야 하므로 중단이 발생할 수 있습니다.

  모든 인스턴스의 일관성과 스토리지 확장에 필요한 충분한 지원을 허용하기 위해 **설정되지 않음** 구성 설정을 새 값으로 변경하는 것이 좋습니다. IBM은 모든 {{site.data.keyword.vmwaresolutions_short}} V2.2 이상 릴리스의 새 설정에 대해서만 테스트하도록 계획하고 있습니다.

  자세한 정보는 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239)를 참조하십시오.

### 관련 링크

* [빌드 번호 및 VMware ESXi/ESX(2143832)의 버전](https://kb.vmware.com/s/article/2143832)
* [빌드 번호 및 VMware vCenter Server(2143838)의 버전](https://kb.vmware.com/s/article/2143838)
* [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Cloud Foundation 개요](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Cloud Foundation 인스턴스 계획](/docs/services/vmwaresolutions/sddc/sd_planning.html)

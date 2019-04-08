---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 인스턴스에 대한 용량 확장 및 축소
{: #vc_addingremovingservers}

비즈니스 요구사항에 따라 ESXi 서버 또는 네트워크 파일 시스템(NFS) 스토리지를 추가하거나 제거하여 VMware vCenter Server 인스턴스의 용량을 확장하거나 축소할 수 있습니다.

V2.9 릴리스부터는 서버가 유지보수 모드에 있는 동안 새 ESXi 서버를 클러스터에 추가할 수 있습니다. 또한 여러 클러스터에서 ESXi 서버를 동시에 추가 또는 제거할 수 있습니다. 다음 동시 조작을 사용할 수 있습니다.

* 호스트를 클러스터에 추가하고 호스트를 추가 클러스터에 추가하십시오.
* 호스트를 클러스터에서 제거하고 호스트를 추가 클러스터에서 제거하십시오.
* 호스트를 클러스터에 추가하고 호스트를 추가 클러스터에서 제거하십시오.
* 호스트를 클러스터에서 제거하고 호스트를 추가 클러스터에 추가하십시오.

NFS 스토리지 공유를 기존 NFS 또는 vSAN vCenter Server 클러스터에 추가하거나 기존 NFS 또는 vSAN vCenter Server 클러스터에서 제거할 수 있습니다.
{:note}

초기 클러스터에 스토리지로 vSAN이 있는 경우 배치 후 하나 이상의 ESXi 서버를 추가하면 클러스터 스토리지 용량이 늘어날 수 있습니다.

## vCenter Server 인스턴스에 ESXi 서버 추가
{: #vc_addingremovingservers-adding}

### ESXi 서버를 추가하기 전에
{: #vc_addingremovingservers-adding-prereq}

* VMware vSphere Web Client에서 ESXi 서버를 추가하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_full}} 콘솔과 동기화되지 않습니다.
* NFS 스토리지가 포함된 vCenter Server 인스턴스에는 최소 두 개의 ESXi 서버가 있어야 합니다. V2.1 이상에 배치된 인스턴스의 경우, 최대 51개의 ESXi 서버를 보유하도록 기본 클러스터를 확장할 수 있습니다. 기본이 아닌 각 클러스터는 최대 59개의 ESXi 서버를 보유하도록 확장할 수 있습니다.
* vSAN 스토리지가 포함된 vCenter Server 인스턴스에는 최소 네 개의 ESXi 서버가 있어야 합니다.
* V2.0 이전에 배치된 vCenter Server 인스턴스의 경우, 최대 32개의 ESXi 서버를 보유하도록 각 클러스터를 확장할 수 있습니다.
* 한 번에 1 - 20개의 ESXi 서버를 추가할 수 있습니다. 최소 ESXi 서버에 대한 자세한 정보는 [두 개의 노드 vCenter Server 인스턴스가 고가용성입니까?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)를 참조하십시오.

### ESXi 서버를 추가하는 프로시저
{: #vc_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 추가할 클러스터를 클릭하십시오.
5. **ESXi 서버** 섹션에서 **추가**를 클릭하십시오.
6. **서버 추가** 창에서 추가할 서버의 수를 입력하십시오.
7. 또는 유지보수 모드 동안 서버를 추가하려면 선택란을 선택하십시오.
8. 예상 비용을 검토하고 **추가**를 클릭하십시오.

### ESXi 서버를 추가한 후의 결과
{: #vc_addingremovingservers-adding-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버를 추가하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 클러스터의 목록에 추가된 새 ESXi 서버가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.
4. 다음 상황에서는 ZVM(Zerto Virtual Manager) 콘솔 및 사전에 채워진 Zerto Virtual Replication Appliance(VRA) IP 주소를 사용하여 수동으로 VRA 가상 머신(VM)을 배치해야 합니다.
   * 서버가 유지보수 모드에 있고 {{site.data.keyword.cloud_notm}}용 Zerto가 설치되어 있는 동안 ESXi 서버를 기본 클러스터에 추가할 경우.
   * 유지보수 모드의 ESXi 서버가 있는 vCenter Server 인스턴스에 {{site.data.keyword.cloud_notm}}용 Zerto를 추가할 경우.

유지보수 모드 동안 ESXi 서버를 추가하는 경우, 유지보수 모드를 제거할 때까지 가상 머신이 새 서버에 마이그레이션되지 않습니다.   
{:important}

## vCenter Server 인스턴스에서 ESXi 서버 제거
{: #vc_addingremovingservers-removing}

### ESXi 서버를 제거하기 전에
{: #vc_addingremovingservers-removing-prereq}

* VMware vSphere Web Client에서 ESXi 서버를 제거하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* NFS 스토리지가 포함된 vCenter Server 인스턴스에는 최소 두 개의 ESXi 서버가 있어야 하고 vSAN 스토리지가 포함된 vCenter Server 인스턴스에는 최소 네 개의 ESXi 서버가 있어야 합니다.
* F5 on {{site.data.keyword.cloud_notm}} 또는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 ESXi 서버를 제거하기 전에 VM을 호스팅하는 ESXi 서버와 다른 ESXi 서버로 F5 BIG-IP 및 FortiGate VM을 마이그레이션해야 합니다.
* 활성 상태의 오퍼레이션으로 인해 ESXi 서버가 제거되지 않을 수 있으므로, IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스가 설치된 상태에서 ESXi 서버를 제거하기 전에 활성 상태가 아닌(실패 또는 진행 중) 백업 또는 복원 오퍼레이션이 있는지 확인하십시오.
* ESXi 서버를 제거하는 경우 서버가 유지보수 모드로 설정되고, 그 이후 서버에서 실행되는 모든 가상 머신(VM)이 vCenter Server에서 제거되기 전에 마이그레이션됩니다. VM의 재배치에 대한 제어를 최대화하려면 제거할 ESXi 서버를 유지보수 모드로 설정하고 VMware vSphere Web Client를 사용하여 수동으로 ESXi 서버에서 실행되는 VM을 마이그레이션하는 것이 좋습니다. 그런 다음, {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여 ESXi 서버를 제거하십시오.

### ESXi 서버를 제거하는 프로시저
{: #vc_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 제거할 클러스터를 클릭하십시오.
5. **ESXi 서버** 섹션에서 제거할 서버를 선택한 후 **제거**를 클릭하십시오.

### ESXi 서버를 제거한 후의 결과
{: #vc_addingremovingservers-removing-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버를 제거하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 ESXi 서버가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   제거된 ESXi 서버에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
   {:note}

## vCenter Server 인스턴스에 NFS 스토리지 추가
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### NFS 스토리지를 추가하기 전에
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

VMware vSphere Web Client에서 NFS 스토리지를 추가하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. IBM은 인스턴스에 수동으로 추가하는 NFS 파일 공유를 관리하지 않습니다.

### NFS 스토리지를 추가하는 프로시저
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 NFS 스토리지를 추가할 클러스터를 클릭하십시오.
5. **스토리지** 섹션에서 **추가**를 클릭하십시오.
6. **스토리지** 창에서 스토리지 구성을 완료하십시오.
   * 모든 파일 공유에 동일한 설정을 추가하여 구성하려는 경우에는 **공유 수**, **성능** 및 **크기(GB)**를 지정하십시오.
   * 파일 공유를 개별적으로 추가하여 구성하려는 경우에는 **공유 개별 구성**을 선택한 후, **공유 스토리지 추가** 레이블 옆에 있는 **+** 아이콘을 클릭하고 각 개별 파일 공유에 대한 **성능** 및 **크기(GB)**를 선택하십시오. 하나 이상의 파일 공유를 선택해야 합니다.
7. **NFS 스토리지 추가**를 클릭하십시오.

### NFS 스토리지를 추가한 후의 결과
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. NFS 스토리지를 추가하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 NFS 스토리지와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 클러스터의 목록에 추가된 새 NFS 스토리지가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.

## vCenter Server 인스턴스에서 NFS 스토리지 제거
{: #vc_addingremovingservers-removing-nfs-storage}

### NFS 스토리지를 제거하기 전에
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* VMware vSphere Web Client에서 NFS 스토리지를 제거하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* NFS 스토리지를 제거하기 전에 해당 스토리지에 상주하는 모든 VM이 제거되었는지 확인하십시오.
* 제거할 공유가 올바른 vCenter Server 인스턴스와 연관되었는지 확인하십시오.
* 클러스터는 **사용할 준비가 됨** 상태여야 합니다.

### NFS 스토리지를 제거하는 프로시저
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 NFS 스토리지를 제거할 클러스터를 클릭하십시오.
5. **스토리지** 섹션에서 제거할 스토리지 공유를 선택한 후 **삭제**를 클릭하십시오.
6. **스토리지 제거** 창에서 **제거**를 클릭하십시오.

### NFS 스토리지를 제거한 후의 결과
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. NFS 스토리지를 제거하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 NFS 스토리지와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 NFS 스토리지가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   제거된 NFS 스토리지에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
   {:note}

## 관련 링크
{: #vc_addingremovingservers-related}

* [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server 인스턴스 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server NSX-T add hosts, add servers to vCenter Server NSX-T, remove hosts from vCenter Server NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T 인스턴스에 대한 용량 확장 및 축소
{: #vc_nsx-t_addingremovingservers}

비즈니스 요구사항에 따라 ESXi 서버 또는 네트워크 파일 시스템(NFS) 스토리지를 추가하거나 제거하여 VMware vCenter Server with NSX-T 인스턴스의 용량을 확장하거나 축소할 수 있습니다.

* V3.1 릴리스부터는 클러스터에서 기존 호스트가 아닌 기존 구성 또는 대체 구성을 선택하여 새 ESXi 서버를 기존 클러스터에 추가할 수 있습니다. 새 서버 주문 시 인스턴스를 선택하는 데 기존 구성을 사용할 수 있습니다. 성능 또는 안전성 문제를 방지하기 위해 클러스터가 CPU, RAM 및 스토리지와 관련하여 동일하거나 유사한 구성을 사용하는 것이 좋습니다. 이 기능은 동일한 클러스터 내의 하드웨어 업데이트에 유용합니다. 클러스터에는 하나의 스토리지 유형만 허용됩니다.
* V3.0 릴리스부터 NFS 스토리지 및 ESXi 서버를 **사용할 준비가 됨** 상태의 클러스터에 동시에 추가하거나 제거할 수 있습니다. 예를 들어, 한 클러스터에서 ESXi 서버를 추가하거나 제거하고 다른 클러스터에서 NFS 스토리지를 추가하거나 제거할 수 있습니다.
* V2.9 릴리스부터는 서버가 유지보수 모드에 있는 동안 새 ESXi 서버를 클러스터에 추가할 수 있습니다. 또한 여러 클러스터에서 ESXi 서버를 동시에 추가 또는 제거할 수 있습니다.

**참고**:
* 초기 클러스터에 스토리지로 vSAN이 있는 경우 배치 후 하나 이상의 ESXi 서버를 추가하면 클러스터 스토리지 용량이 늘어날 수 있습니다.
* NFS 스토리지 공유를 기존 NFS 또는 vSAN vCenter Server with NSX-T 클러스터에 추가하거나 기존 NFS 또는 vSAN vCenter Server 클러스터에서 제거할 수 있습니다.

## vCenter Server with NSX-T 인스턴스에 ESXi 서버 추가
{: #vc_nsx-t_addingremovingservers-adding}

### ESXi 서버를 추가하기 전에
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 ESXi 서버를 추가하십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. 따라서 온프레미스 ESXi 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 ESXi 서버에 대해서만 ESXi 서버를 vCenter Server에 추가하십시오.
* NFS 스토리지가 포함된 vCenter Server with NSX-T 인스턴스에는 최소 세 개의 ESXi 서버가 있어야 합니다. 최대 51개의 ESXi 서버를 보유하도록 기본 클러스터를 확장할 수 있습니다. 기본이 아닌 각 클러스터는 최대 59개의 ESXi 서버를 보유하도록 확장할 수 있습니다.
* vSAN 스토리지가 포함된 vCenter Server with NSX-T 인스턴스에는 최소 네 개의 ESXi 서버가 있어야 합니다.

### ESXi 서버를 추가하는 프로시저
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 추가할 클러스터를 클릭하십시오.
5. **ESXi 서버** 섹션에서 **추가**를 클릭하십시오.
6. **서버 추가** 창에서 추가할 서버의 수를 입력하십시오.
7. 또는 유지보수 모드 동안 서버를 추가하려면 선택란을 선택하십시오. 기본적으로 선택란이 선택되어 있습니다.

   새 ESXi 서버를 프로비저닝하는 경우 **유지보수 모드** 선택란을 선택하지 않으면 가상 머신(VM)은 즉시 새 서버로 마이그레이션됩니다. 마이그레이션이 시작되기 전에는 확인 메시지가 수신되지 않습니다.
   {:important}

8. 베어메탈 구성을 완료하십시오.
   * 클러스터의 기존 호스트에서 구성을 선택하십시오.
   * 새 {{site.data.keyword.baremetal_short_sing}} 구성을 선택하고 CPU 모델 및 RAM 크기를 지정하십시오.
9. 스토리지 구성을 완료하십시오. 용량 및 캐시 디스크의 디스크 유형과 디스크 수 및 vSAN License 에디션을 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
10. 예상 비용을 검토하고 **추가**를 클릭하십시오.

  **예상 금액에 추가**를 클릭하여 {{site.data.keyword.cloud_notm}} 예상 도구에 프로비저닝된 리소스를 추가할 수도 있습니다. 구매를 고려할 수 있는 기타 {{site.data.keyword.cloud_notm}} 리소스와 함께 선택된 {{site.data.keyword.vmwaresolutions_short}} 리소스의 비용을 예상하려는 경우 유용합니다.

### ESXi 서버를 추가한 후의 결과
{: #vc_nsx-t_addingremovingservers-adding-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버를 추가하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 클러스터의 목록에 추가된 새 ESXi 서버가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.

유지보수 모드 동안 ESXi 서버를 추가하는 경우, 클러스터를 유지보수 모드에서 제거할 때까지 가상 머신(VM)이 새 서버에 마이그레이션되지 않습니다.   
{:important}

## vCenter Server with NSX-T 인스턴스에서 ESXi 서버 제거
{: #vc_nsx-t_addingremovingservers-removing}

### ESXi 서버를 제거하기 전에
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 ESXi 서버를 제거하십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. 따라서 온프레미스 ESXi 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 ESXi 서버에 대해서만 ESXi 서버를 vCenter Server에서 제거하십시오.
* NFS 스토리지가 포함된 vCenter Server with NSX-T 인스턴스에는 최소 세 개의 ESXi 서버가 있어야 하고 vSAN 스토리지가 포함된 vCenter Server 인스턴스에는 최소한 4개의 ESXi 서버가 있어야 합니다.
* ESXi 서버를 제거하는 경우 서버가 유지보수 모드로 설정되고, 그 이후 서버에서 실행되는 모든 VM이 vCenter Server에서 제거되기 전에 마이그레이션됩니다. VM의 재배치에 대한 제어를 최대화하려면 제거할 ESXi 서버를 유지보수 모드로 설정하고 VMware vSphere Web Client를 사용하여 수동으로 ESXi 서버에서 실행되는 VM을 마이그레이션하는 것이 좋습니다. 그런 다음, {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여 ESXi 서버를 제거하십시오.

### ESXi 서버를 제거하는 프로시저
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 제거할 클러스터를 클릭하십시오.
5. **ESXi 서버** 섹션에서 제거할 서버를 선택한 후 **제거**를 클릭하십시오.

### ESXi 서버를 제거한 후의 결과
{: #vc_nsx-t_addingremovingservers-removing-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버를 제거하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 ESXi 서버가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   제거된 ESXi 서버에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
   {:note}

## vCenter Server with NSX-T 인스턴스에 NFS 스토리지 추가
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### NFS 스토리지를 추가하기 전에
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

VMware vSphere Web Client에서 NFS 스토리지를 추가하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. IBM은 인스턴스에 수동으로 추가하는 NFS 파일 공유를 관리하지 않습니다.

### NFS 스토리지를 추가하는 프로시저
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 NFS 스토리지를 추가할 클러스터를 클릭하십시오.
5. **스토리지** 섹션에서 **추가**를 클릭하십시오.
6. **스토리지** 창에서 스토리지 구성을 완료하십시오.
   * 모든 파일 공유에 동일한 설정을 추가하여 구성하려는 경우에는 **공유 수**, **성능** 및 **크기(GB)**를 지정하십시오.
   * 파일 공유를 개별적으로 추가하여 구성하려는 경우에는 **공유 개별 구성**을 선택한 후, **공유 스토리지 추가** 레이블 옆에 있는 **+** 아이콘을 클릭하고 각 개별 파일 공유에 대한 **성능** 및 **크기(GB)**를 선택하십시오. 하나 이상의 파일 공유를 선택해야 합니다.
7. 예상 비용을 검토하고 **NFS 스토리지 추가**를 클릭하십시오.

  **예상 금액에 추가**를 클릭하여 {{site.data.keyword.cloud_notm}} 예상 도구에 프로비저닝된 리소스를 추가할 수도 있습니다. 구매를 고려할 수 있는 기타 {{site.data.keyword.cloud_notm}} 리소스와 함께 선택된 {{site.data.keyword.vmwaresolutions_short}} 리소스의 비용을 예상하려는 경우 유용합니다.

### NFS 스토리지를 추가한 후의 결과
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. NFS 스토리지를 추가하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 NFS 스토리지와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 클러스터의 목록에 추가된 새 NFS 스토리지가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.

## vCenter Server with NSX-T 인스턴스에서 NFS 스토리지 제거
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### NFS 스토리지를 제거하기 전에
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* VMware vSphere Web Client에서 NFS 스토리지를 제거하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* NFS 스토리지를 제거하기 전에 해당 스토리지에 상주하는 모든 VM이 제거되었는지 확인하십시오.
* 제거할 공유가 올바른 vCenter Server 인스턴스와 연관되었는지 확인하십시오.
* 클러스터는 **사용할 준비가 됨** 상태여야 합니다.

### NFS 스토리지를 제거하는 프로시저
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 NFS 스토리지를 제거할 클러스터를 클릭하십시오.
5. **스토리지** 섹션에서 제거할 스토리지 공유를 선택한 후 **삭제**를 클릭하십시오.
6. **스토리지 제거** 창에서 **제거**를 클릭하십시오.

### NFS 스토리지를 제거한 후의 결과
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. NFS 스토리지를 제거하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 NFS 스토리지와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 NFS 스토리지가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   제거된 NFS 스토리지에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
   {:note}

## 관련 링크
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server 인스턴스 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [vCenter Server with NSX-T 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:external}

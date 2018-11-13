---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation 인스턴스에 대한 용량 확장 및 축소

비즈니스 요구사항에 따라 ESXi 서버를 추가하거나 제거하여 VMware Cloud Foundation 인스턴스의 용량을 확장하거나 축소할 수 있습니다.

Cloud Foundation 인스턴스에는 최대 5개의 클러스터가 포함될 수 있으며, 이 중 하나가 기본값입니다. 각 초기 클러스터에는 최대 51개의 ESXi 서버가 포함될 수 있으며, 추가 클러스터에는 최대 59개의 ESXi 서버가 포함될 수 있습니다.

## Cloud Foundation 인스턴스에 ESXi 서버 추가

### ESXi 서버를 추가하기 전에

* VMware vSphere Web Client에서 ESXi 서버를 추가하지 마십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_full}} 콘솔과 동기화되지 않습니다.
* 주문한 기본 플랫폼에는 기본적으로 네 개의 ESXi 서버가 있습니다. 최대 32개의 ESXi 서버까지 플랫폼을 확장할 수 있습니다. 그러나 한 번에 추가할 수 있는 {{site.data.keyword.baremetal_short}}의 수는 다음과 같습니다.
   * **소형** 및 **대형** 구성의 경우 한 번에 1 - 10개의 ESXi 서버를 추가할 수 있습니다.
   * **Skylake** 및 **Broadwell** 구성의 경우, 한 번에 1 - 20개의 ESXi 서버를 추가할 수 있습니다. 

## ESXi 서버를 추가하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **Cloud Foundation 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 추가할 클러스터를 클릭하십시오.
5. **ESXi 서버** 섹션에서 **추가**를 클릭하십시오.
6. **서버 추가** 창에서 추가할 서버의 수를 입력하고 예상 비용을 검토한 후 **추가**를 클릭하십시오.

### ESXi 서버를 추가한 후의 결과

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버가 추가될 때 이메일로 알림을 받습니다.
3. 클러스터의 목록에 추가된 새 ESXi 서버가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.

## Cloud Foundation 인스턴스에서 ESXi 서버 제거

### ESXi 서버를 제거하기 전에

* VMware vSphere Web Client에서 ESXi 서버를 제거하지 마십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* 주문한 기본 플랫폼에는 기본적으로 네 개의 ESXi 서버가 있습니다. 추가한 ESXi 서버를 제거할 수 있습니다. 기본 ESXi 서버는 제거할 수 없습니다.
* F5 on {{site.data.keyword.cloud_notm}} 또는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 ESXi 서버를 제거하기 전에 VM을 호스팅하는 ESXi 서버와 다른 ESXi 서버로 F5 BIG-IP 및 FortiGate VM을 마이그레이션해야 합니다.
* IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스가 설치된 ESXi 서버를 제거하기 전에 활성 상태인 백업 또는 복원 오퍼레이션이 없는지 확인하십시오. 실패했거나 진행 중인 활성 오퍼레이션으로 인해 ESXi 서버가 제거되지 않을 수 있습니다.

## ESXi 서버를 제거하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **Cloud Foundation 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 제거할 클러스터를 클릭하십시오.
6. **ESXi 서버** 섹션에서 제거할 서버를 선택한 후 **제거**를 클릭하십시오.

### ESXi 서버를 제거한 후의 결과

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버가 제거될 때 이메일로 알림을 받습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 비용 청구 주기 종료 시 ESXi 서버가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   제거된 ESXi 서버에 대한 {{site.data.keyword.cloud_notm}} 비용 청구 주기 종료 시까지 비용이 청구됩니다.
   {:note}

### 관련 링크

* [Cloud Foundation 명세서](sd_bom.html)
* [Cloud Foundation 인스턴스에 대한 요구사항 및 계획](sd_planning.html)
* [Cloud Foundation 인스턴스의 클러스터 추가, 보기 및 삭제](sd_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

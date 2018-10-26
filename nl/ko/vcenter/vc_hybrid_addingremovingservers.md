---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# vCenter Server with Hybridity Bundle 인스턴스의 용량 확장 및 축소

비즈니스 요구사항에 따라 ESXi 서버를 추가하거나 제거하여 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스의 용량을 확장하거나 축소할 수 있습니다.

초기 클러스터의 스토리지가 vSAN이었으므로, 배치 후 하나 이상의 ESXi 서버를 추가하면 클러스터 스토리지 용량을 늘릴 수 있습니다.

## vCenter Server with Hybridity Bundle 인스턴스에 ESXi 서버 추가

### ESXi 서버를 추가하기 전에

* VMware vSphere Web Client에서 ESXi 서버를 추가하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* vSAN 스토리지는 네 개 이상의 ESXi 서버를 필요로 합니다.

## ESXi 서버를 추가하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 확장할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 추가할 클러스터를 클릭하십시오.
5. **ESXi 서버** 테이블에서 **추가**를 클릭하십시오.
6. **서버 추가** 창에서 추가할 서버의 수를 입력하고, 가격 링크를 클릭하여 예상 비용을 검토한 후 **추가**를 클릭하십시오.

### ESXi 서버를 추가한 후의 결과

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 작성하기 전에 오퍼레이션이 완전히 완료되도록 하십시오.
2. ESXi 서버를 추가하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 클러스터의 목록에 추가된 새 ESXi 서버가 표시되지 않으면 이메일 또는 콘솔 알림을 확인하여 실패에 대한 추가 세부사항을 찾을 수 있습니다.

## vCenter Server with Hybridity Bundle 인스턴스에서 ESXi 서버 제거

### ESXi 서버를 제거하기 전에

* VMware vSphere Web Client에서 ESXi 서버를 제거하지 마십시오. vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다.
* vSAN 스토리지는 네 개 이상의 ESXi 서버를 필요로 합니다.
* F5 on {{site.data.keyword.cloud_notm}} 또는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 ESXi 서버를 제거하기 전에 VM을 호스팅하는 ESXi 서버와 다른 ESXi 서버로 F5 BIG-IP 및 FortiGate VM을 마이그레이션해야 합니다.
* 활성 상태의 오퍼레이션으로 인해 ESXi 서버가 제거되지 않을 수 있으므로, IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스가 설치된 상태에서 ESXi 서버를 제거하기 전에 활성 상태가 아닌(실패 또는 진행 중) 백업 또는 복원 오퍼레이션이 있는지 확인하십시오.
* ESXi 서버를 제거하는 경우 서버가 유지보수 모드로 설정되고, 그 이후 서버에서 실행되는 모든 가상 머신(VM)이 vCenter Server에서 제거되기 전에 마이그레이션됩니다. VM의 재배치에 대한 제어를 최대화하려면 제거할 ESXi 서버를 유지보수 모드로 설정하고 VMware vSphere Web Client를 사용하여 수동으로 ESXi 서버에서 실행되는 VM을 마이그레이션하는 것이 좋습니다. 그런 다음, {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여 ESXi 서버를 제거하십시오.

## ESXi 서버를 제거하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 용량을 축소할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
4. **클러스터** 테이블에서 ESXi 서버를 제거할 클러스터를 클릭하십시오.
5. **ESXi 서버** 테이블에서 제거할 서버를 선택한 후 **제거**를 클릭하십시오.

### ESXi 서버를 제거한 결과

1. 인스턴스 상태가 **사용할 준비가 됨**에서 **수정 중**으로 변경되는 동안 콘솔에서 약간의 지연이 발생할 수 있습니다. 인스턴스에 추가 변경사항을 수행하기 전에 오퍼레이션이 완전히 완료되도록 허용하십시오.
2. ESXi 서버를 제거하는 요청이 처리 중이라는 알림을 이메일로 받습니다. 콘솔에서 ESXi 서버와 연관된 클러스터의 상태가 **수정 중**으로 변경되었습니다.
3. 일반적으로 30일인 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 ESXi 서버가 {{site.data.keyword.cloud_notm}} 인프라에서 완전히 재확보됩니다.

   **주의:** 제거된 ESXi 서버에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 비용이 청구됩니다.

### 관련 링크

* [vCenter Server 명세서](vc_bom.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 요구사항 및 계획](vc_hybrid_planning.html)
* [vCenter Server with Hybridity Bundle 인스턴스의 클러스터 추가, 보기 및 삭제](vc_hybrid_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

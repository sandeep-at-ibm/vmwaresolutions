---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# vCenter Server 아티팩트 변경에 대한 고려사항

{{site.data.keyword.vmwaresolutions_full}}에 대해 예약된 사용자, 리소스 또는 서브넷을 변경하면 관리 오퍼레이션에 영향을 줄 수 있습니다.

**중요:** VMware vSphere Web Client의 **사용자 및 그룹** 페이지에서 **ic4v-vCenter** 그룹의 글로벌 권한을 편집하지 마십시오. 이러한 변경에는 사용자 이름 변경, 사용자 삭제 또는 해당 비밀번호 변경이 포함됩니다.

## 자동화 ID

**자동화** ID는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 제공된 자동화된 오퍼레이션에 의해 사용되는 사용자 계정입니다. 

해당 신임 정보에 기반한 콘솔 오퍼레이션이 실패할 수 있으므로 콘솔에서 자동화된 오퍼레이션의 사용자 및 비밀번호를 변경하면 안 됩니다.

## 서비스 고유 사용자 계정

각 서비스는 vCenter Server에 내부 사용자 계정을 작성합니다. 이 계정은 서비스와 연관된 관리 조작이 서비스에 대해 해당 조작을 수행하기 위해 vCenter Server에 연결하는 데 필요합니다.

**중요**: 가동 중단 및 연결 문제점을 방지하기 위해, 이 사용자 계정의 사용자 ID, 비밀번호 또는 비밀번호 만기 설정을 변경하는 경우에는 연관된 서비스에서도 해당 정보를 업데이트해야 합니다.

이 계정의 사용자 ID 형식은 `<service_name>-<service_uuid>@VSPHERE.LOCAL`입니다. 예를 들어, Veeam on {{site.data.keyword.cloud_notm}} 서비스가 스케줄된 백업을 수행하기 위해 vCenter Server에 연결하는 데 사용하는 사용자 ID는 `Veeam-<Veeam_uuid>@VSPHERE.LOCAL`입니다.

## vCenter Server 인스턴스용 VMware 리소스(V1.9 이상)

V1.9 이상에 배치된 인스턴스의 경우, vCenter Server 인스턴스가 **사용할 준비** 상태에 있으면 VMware vSphere Web Client에서 VMware 가상 데이터 센터, 클러스터, 스위치, 포트 그룹 및 고객 데이터 저장소 이름을 수정할 수 있습니다. 그러나 관리 데이터 저장소의 이름은 기본값(vSAN 인스턴스의 경우 **vsanDatastore**, Network File System(NFS) 인스턴스의 경우 **management-share**)을 변경하지 않아야 합니다.

## vCenter Server 인스턴스용 VMware 리소스(V1.8 이상)

다음 표는 SSO 관리자가 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 VMware vCenter Server 리소스를 변경하는 경우 영향을 받을 수 있는 오퍼레이션을 나열합니다. 복구하기 위한 솔루션을 사용할 수 있는 경우 해당 솔루션도 제공됩니다.

이 표는 V1.8 이하에 배치된 인스턴스, 그리고 V1.8 이하에서 배치된 후 V1.9 이상으로 업그레이드된 인스턴스에 적용할 수 있습니다.

표 1. VMware 리소스로 영향을 받은 오퍼레이션

|시도된 변경  |영향을 받은 오퍼레이션  |심각도  |복구 방법  |
|:------------- |:------------- |:--------------|:--------------|
|VMware 가상 데이터 센터 이름 변경 |새 ESXi 서버가 변경된 가상 데이터 센터에 결합할 수 없으므로 VMware 가상 데이터 센터 추가에 실패할 수 있음 |중요 |VMware 가상 데이터 센터 이름을 원래의 이름으로 다시 변경함 |
|포트 그룹 이름 변경    |ESXi 서버 추가에 실패할 수 있음 |중요 |포트 그룹 이름을 원래의 이름으로 다시 변경함 |
|클러스터 이름 변경 |ESXi 서버 추가에 실패할 수 있음 |중요 |클러스터 이름을 원래의 이름으로 다시 변경함
|공용 또는 사설 DVS(Distributed Virtual Switch) 이름 변경 |ESXi 서버 추가에 실패할 수 있음 |중요 |공용 또는 사설 DVS(Distributed Virtual Switch) 이름을 원래의 이름으로 변경
|vSAN을 사용하는 인스턴스에서 vSAN 데이터 저장소 이름 변경 |ESXi 서버 추가에 실패할 수 있음<br><br>인스턴스 업그레이드가 실패할 수 있음 |중요 |vSAN 데이터 저장소 이름을 원래 이름인 **vsanDatastore**로 다시 변경함
|NFS를 사용하는 인스턴스에서 관리 NFS 데이터 저장소 이름 변경 |ESXi 서버 추가에 실패할 수 있음<br><br>인스턴스 업그레이드가 실패할 수 있음 |중요 |NFS 관리 데이터 저장소 이름을 원래 이름인 **management-share**로 다시 변경하고 NFS 데이터 저장소를 ESXi 서버에 읽기 전용으로 다시 마운트함

다음 표는 VC/PSC 루트 사용자가 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 vCenter Server 리소스를 변경하는 경우 영향을 받을 수 있는 오퍼레이션을 나열합니다.

표 2. VC/PSC 루트 액세스(로컬)에 대해 영향을 받은 오퍼레이션

|시도된 변경  |영향을 받은 오퍼레이션  |심각도  |복구 방법  |
|:------------- |:------------- |:--------------|:--------------|
|쉘 액세스 사용 또는 사용 안함    |PSC와 vCenter Server의 패치 및 업데이트가 실패할 수 있음    |중요    |해당사항 없음    |

## vCenter Server 인스턴스에 대한 관리 서브넷

다음 정보는 {{site.data.keyword.vmwaresolutions_short}}에서 주문된 서브넷에 대해 설명하고 사용자 전용의 추가 서브넷을 주문할 수 있는 옵션을 제공합니다.

**주의**: 다른 목적으로 컴포넌트를 사용하지 마십시오. 그렇지 않으면, 환경의 안전성이 심각하게 손상될 수 있습니다.

각 {{site.data.keyword.cloud_notm}} Bare Metal Server 주문 시 기본적으로 다음 범위의 IP 주소가 주문됩니다.
*  32개 IP 주소의 기본 공용 범위
*  64개 IP 주소의 기본 개인 범위

또한 다음 관리 서브넷도 {{site.data.keyword.vmwaresolutions_short}}에 대해 예약됩니다.
*  첫 번째 VLAN에서 64개 IP 주소의 두 가지 포터블 사설 서브넷(하나는 관리용, 다른 하나는 VTEPS용)
*  두 번째 VLAN에서 64개 IP 주소의 두 가지 포터블 사설 서브넷(하나는 VMotion용, 다른 하나는 vSAN용)
*  공인 VLAN에서 16개 IP 주소의 공인 포터블 서브넷

사용할 추가 서브넷이 필요한 경우 다음 방법 중 하나로 사용할 IP 주소를 얻을 수 있습니다.
*  **옵션 1(권장)**: VMware NSX 가상 네트워크 오버레이를 사용하십시오. 샘플 VXLAN 템플리트는 주문 시 제공됩니다. 이 VXLAN은 소프트웨어 정의 네트워킹(SDN)을 빌드하기 위한 시작 지점으로 사용될 수 있습니다. 자세한 정보는 [고객 관리 NSX Edge를 사용하도록 네트워크 구성](vc_esg_config.html)을 참조하십시오.
*  **옵션 2**: 고유한 포터블 공인 또는 사설 서브넷을 주문하여 IP 주소를 가져오십시오. 주문한 서브넷을 관리 서브넷과 구별하기 위해 주문 중인 모든 서브넷에 참고사항을 추가할 수 있습니다.

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# IBM Spectrum Protect Plus on IBM Cloud 개요

{{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스는 가상 환경에 대한 데이터 보호, 데이터 재사용 및 데이터 복구를 위한 효율적이고 확장 가능한 솔루션을 제공합니다. 사용자는 독립형 솔루션으로서 서비스를 구현하거나 장기 저장 및 데이터 통제를 위한 사본을 오프로드하기 위해 이를 IBM Spectrum Protect 환경과 통합할 수 있습니다.

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.2 이상 릴리스에 배치된(또는 이 릴리스로 업그레이드된) 인스턴스에서만 사용할 수 있습니다.

**참고:**
* V2.4 이상 릴리스로 배치된 인스턴스에 대해 이 서비스를 설치하는 경우에는 IBM Spectrum Protect Plus V10.1.1 패치 1이 설치됩니다.
* V2.3으로 배치된 인스턴스에 대해 이 서비스를 설치하는 경우에는 IBM Spectrum Protect Plus V10.1.1이 설치됩니다.
* V2.2에 배치된 인스턴스에 대한 서비스를 설치하면 IBM Spectrum Protect Plus V10.1.0이 설치됩니다.


## IBM Spectrum Protect Plus on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### vCenter 리소스

* IBM Spectrum Protect Plus 서버를 실행 중인 서버 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 운영 체제
   * 4 x 2.0GHz 코어
   * 32GB RAM
   * 370GB 디스크
* IBM Spectrum Protect Plus vSnap 서버 및 VADP 프록시를 실행 중인 보조 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 운영 체제
   * 선택된 스토리지 크기 및 [IBM Spectrum Protect Plus 블루프린트](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) 크기 조정 지침에 따라 구성된 CPU 및 RAM
   * 150GB 디스크

### 백업용 스토리지

다음 옵션이 포함된, 백업을 위한 사용자 정의할 수 있는 스토리지:
* 파일 스토리지 수: 1 - 10
* 각 endurance 파일 스토리지: 500, 1000, 2000, 4000, 8000 또는 12000GB
* 스토리지 성능: 0.25, 2 또는 4IOPS/GB

계획 및 크기 조정에 대해서는 [IBM Spectrum Protect Plus 블루프린트 및 크기 조정 도구](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)를 참조하십시오.

### 관리용 스토리지

IBM Spectrum Protect Plus 가상 머신을 호스팅하며 백업 스토리지와 동일한 서브넷에서 실행 중인 하나의 1000GB, 2 IOPS/GB Endurance 파일 스토리지

### 네트워킹

2개의 포터블 사설 IP 주소.

### 라이센스 및 요금

* IBM Spectrum Protect Plus(10개에서 최대 1000개의 VM 라이센스, 10개씩 증가)
* BYOL로서 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔(10의 패키지의 VM 수)을 통해 제공된 IBM Spectrum Protect Plus 라이센스

## IBM Spectrum Protect Plus on IBM Cloud 설치 시 고려사항

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 다음 고려사항을 검토하십시오.

* 인스턴스의 기본 클러스터에서 IBM Spectrum Protect Plus 가상 머신에 충분한 CPU 및 메모리가 있는지 확인하십시오.
* ESXi 서버의 버전에 따라 ESXi 서버에 사용 가능한 NFS 마운트가 충분한지 확인하십시오.

  V2.2 이상 릴리스로 배치된(또는 이러한 릴리스로 업그레이드된) Cloud Foundation 인스턴스 및 vCenter Server 인스턴스에는 VMware의 `NFS.MaxVolumes` 매개변수 설정이 있습니다. 이 매개변수는 ESXi 서버에서 최대 NFS 마운트 수를 정의하고 ESXi 서버의 버전에 특정한 최대 256의 값으로 설정될 수 있습니다. 자세한 정보는 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239)를 참조하십시오.

  IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스는 인스턴스의 기본 클러스터의 각 ESXi 서버에서 최대 11개의 NFS 볼륨을 사용할 수 있습니다. 또한 서비스는 백업 및 복원을 위해 임시 NFS 마운트를 작성합니다. 그러므로 서비스를 설치하고 작동할 수 있도록 NFS 마운트 수를 최소 64의 값으로 설정해야 합니다.

## IBM Spectrum Protect Plus on IBM Cloud 제거 시 고려사항

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* 모든 백업 작업 구성이 활성 백업 또는 복원 오퍼레이션과 함께 제거되었는지 확인하십시오.
* 서비스를 제거하는 경우 백업 저장소의 스토리지가 IBM Spectrum Protect Plus VM에서 제거되고 백업 저장소 데이터를 영구적으로 삭제하는 스토리지 주문이 취소됩니다.
* 서비스를 제거하는 경우 서비스에 대해 주문된 백업 스토리지도 제거됩니다. 서비스 제거 중에 모든 백업에 액세스할 수 없습니다.

### 관련 링크

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service 계획](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 관리](managingspp.html)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 주문](spp_ordering.html)
* [IBM Spectrum Protect Plus 문서](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

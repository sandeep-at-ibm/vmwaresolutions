---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Cloud Foundation 인스턴스에 대한 다중 사이트 구성

{{site.data.keyword.vmwaresolutions_full}}를 사용하여 다른 위치에 인스턴스를 배치할 수 있고 짧은 시간 동안 시작하고 실행할 수 있습니다.

**참고**:
* 다중 사이트 구성에서 VMware Cloud Foundation과 VMware vCenter Server 인스턴스를 연결할 수 없습니다.
* 이전 릴리스의 인스턴스로 V2.0에 배치된 인스턴스를 연결할 수 없습니다(이전 릴리스가 V2.0으로 업그레이드된 경우에도 해당).


## 다중 사이트 배치 컴포넌트

다중 사이트 배치는 다음 컴포넌트로 구성됩니다.

* **기본 인스턴스**: 기본 VMware Cloud Foundation 인스턴스의 구성은 다음과 같습니다.
  *  Microsoft Active Directory(AD) 및 DNS(Domain Name System) 루트 도메인
  *  Cloud Foundation 하위 도메인
  *  SSO(Single Sign-On) 도메인
  *  SSO 사이트 이름
* **보조 인스턴스**: 기본 인스턴스에 연결된 하나 이상의 보조 Cloud Foundation 인스턴스의 구성은 다음과 같습니다.
   *  SSO 사이트 이름
   *  기본 인스턴스의 루트 도메인에 연결된 DNS 하위 도메인
   *  DNS 및 AD 복제가 기본 및 보조 인스턴스의 AD 가상 머신 사이에 설정됨
   *  기본 인스턴스의 PSC(Platform Services Controller)로 복제하도록 배치되고 구성된 PSC
   *  보조 인스턴스의 VMware vCenter가 기본 인스턴스에서 vCenter에 대한 향상된 연결 모드로 설정됨

## Cloud Foundation 다중 사이트 배치

다중 사이트 구성 기능은 기본 사이트와 최대 일곱 개의 보조 사이트로 허브 및 스포크 토폴로지를 사용합니다. 단일 사이트 계층이 지원되며, 이는 다른 보조 사이트에 연결된 후속 사이트를 구성할 수 없음을 의미합니다. 모든 인스턴스의 다중 사이트 구성에서 총 128개의 ESXi 서버를 보유할 수 있습니다.

**참고**: 구성에서 128개를 초과하는 ESXi 서버가 포함된 다중 사이트 배치가 필요한 경우 IBM 지원 센터에 문의하여 도움을 받으십시오. 자세한 정보는 [IBM 지원 센터에 문의](../vmonic/trbl_support.html)를 참조하십시오.

다음 그림은 Cloud Foundation 다중 사이트 배치의 전체 보기에 대해 설명합니다.

그림 1. Cloud Foundation 다중 사이트 배치

![Cloud Foundation 다중 사이트 배치](multisite-hub-spoke.svg "Cloud Foundation 다중 사이트 배치")

모델에는 다음 계층이 포함됩니다.

* **기본 인스턴스**: 다중 사이트 구성에서 첫 번째 인스턴스를 배치하기 위해 인스턴스 주문 프로세스 중에 인스턴스를 기본 인스턴스로 정의합니다.
* **보조 인스턴스**: 다중 사이트 구성에서 주문 프로세스 중에 기본 인스턴스에 연결된 인스턴스를 보조 인스턴스로 정의합니다.

한 번에 하나의 보조 인스턴스만 기본 인스턴스에 지정할 수 있습니다. 동시에 다중 보조 인스턴스를 기본 인스턴스에 지정할 수 없습니다. 이를 수행하려면 주문 프로세스를 다시 수행하고 보조 인스턴스를 위해 기본 인스턴스로 이전에 정의한 기본 인스턴스를 선택해야 합니다. 작성할 모든 보조 인스턴스에 대한 프로세스를 반복해야 합니다.

다중 사이트 구성에 배치된 최대 8개의(1개의 기본 및 7개의 보조) 인스턴스를 보유할 수 있습니다.

**참고**: 다중 사이트 구성의 일부인 Cloud Foundation 인스턴스를 삭제하려면 특수 계획이 필요합니다. 자세한 정보는 [다중 사이트 구성에서 Cloud Foundation 인스턴스 삭제](sd_deletinginstance_multi.html)를 참조하십시오.

### 관련 링크

* [Assign Primary Role to NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [Configuring Secondary NSX Managers](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/kb/2064250){:new_window}
* [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}

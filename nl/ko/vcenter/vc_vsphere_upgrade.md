---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-07"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server vSphere 소프트웨어를 VMware vSphere 6.5에서 6.7로 업그레이드
{: #vc_vsphere_upgrade}

vCenter Server on {{site.data.keyword.cloud}} 오퍼링은 vSphere, NSX 및 vSAN 제품(선택사항)을 포함하여 VMware vSphere SDDC 스택에 맞게 완전히 자동화된 배치 솔루션입니다. vCenter Server가 VMware SDDC 기반 인프라를 배치하고, 확장하고, 축소하는 가장 어려운 부분을 자동화하지만 이는 관리 서비스가 아닙니다. vCenter Server에 VMware SDDC 소프트웨어 버전(N-1 범위 내)의 자동화를 지원하는 정책이 있음에 따라 {{site.data.keyword.vmwaresolutions_short}}의 자동화 이점을 계속해서 활용하려면 기존 vCenter Server의 인스턴스를 업그레이드해야 합니다.

자동화 지원에 필요한 레벨이 아닌 vCenter Server 버전은 VMware 지원 정책의 필요에 따라 계속해서 지원되지만 {{site.data.keyword.vmwaresolutions_short}} 자동화에 계속해서 작동되지는 않습니다. vCenter Server 인스턴스의 라이프사이클 동안 VMware 소프트웨어의 패치 및 업그레이드를 지속적으로 수행해야 합니다. 여기에는 필요에 따라 {{site.data.keyword.vmwaresolutions_short}} 자동화에서 지원하는 버전으로의 VMware SDDC 소프트웨어 업그레이드가 포함됩니다.

다음 프로시저는 vCenter Server VMware vSphere 6.5 기반 인스턴스를 vCenter Server VMware vSphere 6.7 기반 인스턴스로 변환하는 데 필요한 단계를 제공합니다. 이 단계에서는 vSphere, NSX 및 vSAN의 최신 6.7 레벨에 대한 초기 업그레이드를 제공합니다. 이 업그레이드 후에는 가상 머신(VM) 하드웨어 레벨 및 도구로 업그레이드하기 위해 일반적인 vSphere 기능을 사용해야 할 수 있습니다.

vCenter Server는 "롤링" 업그레이드를 허용하도록 설계되었습니다. 즉, 다음 프로시저를 완료하면 현재 작동 중인 VM 워크로드는 중단 없이 계속해서 작동합니다. 엔터프라이즈는 예기치 못한 상황에 대비하여 구조화되고 전달된 업그레이드 및 플랜이 사용 가능하도록 변경 관리 정책을 포함해야 합니다. 그러나 vCenter 및 NSX 관리자와 같은 특정 관리 기능의 업그레이드 프로세스 중에 관리 기능의 일시적인 작동 중지, 구성 변경, VM 전원 켜기 및 끄기에 영향을 미칠 수 있습니다.
{:note}

## 시작하기 전에
{: #vc_vsphere_upgrade-prereq}

업그레이드를 수행하는 데 필요한 예상 시간을 알 수 없습니다. 환경을 완전히 업그레이드하려면 여러 유지보수 기간이 필요할 수 있습니다. 업그레이드 프로세스 중에 VMware에서 SDDC 소프트웨어의 상위 레벨 버전 및 하위 레벨 버전을 실행할 수 있도록 지원합니다. 그러나 이 프로세스 중에 vMotion과 같은 일부 기능이 제한될 수 있습니다.

업그레이드를 시작하기 전에 다음 요구사항을 완료하십시오.  
* 사용자는 vCenter Server 환경에서 확장 또는 스냅인을 업그레이드해야 합니다. 업그레이드를 계획하려면 다음 문서를 검토하십시오.
  * [VMware vCenter Server 6.7 Update 1b 릴리스 정보](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [VMware ESXi 업그레이드 정보](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* vCenter Server 인스턴스 내의 VUM(vSphere Update Manager)을 설정하여 VMware vSphere에서 최신 업데이트를 다운로드하십시오. 자세한 정보는 [VMware Update Manager 소개](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro)를 참조하십시오.
*	업그레이드가 수행 중임을 알리려면 {{site.data.keyword.vmwaresolutions_short}} 팀을 통해 지원 티켓을 여십시오. 티켓은 인스턴스가 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 업그레이드된 레벨로 등록될 때까지 열려 있습니다.
* 업그레이드 중인 vCenter Server 인스턴스가 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 기본 또는 보조로서 다른 vCenter Server 인스턴스에 연결되는지 여부를 확인하십시오. 연결된 모든 인스턴스에서는 특정 사이트 업그레이드 일부로 먼저 PSC(Platform Services Controllers)를 업그레이드해야 합니다.
* 다음 vSAN 기반 인스턴스를 확인하십시오.
  * vSAN 상태 도구가 사용 가능한지와 중요한 오류를 보고하지 않는지 확인하십시오. 중요한 오류가 발생한 경우 업그레이드 지원 티켓 ID를 사용하여 IBM 지원 센터에 문의하십시오.
  * ESXi 호스트가 업그레이드 중에 다시 작동하는 데 실패하는 경우 vSAN 오브젝트의 중복된 다시 빌드를 처리할 수 있도록 각 노드에 공간이 있는지 확인하십시오. 업그레이드 전에 디스크 사용량을 줄이거나 추가 ESXi 호스트를 추가해야 할 수 있습니다.  
  * 전체 vSAN 볼륨의 활용률이 70%를 초과하는지 여부를 확인하십시오. 업그레이드 전에 디스크 사용량을 줄이거나 추가 ESXi 호스트를 추가해야 할 수 있습니다.
* **customerroot** 액세스 권한이 있는 서비스 계정만 포털에 표시됨에 따라 vCenter Server 인스턴스가 {{site.data.keyword.vmwaresolutions_short}} V2.5 이상에서 실행된 경우 PSC 및 vCenter의 **root** 사용자 ID 비밀번호를 찾으려면 IBM 지원 센터에 문의해야 합니다. 해당 비밀번호를 사용하여 PSC 및 vCenter **root** 사용자 ID가 표시되는 경우 이 단계는 필요하지 않습니다.
* 필요한 업그레이드 바이너리를 다운로드하려면 https://my.vmware.com의 사용자 ID가 있는지 확인하십시오. 사용자 ID가 없으면 업그레이드 지원 티켓 ID를 사용하여 IBM 지원 센터에 문의하십시오.
* 패치를 다운로드하려면 https://www.vmware.com에 연결할 수 있도록 VUM이 구성되어 있는지 확인하십시오. 보안 정책으로 인해 구성될 수 없는 경우 수동으로 최신 패치 세트를 다운로드하고 VUM에 업로드해야 합니다. 자세한 정보는 [VMware Update Manager 소개](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)를 참조하십시오.

### 점프 박스 준비
{: #vc_vsphere_upgrade-prereq-jumpbox}

{{site.data.keyword.cloud_notm}} 클라이언트 액세스 VPN이 512Kbps로 제한됨에 따라 {{site.data.keyword.cloud_notm}} Windows 2012 - 2016 서버 VSI(Virtual Server Instance)를 프로비저닝하거나 동일한 {{site.data.keyword.CloudDataCent_notm}} 내의 개별 vSphere vCenter Server 환경에 유사한 Windows VM을 설정하는 것이 좋습니다. 이는 업그레이드할 vCenter Server 인스턴스에 대한 점프 박스로 사용되며 바이너리를 위해 https://my.vmware.com에서 빠르게 다운로드할 수 있습니다. 업그레이드 중인 vCenter Serve 인스턴스에 이 VM을 배치할 수 있지만 권장사항은 아닙니다.

VSI 점프 박스를 주문하려면 다음 단계를 완료하십시오.

사용자 환경에 VSI 점프 박스가 이미 설치되어 있으면 첫 번째 단계를 건너뛰십시오.
{:note}

1. [IBM Cloud 인프라 고객 포털](https://control.softlayer.com/)에서 시간별 또는 월별 VSI를 주문하십시오. 다음 속성을 주문하십시오.
  * Windows 2012 또는 2016 Server Standard
  * 2개의 CPU
  * 16GB 메모리
  * 100G 디스크
  * 1Gbps 공용 및 사설 업링크
2. VSI가 프로비저닝된 경우 사설 링크에서 모든 유입 및 유출을 허용하고 공용 링크에서 유출만 허용하도록 제어 패널에서 {{site.data.keyword.cloud_notm}} Access Control Lists(ACL)를 구성하십시오. Windows VSI에 대한 RDP(Remote Desktop Protocol) 세션용 {{site.data.keyword.cloud_notm}} 클라이언트 액세스 VPN을 사용해야 합니다.
3. Windows VSI에 대한 RDP를 사용하십시오. 업그레이드할 vCenter Server 인스턴스 내에서 Windows AD 서버만 지정하도록 사설 네트워크 어댑터에서 DNS(Domain Name System) 설정을 수정하십시오.
4. Google Chrome 브라우저를 다운로드하여 설치하십시오. Mozilla Firefox를 사용할 수 있지만 vCenter 사용자 인터페이스 내에서 VUM 화면을 사용할 때 캐시 문제가 발생합니다.
5. 원하는 SSH 터미널 소프트웨어를 다운로드하십시오. 예를 들면, Putty입니다.
6. Google Chrome을 사용하여 업데이트할 vCenter Server 인스턴스에 액세스하십시오. **administrator@vsphere.local**을 사용하고 사용자 인터페이스를 볼 수 있는지 확인하십시오.  
7. 이전 절에서 설명된 대로 오류 및 문제를 보려면 vSphere 환경을 확인하십시오.
8. SSH 터미널 소프트웨어를 사용하여 포털 또는 지원 센터에서 제공하는 **root**의 비밀번호를 통해 PSC 및 vCenter에 액세스하십시오.
9. 선택적으로 **root** 비밀번호를 확인하려면 SL 제어 패널에 표시된 **root** 사용자 ID 및 비밀번호를 사용하여 각 ESXi 호스트에 액세스하십시오.

#### 바이너리 다운로드
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Windows VSI 점프 박스를 사용하고 https://my.vmware.com 계정에 로그인하여 다음 바이너리를 다운로드하십시오.

*	VMware vSphere 6.7u1 Hypervisor(ESXi ISO) 이미지(VMware Tools 포함)
* vCenter 6.7u1b 어플라이언스 ISO. 업데이트 번들이 아닙니다.
*	NSX for vSphere 6.4.4 업그레이드 번들

Optane 드라이브의 경우 다음 파일을 다운로드하여 VMware Update Manager를 활용하는 사후 업그레이드 패치 프로세스의 일부로 사용하십시오.

https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742에서 Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA(750 GB, HHHL)의 Intel NVMe 드라이브에 맞는 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 파일을 찾으십시오.

#### 컴포넌트 백업

업그레이드를 시작하기 전에 각 컴포넌트를 백업하십시오.

* vCenter Server 및 PSC 백업에 대한 정보는 [ vCenter Server 6.x(2149237)의 백업 및 복원 옵션 개요](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}를 참조하십시오.
* vCenter Server 및 PSC 백업에 대한 추가 고려사항 및 정보는 [vCenter 파일 기반 백업](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter)을 참조하십시오.
*	NSX 백업에 대한 정보는 [NSX Manager 데이터 백업](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}을 참조하십시오.

파일 기반 백업을 사용하는 것이 좋습니다. VMware vSphere 6.7에서는 이미지 기반 백업(vSphere Data Protection 사용)이 지원되지 않습니다.
{:note}

## IBM vCenter Server vSphere 소프트웨어를 6.5에서 6.7로 업그레이드하는 프로시저
{: #vc_vsphere_upgrade-procedure}

업그레이드 프로세스 중에 언제라도 문제가 발생하면 프로세스 시작 시 열었던 {{site.data.keyword.vmwaresolutions_short}} 업그레이드 티켓을 사용하여 IBM 지원 센터에 문의하십시오. IBM 지원 센터는 필요에 따라 VMware 지원을 사용하여 티켓을 엽니다.

**중요**:

* 이 경로를 사용하여 {{site.data.keyword.vmwaresolutions_short}}가 vCenter Server 디자인, 설정에 대해 필요한 모든 정보와 {{site.data.keyword.cloud_notm}} 정보를 사용하여 VMware 지원을 제공하는지 확인해야 합니다. 정확한 정보가 VMware 지원과 공유되는지 확인하기 위해 이 프로세스를 수행하면 지원 경험을 줄일 수 있습니다. IBM 지원 센터에서 필요한 정보를 VMware 지원에 제공한 후 필요에 따라 VMware 지원과 직접적으로 상호작용할 수 있습니다.
* 이 업그레이드 프로세스의 일부로 작성하는 새 비밀번호 및 인증 정보를 모두 기록해 두십시오. IBM 지원 센터에서는 내부 데이터베이스를 업데이트하기 위해 업그레이드 프로세스가 끝날 때 이러한 인증 정보가 필요합니다.

### VMware NSX 업그레이드
{: #vc_vsphere_upgrade-procedure-nsx}

업그레이드 프로세스를 실행하면 ESXi 호스트의 vSphere 설치 번들이 업데이트되고 각 호스트를 다시 부팅해야 하므로 VMware NSX 업그레이드에는 약간의 시간이 소요될 수 있습니다. 따라서 유지보수 기간을 적절하게 계획하십시오.

#### VMware NSX를 업그레이드하기 전에
{: #vc_vsphere_upgrade-procedure-nsx-before}

* 사용자 환경에 Zerto for {{site.data.keyword.cloud_notm}}가 설치된 경우 Zerto 사용자 인터페이스를 사용하여 각 호스트에서 zVRA를 종료하십시오. Zerto 사용자 인터페이스의 Zerto 사이트 설정, 정책 섹션 내에서 **Zerto가 항상 조치방안 중에 호스트를 유지보수 모드로 전환하도록 허용**을 선택하십시오. 그렇지 않으면 Zerto에서 zVRA를 시작하고 ESXi 호스트가 유지보수 모드로 전환되도록 업그레이드하는 것을 허용하지 않은 상태에서 업그레이드가 계속 진행됩니다.
* VMware 도구가 설치되지 않은 VM의 경우 NSX ESXi 호스트 모듈을 설치하기 전에 수동으로 종료하거나 강제로 전원을 끄십시오. 이 VM은 대상 ESXi 호스트가 유지보수 모드로 전환되지 않도록 합니다.

#### VMware NSX를 업그레이드하는 프로시저
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

다음 프로시저와 관련된 자세한 내용은 [NSX 업그레이드 안내서](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}를 참조하십시오.

1. 특정 환경 구성과의 호환성을 확인하려면 NSX 6.4.4에 대한 릴리스 정보를 읽으십시오. 자세한 정보는 [VMware NSX Data Center for vSphere 6.4.4 릴리스 정보](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}를 참조하십시오.
2. 먼저 NSX 관리자를 업그레이드하십시오. 교차 vCenter 연결 모드를 사용하는 다중 NSX 환경을 보유하고 있는 경우 NSX 사용자 인터페이스 **조정자 업그레이드**에서 컴포넌트를 업그레이드하기 전에 모든 NSX 관리자를 업그레이드하십시오.
3.	NSX 컴포넌트를 업그레이드하려면 vCenter 사용자 인터페이스 내의 NSX 사용자 인터페이스에서 **조정자 업그레이드**를 사용하십시오.
4. 발생 가능한 문제가 해결되면 모든 컴포넌트가 업그레이드될 때까지 업그레이드가 진행되는지 확인하기 위해 vCenter 사용자 인터페이스 내의 NSX 업그레이드 사용자 인터페이스를 계속해서 검토하고 모니터하십시오.

### Platform Services Controller 업그레이드
{: #vc_vsphere_upgrade-procedure-psc}

vCenter Server가 인스턴스에 연결된 경우 vCenter Server 기본 및 보조 사이트에서 모든 PSC 인스턴스를 업그레이드해야 합니다. 연결된 vCenter Server 인스턴스에서 허브 및 스포크 PSC 복제(기본 vCenter Server 인스턴스가 허브임)를 작성하므로 기본 vCenter Server 인스턴스 PSC를 업그레이드한 후 각 보조 사이트 PSC를 업그레이드하여 시작하는 것이 좋습니다.

#### Platform Services Controller를 업그레이드하기 전에
{: #vc_vsphere_upgrade-procedure-psc-before}

* vCenter 및 PSC 루트 비밀번호를 다음 프로시저에서 사용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여 vCenter Server 인스턴스 버전이 V2.4 이전부터 V2.7 이후까지 업그레이드되는지 여부를 확인하십시오.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 PSC 및 vCenter의 루트 비밀번호로 하나의 비밀번호가 표시됩니다. 그러나 이 비밀번호는 vCenter 전용입니다. 루트 PSC 비밀번호는 지원 센터에 문의해야 합니다.
* 충돌을 피하려면 vCenter 및 PSC가 현재 사용 중인 동일한 서브넷의 상단에 IP를 사용하십시오. 새 어플라이언스 배치를 위해 임시 IP를 사용해야 합니다.

#### Platform Services Controller를 업그레이드하는 프로시저
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. ``https://<psc-fqdn>:5480``에서 PSC 및 vCenter 어플라이언스 관리 사용자 인터페이스에 로그인하여 루트 비밀번호의 만료 여부를 확인하십시오. 비밀번호 만기 날짜의 연도가 **1970**인 경우 만료되었음에 따라 PSC 어플라이언스 관리 사용자 인터페이스에서 SSH 및 bash 쉘을 사용으로 설정해야 합니다.
    1. 루트 ID 및 비밀번호를 사용하여 PSC에 SSH로 연결하십시오. 비밀번호가 만료된 경우에도 로그인할 수 있습니다.
    2. 쉘 **passwd** 명령을 사용하여 PSC 및 vCenter의 새 루트 비밀번호를 설정하십시오.
    3. {{site.data.keyword.vmwaresolutions_short}} 콘솔에 표시되거나 IBM 지원 센터에서 제공한 비밀번호를 저장하십시오. 어플라이언스를 업그레이드하면 나중에 이 비밀번호가 다시 사용됩니다.
2. 기본 제공 Windows ISO 마운트 기능을 사용하여 점프 박스 내에서 vCenter 6.7u1b ISO를 마운트하십시오.
3. 먼저 VMware 지시사항에 따라 모든 PSC를 업그레이드하십시오. 자세한 정보는 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html)를 참조하십시오.

**업그레이드할 어플라이언스와 동일한 네트워크에 있는 Windows, Linux 또는 Mac 머신에서 GUI 업그레이드를 실행해야 함**이라는 요구사항이 사용자 계정의 {{site.data.keyword.cloud_notm}} 내의 모든 서브넷에 적용됩니다.
{:note}

업그레이드하려면 소스 및 대상으로 vCenter를 사용하는 것이 좋습니다.

### vCenter 업그레이드
{: #vc_vsphere_upgrade-procedure-vcenter}

vCenter Server가 인스턴스에 연결된 경우 vCenter Server 기본 보조 사이트에서 모든 vCenter 인스턴스를 업그레이드하는 것이 권장되지만 필수 사항은 아닙니다.

#### vCenter를 업그레이드하기 전에
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* vCenter 및 PSC 루트 비밀번호를 다음 프로시저에서 사용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여 vCenter Server 인스턴스 버전이 V2.4 이전부터 V2.7 이후까지 업그레이드되는지 여부를 확인하십시오.
* 충돌을 피하려면 vCenter 및 PSC가 현재 사용 중인 동일한 서브넷의 상단에 IP를 사용하십시오. 새 어플라이언스 배치를 위해 임시 IP를 사용해야 합니다.

#### vCenter를 업그레이드하는 프로시저
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. ``https://<psc-fqdn>:5480``에서 PSC 및 vCenter 어플라이언스 관리 사용자 인터페이스에 로그인하여 루트 비밀번호의 만료 여부를 확인하십시오. 비밀번호 만기 날짜의 연도가 **1970**인 경우 만료되었음에 따라 PSC 어플라이언스 관리 사용자 인터페이스에서 SSH 및 bash 쉘을 사용으로 설정해야 합니다.
    1. 루트 ID 및 비밀번호를 사용하여 PSC에 SSH로 연결하십시오. 비밀번호가 만료된 경우에도 로그인할 수 있습니다.
    2. 쉘 **passwd** 명령을 사용하여 PSC 및 vCenter의 새 루트 비밀번호를 설정하십시오.
    3. {{site.data.keyword.vmwaresolutions_short}} 콘솔에 표시되거나 IBM 지원 센터에서 제공한 비밀번호를 저장하십시오. 어플라이언스를 업그레이드하면 나중에 이 비밀번호가 다시 사용됩니다.
2. 기본 제공 Windows ISO 마운트 기능을 사용하여 점프 박스 내에서 vCenter 6.7u1b ISO를 마운트하십시오.
3. VMware 지시사항에 따라 vCenter를 업그레이드하십시오. 자세한 정보는 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html)를 참조하십시오. VMware 지시사항은 PSC의 업그레이드 프로세스와 유사합니다. 그러나 PSC를 가리키는 대신 업그레이드 프로세스의 경우 vCenter FQDN/IP를 가리킵니다.

**참고**:
* **업그레이드할 어플라이언스와 동일한 네트워크에 있는 Windows, Linux 또는 Mac 머신에서 GUI 업그레이드를 실행해야 함**이라는 요구사항이 사용자 계정의 {{site.data.keyword.cloud_notm}} 내의 모든 서브넷에 적용됩니다.
* 업그레이드하려면 소스 및 대상으로 vCenter를 사용하는 것이 좋습니다.

#### PSC 기능을 vCenter에 통합

1. PSC 및 vCenter의 업그레이드를 완료한 후 vCenter FLEX 기반 사용자 인터페이스에 로그인하고 **시스템 구성** 섹션에서 vCenter 및 PSC와 연관된 모든 서비스의 상태를 확인하십시오.  
2. PSC를 백업하십시오.  파일 기반 백업을 사용하는 것이 좋습니다. 자세한 정보는 [vSphere 6.7의 파일 기반 백업](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:new_window}을 참조하십시오.
3. ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge`` 디렉토리로 이동하십시오.
4. ``converge.json`` 파일을 점프 VM의 로컬 드라이브에 복사하십시오.
  * 통합하는 첫 번째 PSC인 경우 ``json`` 파일에서 **replication** 섹션을 제거해야 합니다.
  * 그 다음 연결된 PSC인 경우 ``json`` 파일의 **replication** 섹션에 요청된 속성을 채워야 합니다.
5. ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission`` 디렉토리로 이동하십시오.
6. ``decommission_psc.json`` 파일을 점프 VM의 로컬 드라이브에 복사하십시오.
7. ``converge.json`` 및 ``decommission_psc.json`` 파일을 편집하십시오. 편집할 필드에 대한 지시사항은 ``json`` 파일에 있습니다. **managing_esxi_or_vc** 섹션의 vCenter가 아닌 PSC가 포함된 ESXi 호스트가 사용되는 것이 좋습니다.
8. 명령 창에서 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 디렉토리로 이동하십시오.
9. **converge** 스위치와 이전에 편집한 ``converge.json`` 파일에 대한 경로를 사용하여 ``vcsa-util.exe``를 실행하십시오. 예를 들면, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``입니다.
   1. PSC가 백업되었는지 확인하려면 **Y**를 입력하여 계속 진행하십시오.
   2. 프로세스가 완료된 경우 vCenter의 다시 부팅을 확인하려면 **Y**를 입력하십시오.

   통합 프로세스가 ``ERROR converge Failed to get vecs users and permissions`` 메시지와 함께 실패하는 경우 오류를 해결하기 위한 단계는 [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:new_window}를 참조하십시오.
   {:note}

10. vCenter가 다시 부팅된 후 vCenter 사용자 인터페이스에 로그인하여 정상적으로 작동하는지 확인하십시오.
11. 명령 창에서 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 디렉토리로 이동하십시오.
12. ``decommission`` 스위치와 이전에 편집한 **converge.json** 파일에 대한 경로를 사용하여 ``vcsa-util.exe``를 실행하십시오. 예를 들면, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``입니다.
13.	명령이 완료되면 vCenter Flex 사용자 인터페이스에 로그인하고 vCenter 어플라이언스가 연결되지 않은 환경에 나열된 유일한 항목이며 모든 서비스가 양호한 상태임을 확인하십시오.
14. 이전 PSC, vCenter 및 사용되지 않은 통합된 PSC VM을 삭제하십시오.
15. vCenter 사용자 인터페이스 내 vCenter Server의 이름을 **<instancename>_vc_separate**로 변경하십시오. 예를 들어, vCenter Server 인스턴스 이름이 **production**이면 vCenter 사용자 인터페이스 이름이 **production_vc_separate**입니다. 이는 필수 항목이므로 자동화를 통해 이 vCenter Server 인스턴스에 맞는 해당 기능이 재개될 수 있습니다.  

### ESXi 호스트 업그레이드
{: #vc_vsphere_upgrade-procedure-esxi}

vCenter 내의 VMware Update Manager 기능은 ESXi 호스트를 6.7u1 레벨로 업그레이드하고 패치하는 데 활용됩니다. 이 문서의 NSX 업그레이드 절과 유사하게, 다른 호스트로 vMotion하지 않을 수 있는 모든 VM은 문제 없이 종료되어야 합니다. 그렇지 않으면 이로 인해 업그레이드 프로세스가 정지될 수 있습니다.
{:note}

#### ESXi ISO를 VUM으로 업로드
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. https://www.vmware.com에서 패치를 다운로드하도록 VUM이 구성되었는지 확인하십시오. 자세한 정보는 [VMware Update Manager 소개](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction)를 참조하십시오.
2. Flex 또는 HTML을 사용하여 vCenter 사용자 인터페이스를 열고 **VUM 관리자 보기**로 이동하십시오.
3. **VUM 관리자 보기**에서 **ESXi 이미지** 탭을 선택하고 **ESXi 이미지 가져오기**를 선택하십시오.
4. VMware에서 다운로드한 **ESXi 6.7u1iso** 이미지를 찾아 이를 VUM 저장소로 가져오십시오.

#### ESXi 호스트를 업그레이드하는 프로시저
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. vCenter 사용자 인터페이스에서, 업그레이드할 ESXi 호스트가 포함된 클러스터로 이동하십시오.
2. 탐색 패널에서 **업데이트** 탭을 클릭하십시오. 호스트 업데이트로 이동하여 **연결**을 클릭하십시오.
3. VUM에 업로드한 기준선(ESXi 업그레이드를 위한 ISO 이미지)을 선택하고 **수정**을 클릭하십시오.
4. 일반 사용자 라이센스 계약에 동의하고 **확인**을 클릭하십시오.
5. 수정될 호스트를 검토하고 사전 수정 검사 결과를 확인하십시오.

   VM에 연결된 CD 또는 DVD를 분리해야 합니다. 그렇지 않으면 해당 VM이 포함된 호스트가 유지보수 모드로 전환될 수 없습니다.
   {:note}

6. 사전 수정 검사에 성공한 후 **수정**을 클릭하십시오. 엔티티 수정 태스크를 사용하여 업그레이드 프로세스를 모니터하십시오.
7. 업그레이드가 완료된 후 호스트의 요약 섹션을 검토하여 ``VMware ESXi, 6.7.0``이 표시되는지 확인하십시오.

업그레이드 프로세스가 즉시 실패하고 **호스트가 유지보수 모드로 전환될 수 없음** 오류 메시지가 표시되는 경우 Zerto ZVA를 종료하고 다시 시도하십시오. 각 서버의 수정이 완료되면 ZVRA VM이 자동으로 시작됩니다. 업그레이드 프로세스 중에 Zerto 복제 진행에 대한 자세한 정보는 [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}를 참조하십시오.
{:note}

#### Intel NVME 드라이버 패치를 VUM 저장소에 추가
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

바이너리 다운로드 섹션에 설명된 대로 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 파일의 컨텐츠를 저장소로 가져와야 합니다. 그런 다음 이는 중요하지 않은 ESXi 호스트 확장으로 후속 섹션에 적용됩니다.

1. ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 파일을 점프 VM의 로컬 드라이브로 추출하십시오.
2. Flex 또는 HTML을 사용하여 vCenter 사용자 인터페이스를 열고 **VUM 관리자 보기**로 이동하십시오.
3. **VUM 관리자 보기**에서 **패치 저장소** 탭을 선택하고 **패치 가져오기**를 선택하십시오.
4. ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 디렉토리의 추출된 컨텐츠를 찾아 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` 파일을 선택하십시오. 파일을 VUM 저장소로 즉시 가져옵니다.

패치 저장소에서**important** 호스트 확장으로  이미지를 찾으십시오.

#### ESXi 호스트 패치
{: #vc_vsphere_upgrade-procedure-esxi-patch}

중요하고 중요하지 않은 모든 ESXi 호스트 패치를 적용하도록 사후 업그레이드를 수행하는 것이 좋습니다.

1. vCenter 사용자 인터페이스에서 패치될 호스트가 포함된 클러스터를 선택하십시오. 
2. 탐색 패널에서 **업데이트** 탭을 클릭하고 **호스트 업데이트** 탭을 선택하십시오. **중요 호스트 패치(사전 정의됨)**를 선택하십시오. ESXi 호스트를 업그레이드하는 프로시저를 반복하십시오
3. 탐색 패널에서 **업데이트** 탭을 클릭하고 **호스트 업데이트** 탭을 선택하십시오. **중요하지 않은 호스트 패치(사전 정의됨)**를 선택하십시오. ESXi 호스트를 업그레이드하는 프로시저를 반복하십시오

이 프로세스의 일부로 다시 Zerto zVRA VM을 종료해야 할 수 있습니다.
{:note}

### 추가 항목 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl}

#### vSAN On Disk Format 버전 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

vSAN Disk Format 버전을 버전 7로 업그레이드하십시오.

1. vCenter 사용자 인터페이스를 업그레이드하려면 vSAN이 포함된 클러스터로 이동하십시오.
2. 클러스터 오브젝트에서 **구성 > vSAN > 일반**을 선택하십시오.
3. **업그레이드 사전 확인**을 클릭하여 업그레이드 호환성 및 발생 가능한 문제를 확인하십시오. 확인하여 **업그레이드할 준비가 됨...**을 리턴할 때까지 기다리십시오.
4. **업그레이드**를 클릭하십시오. 업그레이드 시 한 번에 디스크 그룹을 처리하므로 완료하는 데 약간의 시간이 소요될 수 있으며 클러스터의 크기에 따라 달라질 수 있습니다. 선택적으로 프로세스 중에 **감소된 중복성**을 선택하십시오. 이를 통해 업그레이드하는 데 소요되는 시간을 상당히 줄일 수 있으나 업그레이드 프로세스 중에 디스크 실패가 발생한 경우 데이터 손실이 발생할 수 있습니다.

#### 가상 분배 스위치 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl-vds}

가상 분배 스위치(VDS)를 v6.6.0으로 업그레이드하면 네트워크 I/O 제어가 업그레이드되고 향상된 LACP(Link Aggregation Control Protocol) 지원도 추가됩니다.

1.	HCX를 배치한 경우 HCX가 상주하는 VDS를 업그레이드하기 전에 HCX의 클라우드 게이트웨이 부분을 배치 취소해야 합니다. 클라우드 게이트웨이를 다시 배치하기 전에 HCX가 최신 버전으로 업데이트되었는지 확인하십시오.
2.	vCenter 사용자 인터페이스에서 **네트워크** 탭으로 이동하십시오.
3.	분배 스위치를 마우스 오른쪽 단추로 클릭하여 업그레이드하고(**SDDC-Dswitch-Private** 또는 **SDDC-Dswitch-Public** 중 하나) **분배 스위치 업그레이드**를 선택하십시오.

#### vCenter 사용자 인터페이스 확장 및 플러그인 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl-extension}

사용자는 vCenter Server 환경에서 확장 또는 스냅인을 업그레이드해야 합니다. vCenter 사용자 인터페이스에서 **Home > 관리 > 솔루션**을 클릭하여 vCenter 확장 및 플러그인을 사용 또는 사용 안함으로 설정하십시오.

#### VMware 도구 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl-tools}

vCenter 사용자 인터페이스를 사용하여 VMware 게스트 도구 업그레이드를 수행하십시오. 일부 VMware 도구는 vCenter Server 환경으로 마이그레이션된 일부 이전 VM에서 필요할 수 있습니다.  

#### 가상 머신 하드웨어 레벨 업그레이드
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

VMware 게스트 도구와 유사하게 vCenter Server 환경 업그레이드로 인해 현재 하드웨어 레벨에서 이전 VM이 지원되지 않은 상태가 될 수 있습니다. vCenter 사용자 인터페이스를 사용하여 필요에 따라 이 VM을 찾아 업데이트하십시오.  

#### EVC(Enhanced vMotion Compatibility) 모드를 Intel Skylake로 설정
{: #vc_vsphere_upgrade-procedure-addtl-evc}

업그레이드 후 클러스터용 Intel Skylake 세대가 있는 호스트를 Skylake EVC(Enhanced vMotion Compatibility) 모드로 설정할 수 있습니다. EVC 모드를 업데이트하려면 다음 단계를 사용하십시오.

1. 호스트가 포함된 클러스터에서 **구성**을 클릭하십시오.
2. **VMware EVC**에서 **편집**을 클릭하고 EVC 모드를 **Intel "Skylake" 세대**로 변경하십시오.

자세한 정보는 [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:new_window}를 참조하십시오.

#### PSC를 가리키도록 NSX Manager 및 HCX Manager 재구성

1. 웹 브라우저에서 ``https://<nsx-manager-ip>`` 또는 ``https://<nsx-manager-hostname>``의 NSX Manager 어플라이언스 사용자 인터페이스로 이동하십시오. 인증 정보로 로그인하십시오.
2. 홈 페이지에서 **vCenter 등록 관리**를 클릭하십시오.
3. vCenter IP를 가리키도록 **검색 서비스 URL**을 편집하십시오. 임베디드 **PSC가 더 이상 존재하지 않음** PSC 독립형을 사용하십시오.

## vCenter Server vSphere 소프트웨어를 업그레이드한 후의 결과
{: #vc_vsphere_upgrade-results}

업그레이드가 완료된 후에 vSAN 상태 검사를 실행하면 IBM Cloud에서 제공하는 RAID 및 네트워크 제어기의 펌웨어 업데이트에 대한 경고가 발생할 수 있습니다. 펌웨어 업데이트가 필요한 호스트를 판별한 후 IBM 지원 센터를 통해 티켓을 열어 권장되는 버전으로 펌웨어를 업데이트하십시오.

1. vCenter 사용자 인터페이스에서 상태를 확인할 vSAN이 포함된 클러스터를 선택하십시오.
2. **모니터** 탭을 선택한 후 **vSAN** 탭을 선택하십시오.
3. **상태** 선택하고 표시된 경고를 기록하십시오.
4. **하드웨어 호환성** 경고가 표시되면 경고를 펼치고 경고 상태에 있는 경우 **제어기 펌웨어는 인증된 VMware임** 메시지를 클릭하십시오.
5. 펌웨어 업데이트 권장사항과 함께 나열된 호스트를 기록하십시오.
6. IBM 지원 센터를 통해 티켓을 열고 펌웨어 업데이트를 허용하기 위해 서비스로부터 각 호스트를 제거하도록 시간을 스케줄하십시오.

업그레이드가 완료되면 IBM 지원 센터를 통해 지원 티켓을 업데이트하십시오. 이 업그레이드 프로세스의 일부로 작성한 새 비밀번호를 제공하십시오. 예를 들어, 지원 티켓에서 어플라이언스 관리 서비스인 PSC 및 vCenter를 배치하기 위한 비밀번호를 제공하십시오. 그러면 IBM 지원 센터에서 {{site.data.keyword.vmwaresolutions_short}} 콘솔 및 내부 데이터베이스를 업데이트하여 6.7 레벨에서 {{site.data.keyword.vmwaresolutions_short}} 자동화를 재개합니다. 여기에는 서비스, 호스트, 클러스터 및 보조 vCenter 서버 인스턴스의 추가 및 제거가 포함됩니다.

## 관련 링크
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

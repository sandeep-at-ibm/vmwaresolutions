---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud 주문
{: #hcx_ordering}

서비스가 포함된 새 VMware vCenter Server with Hybridity Bundle 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 VMware HCX on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 VMware HCX on IBM Cloud 주문
{: #hcx_ordering-new}

새 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 인스턴스를 VMware HCX on {{site.data.keyword.cloud_notm}}와 함께 주문하려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스를 주문할 때 **서비스** 섹션에서 **VMware HCX on IBM Cloud**를 선택하십시오.


## 기존 인스턴스에 대한 VMware HCX on IBM Cloud 주문
{: #hcx_ordering-existing}

기존 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 인스턴스에 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 추가하려면 해당 서비스가 추가될 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.

## VMware HCX on IBM Cloud 구성
{: #hcx_ordering-config}

HCX on {{site.data.keyword.cloud_notm}}를 설치하려면 다음 설정을 완료하십시오.
1. 다음 옵션 중 하나를 선택하여 **HCX 상호연결 유형**을 지정하십시오.
  * **공용 네트워크:** HCX는 공용 네트워크를 통해 사이트 간에 암호화된 연결을 작성합니다. 라이센스 등록 및 측정이 공용 네트워크에서 수행됩니다.
  * **사설 상호 연결:** HCX는 사설 네트워크를 통해 사이트 간에 암호화된 연결을 작성합니다. 라이센스 등록 및 측정이 공용 네트워크에서 수행됩니다.
  * **사설 네트워크:** HCX는 사설 네트워크를 통해 사이트 간에 암호화된 연결을 작성합니다. 라이센스 등록 및 측정이 HTTP 프록시를 통해 사설 네트워크에서 수행됩니다.
3. **사설 네트워크**를 선택하는 경우 다음 필드를 완료하십시오.
  * **프록시 주소:** 프록시 서버의 IPv4 주소입니다.
  * **프록시 포트:** 프록시 서버 포트입니다. 포트 번호는 일반적으로 8080 또는 3128입니다.
  * **사용자 이름:** 프록시 인증이 필요한 경우 사용자 이름입니다.
  * **비밀번호:** 프록시 인증이 필요한 경우 비밀번호입니다.
  * **비밀번호 다시 입력:** 프록시 인증 유효성 검증을 위한 비밀번호를 다시 입력하십시오.
2. **공용 엔드포인트 인증서 유형**을 지정하십시오. **CA 인증서**를 선택하는 경우 다음 설정을 구성하십시오.
  * **인증서 컨텐츠:** CA 인증서의 컨텐츠를 입력하십시오.
  * **개인 키:** CA 인증서의 개인 키를 입력하십시오.
  * (선택사항) **비밀번호:** 개인 키가 암호화된 경우 개인 키의 비밀번호를 입력하십시오.
  * (선택사항) **비밀번호 다시 입력:** 개인 키의 비밀번호를 다시 입력하십시오.
  * (선택사항) **호스트 이름:** CA 인증서의 공통 이름(CN)에 맵핑될 호스트 이름입니다. HCX on {{site.data.keyword.cloud_notm}}에서는 NSX Edge가 CA 인증서의 형식을 허용해야 합니다. NSX Edge 인증서 형식에 대한 자세한 정보는 [SSL 인증서 가져오기](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html)를 참조하십시오.
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## HCX on IBM Cloud에 대한 배치 프로세스
{: #hcx_ordering-deploy}

HCX on {{site.data.keyword.cloud_notm}}의 배치가 자동화됩니다. 서비스가 포함된 vCenter Server with Hybridity Bundle 인스턴스를 주문하거나 나중에 인스턴스에 서비스를 배치할 때 {{site.data.keyword.vmwaresolutions_short}} 자동화 프로세스를 통해 다음 단계가 완료됩니다.
1. {{site.data.keyword.cloud_notm}} 인프라에서 HCX에 대해 3개의 서브넷이 주문됩니다.
   * HCX 관리를 위한 하나의 사설 포터블 서브넷.
   * HCX 상호연결을 위한 하나의 사설 포터블 서브넷. **사설 네트워크** 옵션이 **HCX 상호연결 유형**에 대해 선택된 경우 이 서브넷이 사용됩니다.
   * VMware의 활성화와 유지보수를 위한 하나의 공인 포터블 서브넷. **공인 네트워크** 옵션이 **HCX 상호연결 유형**에 대해 선택된 경우 이 서브넷도 HCX 상호연결에 사용됩니다.

   HCX에 대해 주문된 서브넷의 IP 주소는 VMware on {{site.data.keyword.cloud_notm}} 자동화로 관리되어야 합니다. 사용자가 작성한 VMware 리소스(예: VM 및 NSX Edge)에 이 IP 주소를 지정할 수 없습니다. VMware 아티팩트에 대한 추가 IP 주소가 필요한 경우 {{site.data.keyword.cloud_notm}}에서 고유한 서브넷을 주문해야 합니다.
   {:important}
2. **사설 네트워크**가 **HCX 상호연결 유형**으로 선택된 경우에는 사설 DVS(Distributed Virtual Switch)에서 **SDDC-DPortGroup-HCX-Private**이 작성됩니다.
3. VMware에서 HCX 정품 인증 키가 주문됩니다.
4. HCX 상호연결, 로컬 HCX 컴포넌트 및 원격 HCX 컴포넌트에서 필요로 하는 3개의 HCX용 리소스 풀 및 VM 폴더가 작성됩니다.
5. HCX 관리 트래픽을 위한 VMware NSX ESG(Edge Services Gateway)의 쌍이 배치되고 구성됩니다.
   * 주문된 서브넷을 사용하여 공용 및 사설 업링크 인터페이스가 구성됩니다.
   * ESG가 고가용성(HA)을 사용하는 추가 대형 에지 어플라이언스의 쌍으로 구성됩니다.
   * HCX Manager 간에 인바운드 및 아웃바운드 HTTPS 트래픽을 허용하도록 방화벽 규칙 및 네트워크 주소 변환(NAT) 규칙이 구성됩니다.
   * 로드 밸런서 규칙 및 리소스 풀이 구성됩니다. 이러한 규칙 및 리소스 풀은 HCX Manager 및 vCenter Server(Platform Services Controller가 임베드됨)의 적절한 가상 어플라이언스로 HCX 관련 인바운드 트래픽을 전달하는 데 사용되는 리소스 풀입니다.
   * ESG를 통해 수신되는 HCX 관련 인바운드 HTTPS 트래픽을 암호화하는 SSL 인증서가 적용됩니다.

   HCX 관리 에지는 온프레미스 HCX 컴포넌트와 클라우드 측 HCX 컴포넌트 간의 HCX 관리 트래픽에만 사용됩니다. HCX 관리 에지를 수정하거나 HCX 네트워크 확장에 이를 사용하지 마십시오. 대신, 네트워크 확장을 위한 별도의 에지를 작성하십시오. 또한 방화벽을 사용하거나 사설 IBM 관리 컴포넌트 또는 공용 인터넷과의 HCX 관리 에지 통신을 사용 안함으로 설정하면 HCX 기능에 부정적인 영향을 줄 수 있습니다.
   {:important}

6. HCX Manager on {{site.data.keyword.cloud_notm}}가 배치되고 활성화되고 구성됩니다.
   * HCX Manager는 vCenter Server에 등록됩니다.
   * HCX Manager, vCenter Server(Platform Services Controller가 임베드됨) 및 NSX Manager가 구성됩니다.
   * HCX Fleet가 구성됩니다.
   * 로컬 및 원격 HCX 배치 컨테이너가 구성됩니다.
7. HCX Manager의 호스트 이름 및 IP 주소가 VMware vCenter Server on {{site.data.keyword.cloud_notm}}의 DNS 서버에 등록됩니다.

## 관련 링크
{: #hcx_ordering-related}

* [HCX on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [HCX 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension 개요](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 문서](https://cloud.vmware.com/vmware-hcx/resources)

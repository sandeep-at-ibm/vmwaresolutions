---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VM에서 고객 관리 NSX ESG를 사용하도록 네트워크 구성
{: #vc_esg_config}

VMware vCenter Server 인스턴스에 배치된 VMware NSX Edge Services Gateway(ESG)를 활용할 수 있도록 가상 머신의 네트워크를 구성하십시오. 보안 위험을 최소화하도록 제공된 보안 조치에 대한 자세한 정보는 [관리 서비스 NSX Edge는 보안 문제점을 발생시킵니까?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)를 참조하십시오.

VMware NSX는 격리된 네트워크의 가상화를 허용하고 스위치, 라우팅 및 방화벽과 같은 여러 네트워킹 서비스를 제공하는
네트워크 가상화 플랫폼입니다. NSX에 대한 자세한 정보는 [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}를 참조하십시오.

vCenter Server 인스턴스에 대한 주문 프로세스의 일부로 다음 조치가 사용자 대신 완료됩니다.
* 사설 고객 서브넷은 {{site.data.keyword.cloud}} 인프라 사설 네트워크에 액세스하기 위해 가상 머신(VM)에서 사용하도록 주문됩니다.
* 공인 고객 서브넷은 VM이 인터넷에 액세스할 수 있도록 주문됩니다.
* NSX는 vCenter Server 인스턴스에 배치되고 구성됩니다.
* 샘플 NSX 논리 스위치는 고객 워크로드 VM에서 사용하도록 배치됩니다.
* 샘플 NSX DLR(Distributed Logical Router)은 계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 배치됩니다.
* NSX Edge 어플라이언스는 워크로드 논리 스위치의 IP 주소 범위와 네트워크 주소 변환(NAT) 규칙의 공인 IP 주소 간의 NAT를
수행하도록 배치되고 구성됩니다.

  NSX 에지는 개인 전용인 인스턴스의 경우에는 배치되지 않습니다.
  {:note}

* Veeam on {{site.data.keyword.cloud_notm}} 서비스를 설치한 경우에는 NSX Manager가 NSX 구성의 일별 백업을 수행하도록 구성됩니다. 자세한 정보는 [Veeam on {{site.data.keyword.cloud_notm}} 설치 시 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations#considerations-when-you-install-veeam-on-ibm-cloud)을 참조하십시오.

## VM에 대한 네트워킹 설정을 구성하는 프로시저
{: #vc_esg_config-procedure-config-networking}

워크로드 VM에 대한 NSX를 활용하려면 VM 작성 시 다음 단계를 완료하여 많은 설정을 구성해야 합니다.

1. VM의 네트워크 어댑터를 워크로드 논리 스위치로 설정하십시오.
   1. **새 가상 머신** 대화 상자에서 **하드웨어 사용자 정의** 탭을 클릭하십시오.
   2. **새 디바이스** 메뉴에서 **네트워크**를 선택한 후 **추가**를 클릭하십시오.
   3. 새로 추가된 네트워크 어댑터의 메뉴에서 워크로드 논리 스위치를 선택하십시오. 워크로드 논리 스위치의 예로 **vxw-dvs-17-virtualwire-1-sid-6000-Workload**가 있습니다.

   **워크로드 전환** 스위치를 선택하지 않아야 합니다.
   {:important}

2. VM에 사용 가능한 IP 주소를 식별하십시오.
   *  IP 주소는 `192.168.10.0/24`의 범위에 있어야 합니다. IP 주소 `192.168.10.1`은 예약되어 있습니다(**3단계** 참조).
   *  VM에서 실행되는 운영 체제의 네트워킹을 구성하는 경우 선택된 IP 주소와 넷마스크 `255.255.255.0`을
사용하십시오.

   사용자는 VM을 지정한 IP 주소의 범위를 관리할 책임이 있습니다.
   {:note}

3. VM의 기본 게이트웨이를 `192.168.10.1`로 지정하십시오. 이 주소는 워크로드 VM과 동일한 논리 스위치에 있는 NSX DLR의 IP 주소입니다.

## SNAT 규칙을 사용으로 설정하는 프로시저
{: #vc_esg_config-procedure-enable-snat-rule}

워크로드 VM이 인터넷에 대한 아웃바운드 액세스 권한을 갖도록 하려면 연관된 SNAT(Source Network Address Translation) 규칙을 사용으로 설정해야 합니다. SNAT 규칙을 사용하면 단일 공용 IP 주소로 전환될 VM에서 인터넷 액세스가 허용됩니다. VMware vSphere Web Cliente에서 다음 단계를 완료하십시오.

1. **홈 > 네트워킹 및 보안**을 클릭하십시오.
2. 네비게이터 분할창에서 **NSX Edge**를 클릭하고 **customer-nsx-edge**라는 에지를 두 번 클릭하십시오.
3. **관리 > NAT**를 클릭하여 **NAT** 탭을 여십시오.
4. 테이블에서 기본 SNAT 규칙을 선택한 후 테이블 위의 녹색 선택 표시를 클릭하여 규칙을 사용으로 설정하십시오.

NSX Edge NAT 규칙에 대한 자세한 정보는 [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}를 참조하십시오.

## 고객 서브넷 세부사항을 식별하는 프로시저
{: #vc_esg_config-procedure-identify-customer-subnets-details}

에지 **customer-nsx-edge**는 고유한 사용을 목적으로 하므로 이를 수정하여 인바운드 또는 아웃바운드 트래픽에 대한 추가 NAT 규칙을 정의할 수 있습니다. 이 규칙은 사용자 대신 주문된 공인 및 사설 고객 서브넷에서만 IP 주소를 사용해야 합니다.

주문된 IP 주소를 사용할 수 있도록 고객 서브넷에 대한 세부사항을 식별하려면 VMware vSphere Web Client에서 다음 단계를 완료하십시오.

1. **홈 > 네트워킹 및 보안**을 클릭하십시오.
2. 네비게이터 분할창에서 **NSX 에지**를 클릭하고 오른쪽 분할창의 에지 목록에서 **customer-nsx-edge edge**를 찾으십시오.
3. **설명** 열에서 **customer-nsx-edge**에 대한 에지 설명 위에 마우스를 갖다 대면 사설 및 공용 고객 서브넷 둘 다에 대한 서브넷 ID를 볼 수 있습니다.

또한 {{site.data.keyword.slportal}}의 다음 단계를 완료하여 고객 서브넷에 대한 추가 세부사항을 찾을 수 있습니다.

1. **네트워킹 > IP 관리 > 서브넷**을 클릭하십시오.
2. VMware vSphere Web Client에서 **customer-nsx-edge**의 설명에 표시된 대로 필터 메뉴를 클릭하고 **서브넷** 필드에 ID를 입력하십시오.
3. IP 주소에 표시된 참고사항을 검토하십시오. 이 참고사항은 초기 설정 중에 주문되고 사용된 서브넷과 및 IP 주소를 식별합니다.

   초기 설정 중에 주문되고 사용된 IP 주소를 사용하지 마십시오. 그러나 사용자의 요구사항에 따라 이 서브넷에
   다른 IP 주소를 사용할 수 있습니다. 추가 네트워크 주소 변환을 설정하려면 [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}를 참조하십시오.
   {:important}

## 관련 링크
{: #vc_esg_config-related}

* [문제점 해결](/docs/services/vmwaresolutions/vcenter//vcenter_chg_impact.html)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VM에서 고객 관리 NSX-T ESG를 사용하도록 네트워크 구성
{: #vc_nsx-t_esg_config}

VMware vCenter Server 인스턴스에 배치된 VMware NSX-T Edge Services Gateway(ESG)를 활용할 수 있도록 가상 머신의 네트워크를 구성하십시오. 보안 위험을 최소화하도록 제공된 보안 조치에 대한 자세한 정보는 [관리 서비스 NSX Edge는 보안 문제점을 발생시킵니까?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)를 참조하십시오.

VMware NSX-T는 격리된 네트워크의 가상화를 허용하고 스위치, 라우팅 및 방화벽과 같은 여러 네트워킹 서비스를 제공하는
네트워크 가상화 플랫폼입니다. NSX에 대한 자세한 정보는 [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}를 참조하십시오.

vCenter Server with NSX-T 인스턴스에 대한 주문 프로세스의 일부로 다음 조치가 사용자 대신 완료됩니다.
* 사설 고객 서브넷은 {{site.data.keyword.cloud}} 인프라 사설 네트워크에 액세스하기 위해 가상 머신(VM)에서 사용하도록 주문됩니다.
* 공인 고객 서브넷은 VM이 인터넷에 액세스할 수 있도록 주문됩니다.
* NSX-T는 vCenter Server with NSX-T 인스턴스에 배치되고 구성됩니다.
* 샘플 NSX-T 논리 스위치는 고객 워크로드 VM에서 사용하도록 배치됩니다.
* 샘플 NSX-T 티어 1 라우터는 계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 배치됩니다.
* NSX-T Edge 어플라이언스는 워크로드 논리 스위치의 IP 주소 범위와 네트워크 주소 변환(NAT) 규칙의 공인 IP 주소 간의 NAT를 수행하도록 배치되고 구성됩니다.

  NSX-T 에지는 개인 전용인 인스턴스의 경우에는 배치되지 않습니다.
  {:note}

## VM에 대한 네트워킹 설정을 구성하는 프로시저
{: #vc_nsx-t_esg_config-procedure-config-networking}

워크로드 VM에 대한 NSX-T를 활용하려면 VM 작성 시 다음 단계를 완료하여 많은 설정을 구성해야 합니다.

1. VM의 네트워크 어댑터를 워크로드 논리 스위치로 설정하십시오.
   1. **새 가상 머신** 대화 상자에서 **하드웨어 사용자 정의** 탭을 클릭하십시오.
   2. **새 디바이스** 메뉴에서 **네트워크**를 선택한 후 **추가**를 클릭하십시오.
   3. 새로 추가된 네트워크 어댑터의 메뉴에서 워크로드 오버레이 논리 스위치를 선택하십시오. 스위치의 예제 이름은 **overlay-ls**입니다.

   **워크로드 전환** 스위치를 선택하지 않아야 합니다.
   {:important}

2. VM에 사용 가능한 IP 주소를 식별하십시오.
   *  IP 주소는 `192.168.10.0/24`의 범위에 있어야 합니다. IP 주소 `192.168.10.1`은 예약되어 있습니다(**3단계** 참조).
   *  VM에서 실행되는 운영 체제의 네트워킹을 구성하는 경우 선택된 IP 주소와 넷마스크 `255.255.255.0`을
사용하십시오.

   사용자는 VM을 지정한 IP 주소의 범위를 관리할 책임이 있습니다.
   {:note}

3. VM의 기본 게이트웨이를 `192.168.10.1`로 지정하십시오. 이는 고객 티어 1 논리 라우터에 있는 다운링크 라우터의 IP 주소이고 워크로드 VM과 동일한 오버레이 논리 스위치에 연결되어 있습니다. 

## SNAT 규칙 사용
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

기본적으로 NSX-T는 SNAT 규칙을 사용합니다. 기존 규칙 수정에 대한 자세한 정보는 [Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}를 참조하십시오.

## 고객 서브넷 세부사항을 식별하는 프로시저
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

에지 **cust-nsx-edge1**을 비롯한 논리 라우터 **Customer-T1-LR** 및 **Customer-T0-LR**은 고유한 사용을 목적으로 하므로 이를 수정하여 인바운드 또는 아웃바운드 트래픽에 대한 추가 NAT 규칙을 정의할 수 있습니다. 이 규칙은 사용자 대신 주문된 공인 및 사설 고객 서브넷에서만 IP 주소를 사용해야 합니다.

주문된 IP 주소를 사용할 수 있도록 고객 서브넷에 대한 세부사항을 식별하려면 NSX-T Web Client에서 다음 단계를 완료하십시오.

1. **고급 네트워킹 및 보안** 탭을 클릭하십시오. 
2. 왼쪽 분할창에서 **패브릭**을 클릭한 후 드롭 다운 목록에서 **노드**를 선택하십시오.
3. 탭에서 **에지 전송 노드**를 선택하십시오.
4. 고객 에지 중 하나를 클릭하십시오. 예를 들면, **cust-nsx-edge0**입니다. 공용 및 사설 고객 서브넷은 **설명** 필드에 표시됩니다. 

또한 {{site.data.keyword.slportal}}의 다음 단계를 완료하여 고객 서브넷에 대한 추가 세부사항을 찾을 수 있습니다.

1. **네트워킹 > IP 관리 > 서브넷**을 클릭하십시오.
2. NSX-T Web Client에서 **customer-nsx-edge0**의 설명에 표시된 대로 필터 메뉴를 클릭하고 **서브넷** 필드에 ID를 입력하십시오.
3. IP 주소에 표시된 참고사항을 검토하십시오. 이 참고사항은 초기 설정 중에 주문되고 사용된 서브넷과 및 IP 주소를 식별합니다.

   초기 설정 중에 주문되고 사용된 IP 주소를 사용하지 마십시오. 그러나 사용자의 요구사항에 따라 이 서브넷에
   다른 IP 주소를 사용할 수 있습니다. 추가 네트워크 주소 변환을 설정하려면 [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}를 참조하십시오.
   {:important}

## 관련 링크
{: #vc_nsx-t_esg_config-related}

* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}

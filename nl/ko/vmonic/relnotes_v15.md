---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

subcollection: vmware-solutions


---

# V1.5 릴리스 정보
{: #relnotes_v15}

이 릴리스에는 새 기능, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VRF 대 클래식 SoftLayer 계정 요구사항
{: #relnotes_v15-vrf}

클래식 SoftLayer® 계정의 경우, VLAN Spanning은 계정 레벨에서 사용으로 설정될 수 있는 설정입니다. {{site.data.keyword.vmwaresolutions_short}}에서는 VLAN Spanning이 사용으로 설정되어야 합니다.

VRF(Virtual Routing and Forwarding) SoftLayer 계정의 경우, VLAN Spanning은 변경할 수 없는 영구적인 설정과 상응합니다. VRF 계정에 사용자 구성이 필요하지 않습니다.

주문하기 전에 VLAN Spanning이 사용으로 설정된 상태에서 SoftLayer 계정이 VRF 계정인지 또는 클래식(VRF 아님) 계정인지 확인해야 합니다. 그렇지 않으면 주문이 실패할 수 있습니다.

SoftLayer 계정이 VRF 계정인지 확인하려면 IBM Bluemix 지원 센터에 확인하십시오. 클래식 계정의 경우, [LAN Spanning 사용 또는 사용 안함](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}의 지시사항에 따라 VLAN Spanning을 사용으로 설정해야 합니다.

## 서비스 비용 모델 업데이트
{: #relnotes_v15-svc-charge}

Cloud Foundation 인스턴스의 경우, 각 노드에 적용되는 월별 요금인 새 _SDDC Manager_ 라이센스가 도입되었습니다.

## 사용성 개선사항
{: #relnotes_v15-ui}

개선사항은 사용자 인터페이스를 통해 수행됩니다.

* 여러 {{site.data.keyword.CloudDataCents_notm}}의 가용성 및 주문을 이행할 충분한 재고가 있는지 여부가 사용자 인터페이스에 명확하게 표시되어 있습니다. 이러한 세부사항을 사용하여 인스턴스를 주문할 때 {{site.data.keyword.CloudDataCent_notm}} 선택에 대한 현명한 결정을 내리십시오. 자세한 정보는 [vCenter Server 인스턴스 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)을 참조하십시오.
* Cloud Foundation 인스턴스의 경우, 입력 필드에 필수 정보를 입력할 때 인스턴스 이름, 도메인 및 하위 도메인 이름, 데이터 센터 위치와 같은 정보는 그래픽 형식으로 자동으로 표시됩니다.

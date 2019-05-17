---

copyright:

  years:  2016

lastupdated: "2016-11-04"

subcollection: vmware-solutions


---

# V1.1 릴리스 정보
{: #relnotes_v11}

이 릴리스에는 새 기능, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VLAN Sanning 요구사항
{: #relnotes_v11-vlan-spanning}

클래식(VRF 아님) SoftLayer® 계정을 사용하는 경우 VLAN Spanning이 사용으로 설정되어야 합니다. VLAN Spanning이 클래식 계정에 대해 사용으로 설정되지 않은 경우 VMware 가상화 환경의 여러 컴포넌트는 서로 통신하지 못할 수 있습니다. SoftLayer 계정에서 VLAN Spanning을 사용으로 설정하려면 [VLAN Spanning 사용 또는 사용 안함](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}을 참조하십시오.

## 이메일 설정 및 알림
{: #relnotes_v11-email}

**설정** 페이지에서 이메일 알림을 구성할 수 있습니다. 기본적으로, 해당 인스턴스가 프로비저닝되고 사용할 준비가 되었을 때 설정이 사용으로 설정됩니다. 이는 새로 주문된 인스턴스에 대해 이메일로 알림을 받음을 의미합니다. 또한 **설정** 페이지에서 이메일 알림을 사용 안함으로 설정할 수 있습니다. 자세한 정보는 [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)을 참조하십시오.

## 자세한 상태 정보
{: #relnotes_v11-status-info}

이제 자세한 상태 정보는 Cloud Foundation 인스턴스에 사용할 수 있습니다. 인스턴스 이름을 클릭할 때 표시되는 상태 정보는 배치 진행상태에 대한 추가 세부사항을 제공합니다. 오류가 발생하는 경우 문제에 대한 도움을 제공하도록 메시지가 표시됩니다.

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 콘솔 외부에서 작성된 클러스터 스케일링

VMware vSphere 오퍼링을 사용하여 {{site.data.keyword.vmwaresolutions_full}} 콘솔 외부에서 작성된 기존 vSphere 클러스터를 스케일링할 수 있습니다. 콘솔 외부에서 작성된 vSphere 클러스터를 스케일링하려면 콘솔을 사용하여 동일한 설정의 클러스터를 다시 작성한 후 클러스터를 스케일링하십시오.

## 요구사항

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](/docs/services/vmwaresolutions/vmonic/useraccount.html)를 참조하십시오.
*  [VMware vSphere on {{site.data.keyword.cloud_notm}}에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vsphere/vs_planning.html)의 요구사항 및 고려사항을 검토했습니다.

## 콘솔 외부에서 작성된 클러스터를 스케일링하는 프로시저

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 다음 **가상 데이터 센터** 섹션에 있는 **VMware vSphere**를 클릭하십시오.
2. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.  
   사용자가 **새로 작성** 탭에 있으며 **클러스터 구성** 목록에 **새 클러스터**가 표시되어 있는지 확인하십시오.
3. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 작성된 기존 클러스터와 동일한 설정을 사용하여 클러스터를 작성하십시오. 자세한 정보는 [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)을 참조하십시오.  
   네트워크 인터페이스의 경우에는 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 작성된 클러스터를 스케일링하려면 해당 클러스터의 기존 VLAN을 선택해야 합니다.
   {:note}
4. **주문 요약** 분할창에서 클러스터 구성을 확인한 후 **구성 저장**을 클릭하십시오.   
5. **시작하기** 페이지에서 **VMware vSphere on IBM Cloud** 카드를 클릭하십시오.
6. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.
7. **기존 항목 스케일링** 탭을 클릭하십시오. **클러스터 구성** 목록에서 최근에 작성한 클러스터를 선택하십시오.
8. **{{site.data.keyword.baremetal_short}}** 섹션에서 클러스터에 추가할 {{site.data.keyword.baremetal_short}}의 수를 지정하십시오.
9. 클러스터의 해당 공용 VLAN이 FortiGate 300 Series Security Appliance HA 이중화를 포함하지 않는 경우에는 **FortiGate Physical Appliance 300 Series HA 이중화** 아래의 **구매에 포함**을 선택하여 이를 주문할 수 있습니다.
10. **주문 요약** 분할창에서 인스턴스 구성 및 예상 비용을 확인하고, 비용이 청구될 계정이 올바른지 확인하고, 이용 약관을 검토하고 이에 동의한 후 **프로비저닝**을 클릭하십시오.

## 결과

클러스터의 배치가 자동으로 시작되고 주문이 처리 중이라는 이메일 확인을 수신합니다. 클러스터를 사용할 준비가 되면 이메일로 알림을 받습니다.

vSphere 클러스터는 vCenter Server 및 Cloud Foundation 인스턴스와 함께 **배치된 인스턴스** 페이지에 표시되지 않습니다.
{:note}

### 관련 링크

* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [기존 구성에 따라 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere/vs_orderingbasedonexistingconfig.html)
* [기존 vSphere 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)

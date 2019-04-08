---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 기존 vSphere 클러스터 스케일링
{: #vs_scalingexistingclusters}

{{site.data.keyword.vmwaresolutions_full}} 콘솔에서 주문하거나 저장한 VMware vSphere 클러스터를 스케일 확장할 수 있습니다. 이렇게 하려면 ESXi 서버를 추가하거나 클러스터의 FortiGate 300 Series Security Appliance HA 이중화를 주문하십시오.

## 요구사항
{: #vs_scalingexistingclusters-req}

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings)을 참조하십시오.
*  [vSphere 클러스터에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)의 요구사항 및 고려사항을 검토했습니다.
*  스케일링하려는 클러스터가 사용할 준비가 되었다는 확인 이메일을 받았습니다.

## 기존 클러스터를 스케일링하는 프로시저
{: #vs_scalingexistingclusters-procedure}

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 다음 **가상 데이터 센터** 섹션에 있는 **VMware vSphere**를 클릭하십시오.
2. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.  
3. **기존 항목 스케일링** 탭을 클릭하고 **클러스터 구성** 목록에서 스케일링할 클러스터를 선택하십시오.
4. 자동으로 완료된 클러스터 설정을 검토하십시오.
5. **{{site.data.keyword.baremetal_short}}** 섹션에서 클러스터에 추가할 {{site.data.keyword.baremetal_short}}의 수를 지정하십시오.
6. 클러스터가 공용 VLAN에 FortiGate 300 Series Security Appliance HA 이중화를 포함하지 않는 경우 어플라이언스를 주문할 수 있습니다. 이를 수행하려면, **FortiGate Physical Appliance 300 Series HA 이중화** 아래의 **구매에 포함** 선택란을 선택하십시오.
7. **주문 요약** 분할창에서 인스턴스 구성 및 예상 비용을 확인하십시오.
   * 주문하지 않고 구성을 템플리트로 저장하려면 **구성 저장**을 클릭하십시오.
   * 주문하려는 경우에는 비용이 청구될 계정이 올바른지 확인하고, 이용 약관을 검토하고 이에 동의한 후 **프로비저닝**을 클릭하십시오.

### 결과
{: #vs_scalingexistingclusters-results}

클러스터 스케일링이 자동으로 시작됩니다. 주문이 처리 중이라는 이메일 확인을 수신합니다. 클러스터를 사용할 준비가 되면 이메일로 알림을 받습니다.

스케일링하는 클러스터가 사용할 준비가 되지 않은 경우 오류 메시지를 수신할 수 있습니다.

vSphere 클러스터는 vCenter Server 및 Cloud Foundation 인스턴스와 달리 **리소스** 페이지에 표시되지 않습니다.
{:note}

## 관련 링크
{: #vs_scalingexistingclusters-related}

* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [기존 구성에 따라 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [콘솔 외부에서 작성된 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: vSphere order cluster, vSphere configuration, order vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 기존 구성에 따라 vSphere 클러스터 주문
{: #vs_orderingbasedonexistingconfig}

저장한 구성 템플리트에 따라 VMware vSphere 클러스터를 주문할 수 있습니다. 기존 클러스터 구성을 기반으로 한 새 클러스터 구성을 정의하려면 이 프로시저를 수행하십시오.

## 요구사항
{: #vs_orderingbasedonexistingconfig-req}

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)을 참조하십시오.
*  [vSphere 클러스터에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)의 요구사항 및 고려사항을 검토했습니다.
*  재사용할 구성 템플리트를 작성했습니다.

## 기존 구성에 따라 vSphere 클러스터를 주문하는 프로시저
{: #vs_orderingbasedonexistingconfig-procedure}

1. {{site.data.keyword.cloud_notm}} 카탈로그에서 왼쪽 탐색 분할창에 있는 **VMware** 아이콘을 클릭한 다음 **VMware 가상 데이터 센터** 섹션에 있는 **VMware vSphere on IBM Cloud** 카드를 클릭하십시오.
2. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.  
3. **새로 작성** 탭을 클릭하고 **클러스터 구성** 목록에서 구성 템플리트를 선택하십시오.
4. 새 클러스터 이름을 입력하십시오.
5. 자동으로 완료된 클러스터 설정을 검토하고 필요에 따라 설정을 업데이트하십시오. 설정에 대한 자세한 정보는 [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)을 참조하십시오.
6. **주문 요약** 분할창에서 인스턴스 구성 및 예상 비용을 확인하십시오.
   * 주문하지 않고 구성을 템플리트로 저장하려면 **구성 저장**을 클릭하십시오.
   * 주문하려는 경우에는 비용이 청구될 계정이 올바른지 확인하고, 이용 약관을 검토하고 이에 동의한 후 **프로비저닝**을 클릭하십시오.

   {{site.data.keyword.baremetal_short}}만 설치됩니다. 클러스터 배치 후 VMware vCenter, VMware NSX, VMware vSAN과 같이 다양한 컴포넌트를 설치하고 구성해야 합니다.
   {:note}

## 결과
{: #vs_orderingbasedonexistingconfig-results}

템플리트로 클러스터 구성을 저장한 경우 구성이 완료되었다는 콘솔 알림을 받습니다. 그 후 **클러스터 구성** 목록에서 해당 템플리트를 찾을 수 있습니다.

주문한 경우 클러스터의 배치가 자동으로 시작됩니다. 주문이 처리 중이라는 이메일 확인을 수신합니다. 클러스터를 사용할 준비가 되면 이메일로 알림도 받습니다.

vSphere 클러스터는 vCenter Server 인스턴스와 달리 **리소스** 페이지에 표시되지 않습니다.
{:note}

## 관련 링크
{: #vs_orderingbasedonexistingconfig-related}

* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [기존 vSphere 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [콘솔 외부에서 작성된 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

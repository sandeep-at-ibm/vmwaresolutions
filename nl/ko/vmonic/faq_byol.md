---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 라이센싱 및 BYOL에 대한 FAQ

{{site.data.keyword.vmwaresolutions_full}}의 고유한 라이센스 가져오기(BYOL) 기능을 포함하여 라이센스 부여에 대한 자주 묻는 질문의 답을 찾으십시오.

## BYOL은 무엇입니까?
{: faq}

고유한 라이센스 가져오기, 즉 BYOL은 V1.8 이상의 VMware Cloud Foundation 인스턴스와 V2.0 이상의 VMware vCenter Server 및 VMware vSphere 클러스터에 사용 가능한 기능입니다. BYOL을 통해 다음 VMware 소프트웨어 컴포넌트 중 하나 이상에 대한 고유한 VMware 라이센스를 사용할 수 있습니다.
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

VMware 컴포넌트에 대해 고유 라이센스 사용을 선택하고 이에 대한 유효한 라이센스 키를 제공한 경우에는 이 컴포넌트에 대해 IBM에서 라이센스가 주문되지 않으며 월별 라이센스 비용이 이 컴포넌트의 {{site.data.keyword.cloud_notm}} 인프라 계정으로 부과되지 않습니다.

비즈니스 파트너 사용자는 BYOL 기능을 사용할 수 없습니다.
{:note}

## VMware vSphere on IBM Cloud를 통해 주문된 라이센스 및 컴포넌트는 어디서 관리합니까?

VMware vSphere on {{site.data.keyword.cloud_notm}}에 대한 새 클러스터를 작성하기 위해 주문한 후 VMware 라이센스, ESXi 서버 및 기타 네트워킹 컴포넌트가 제공되고 {{site.data.keyword.slportal}}에서 관리될 수 있습니다.

배치 후 {{site.data.keyword.vmwaresolutions_short}} 콘솔로 이동하여 저장된 구성을 통해 새 클러스터를 스케일링하십시오. 자세한 정보는 [기존 vSphere 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)을 참조하십시오.

## BYOL에 필요한 라이센스 에디션 및 CPU는 무엇입니까?

다음 요구사항이 BYOL의 라이센스 에디션에 적용됩니다.

### vCenter Server 인스턴스에 대한 BYOL 요구사항

표 1. vCenter Server 인스턴스에 대한 라이센스 에디션 및 CPU 최소 요구사항

  |VMware 컴포넌트 |필요한 라이센스 에디션 |필요한 최소 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard                |해당사항 없음 |
  |vSphere        |Enterprise Plus |8개의 CPU |
  |vSAN           |Advanced 또는 Enterprise |8개의 CPU |
  |NSX            |Standard, Advanced 또는 Enterprise |8개의 CPU |

### Cloud Foundation 인스턴스에 대한 BYOL 요구사항

표 2. Cloud Foundation 인스턴스에 대한 라이센스 에디션 및 CPU 최소 요구사항

  |VMware 컴포넌트 |필요한 라이센스 에디션 |필요한 최소 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard |해당사항 없음 |
  |vSphere        |Enterprise Plus |8개의 CPU |
  |vSAN           |Advanced 또는 Enterprise |8개의 CPU |
  |NSX            |Enterprise |8개의 CPU |

## 제공한 라이센스 키가 올바르지 않으면 어떻게 됩니까?

해당 VMware 컴포넌트에 올바르고 VMware 컴포넌트의 최소 에디션 및 CPU 요구사항을 충족하는지 확인하도록 제공한 모든 라이센스 키를 유효성 검증합니다. 라이센스 키의 유효성 검증에 실패하면 알림을 받고 인스턴스 주문을 계속할 수 없습니다.

## 아홉 개 이상의 CPU에 라이센스 키를 제공할 수 있습니까?

예. 각 VMware 컴포넌트의 경우 CPU당 하나의 라이센스가 필요합니다. 현재 모든 vCenter Server 및 Cloud Foundation 서버에 두 개의 CPU가 있습니다. 따라서 각 서버에 두 개의 라이센스가 필요합니다. 나중에 인스턴스에 추가할 기본 인스턴스 및 확장 노드를 지원할 수 있는 라이센스 키를 제공하는 것이 좋습니다.

## BYOL 기능을 사용하는 경우 SDDC Manager 라이센스를 제공할 수 있습니까?

아니오. VMware과의 계약에는 클라이언트의 실제 라이센스 키를 승인해야 하는 내용이 포함됩니다. Cloud Foundation 배치에 SDDC Manager 라이센스가 포함되어 있지만 SDDC Manager 라이센스 키 파일을 승인할 수 없고 BYOL에 대해 이 파일을 유효성 검증할 수 없습니다. 그러므로 IBM에서 모든 인스턴스에 대한 SDDC Manager 라이센스 비용을 청구합니다. SDDC Manager 라이센스는 Cloud Foundation 인스턴스에 대한 전체 라이센스 비용 중 극히 일부만 표시합니다.

## 일부 VMware 컴포넌트의 경우 BYOL 기능을 사용하고, 다른 컴포넌트의 경우 월별 라이센스를 구매할 수 있습니까?

예. 네 가지 VMware 컴포넌트의 모든 조합으로 BYOL 기능을 사용하거나 라이센스를 구매할 수 있습니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔은 인스턴스를 주문할 때 라이센스 부여 옵션을 선택할 수 있도록 간소화할 수 있습니다. 초기 인스턴스 주문 시 라이센스 부여 옵션이 해당 인스턴스의 수명에 적용됩니다.

## 특정 VMware 컴포넌트의 경우 일부 라이센스에 BYOL을 사용하고 IBM에서 나머지 라이센스를 구매할 수 있습니까?

예. 클러스터 작성 시 특정 VMware 컴포넌트에 맞는 BYOL을 선택한 경우 다음 옵션이 제공됩니다.
* 새 BYOL키 입력
* 계속해서 기존 BYOL 키 사용
* 해당 클러스터를 위해 IBM 제공 라이센싱 구매

현재 클러스터당 VMware vSphere Enterprise 및 VMware vSAN만 라이센싱할 수 잇습니다.

## 클러스터 작성 시 BYOL을 사용할 수 있습니까?

예. 클러스터 작성 시 기존 BYOL 라이센스에서 BYOL을 수행하거나 새 BYOL을 입력할 수 있습니다. 또한 클러스터 작성 시 IBM 제공 구독 라이센스를 구매할 수 있습니다.

현재 클러스터당 VMware vSphere Enterprise 및 VMware vSAN만 라이센싱할 수 잇습니다.

## 내 BYOL 라이센스를 관리할 수 있는 방법은 무엇입니까?

인스턴스 배치가 완료된 후 VMware vSphere Web Client를 사용하여 BYOL 라이센스를 관리할 수 있습니다.

## 나중에 더 많은 ESXi 서버를 내 인스턴스에 추가하는 경우 인스턴스에서 내 BYOL 라이센스에 충분한 용량이 있는지를 유효성 검증합니까?

예. 더 많은 ESXi 서버를 배치된 인스턴스에 추가하는 경우 BYOL 라이센스의 용량이 지정된 ESXi 서버의 수를 자동으로 확인합니다. 용량이 충분하지 않으면 ESXi 서버가 추가되지 않고 콘솔 알림을 받습니다.

## BYOL이 사용된 클러스터에서 사용 가능한 라이센스의 용량을 확인할 수 있는 방법은 무엇입니까?

라이센스 키에서 사용 가능한 CPU 수를 찾으려면 다음 단계를 완료하십시오.
1. **배치된 인스턴스** 페이지로 이동하십시오.
2. 인스턴스를 찾아 클릭하십시오.
3. **인프라** 탭에서 라이센스 용량을 확인할 클러스터를 클릭하십시오.
   사용 가능한 CPU의 수는 **사용자 제공 라이센스** 테이블에 나열됩니다.

## BYOL 라이센스 부여 옵션을 선택한 경우 IBM에서 지원을 제공합니까?

IBM 지원 센터는 계속해서 인스턴스 구성 문제를 위한 연락 지점입니다. 그러나 보고된 문제가 BYOL VMware 컴포넌트와 관련된 것으로 판별되면 VMware Support로 이동합니다.

## BYOL을 사용하는 경우 vSphere 라이센스 비용이 가격 예상 목록에 표시되는 이유는 무엇입니까? 이에 대한 비용이 청구됩니까?

{{site.data.keyword.baremetal_short}}는 이미 설치된 VMware vSphere 및 이미 포함된 vSphere 라이센스와 프로비저닝됩니다. vSphere용 BYOL을 선택한 경우 인스턴스 배치 시 프로세스가 자동으로 시작되어 포함된 vSphere를 제거합니다. 그런 다음, 라이센스 비용이 {{site.data.keyword.cloud_notm}} 계정으로 청구됩니다. 이 프로세스에서 수행할 작업은 없습니다.

## BYOL에 대한 기존 수동 프로세스를 계속 사용할 수 있습니까?

BYOL 기능의 도입으로 수동 프로세스를 계속 사용하는 것은 권장되지 않습니다. BYOL을 사용하려면 라이센스를 주문 중일 때 고유한 라이센스를 제공하십시오.

## BYOL이 기타 VMware 제품(예: VMware vRealize Automation, VMware vRealize Operations 또는 VMware vRealize Log Insight)에 지원됩니까?

아니오, 이 VMware 제품은 인스턴스 배치의 일부가 아니기 때문입니다. 초기 배치 외에 이 VMware 제품이 설치될 수 있으며, 이 경우 이 제품을 설치하고 라이센싱하는 데 클라이언트 또는 해당 에이전트가 필요합니다.

## vCenter Server with Hybridity Bundle과 함께 NFS 스토리지를 주문할 수 있습니까?

새로 배치된 인스턴스의 경우 vSAN의 올플래시(all-flash) 스토리지만 지원됩니다. vCenter Server with Hybridity Bundle 오퍼링에 vSAN Advanced 또는 Enterprise 라이센싱이 포함됩니다.

NFS 스토리지를 사용하는 vCenter Server 인스턴스가 있는 경우 기존 인스턴스를 vCenter Server with Hybridity Bundle로 업그레이드할 수 있습니다. vSAN Advanced 라이센싱이 업그레이드 중에 주문될 때 올플래시 vSAN 클러스터를 프로비저닝하지 않아도 됩니다.

## vCenter Server with Hybridity Bundle과 함께 BYOL을 사용할 수 있습니까?

{{site.data.keyword.cloud_notm}}로 고유한 VMware 라이센싱을 가져올 수(BYOL) 없습니다. vCenter Server with Hybridity Bundle에서는 모든 VMware 라이센스가 IBM에서 제공되어야 합니다.

## vCenter Server with Hybridity Bundle 라이센싱과 vCenter Server 라이센싱 간의 차이는 무엇입니까?

vCenter Server에서 사용 가능한 개별 VMware 라이센스는 CPU당 가격이 책정됩니다. IBM에서 제공되는 모든 CPU당 VMware 라이센스와 같이 예를 들어, 듀얼 Intel Xeon Gold 6140의 경우 CPU당 16개가 넘는 코어가 있는 모든 서버에서 가격이 1.3배 증가합니다.

vCenter Server with Hybridity Bundle은 CPU가 아닌 코어마다 라이센스가 부여되는 VMware 라이센스 및 에디션의 지정된 세트입니다. 따라서 이러한 인스턴스에 대한 라이센싱 가격은 변경되지 않습니다.

## vCenter Server with Hybridity Bundle에 사용 가능한 IBM 제공 VMware 라이센스 컴포넌트 및 에디션은 무엇입니까?

vCenter Server with Hybridity Bundle의 새 인스턴스에는 VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced 또는 Enterprise, VMware vSAN Advanced 또는 Enterprise 및 VMware Hybrid Cloud Extension(HCX)가 포함됩니다.

NSX Base 에디션을 사용하는 vCenter Server 인스턴스가 있는 경우 vCenter Server with Hybridity Bundle을 주문할 때 NSX Advanced로 자동으로 업그레이드됩니다.

## vCenter Server with Hybridity Bundle에 포함된 NSX Advanced 에디션을 NSX Enterprise 에디션으로 업그레이드할 수 있습니까?

vCenter Server with Hybridity Bundle에 NSX Advanced가 포함되어 있을 때 vCenter Server with Hybridity Bundle을 주문한 후 NSX Enterprise 에디션으로 업그레이드할 수 있습니다. 이렇게 하려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 인스턴스 세부사항 페이지 탭에서 **업데이트 및 패치** 탭을 사용하십시오.

### 관련 링크

* [Cloud Foundation 인스턴스 주문](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Cloud Foundation 인스턴스](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [콘솔에 액세스](/docs/services/vmwaresolutions/vmonic/loginmethod.html)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Shared On-Demand 주문
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared는 시범 오퍼링으로 제공됩니다.
{:note}

On-Demand의 경우 가상 데이터 센터 vCPU 및 RAM이 필요에 따라 할당되며 가상 데이터 센터 vCPU 및 RAM 이용의 글로벌 사용량에 따라 할당되는 시간이 달라질 수 있습니다.
* vCPU 및 RAM 크기에 대해 설정되는 한계는 언제든지 이용할 수 있는 최대값입니다.
* 나중에 필요에 따라 vCPU 및 RAM 리소스를 늘리고 줄일 수 있습니다.
* 비용은 월별로 계산되며 가상 데이터 센터의 리소스 사용량을 기반으로 합니다.
* 가상 데이터 센터에서 할당되고 사용될 수 있는 스토리지의 크기에는 한계가 없습니다. 비용은 할당된 스토리지의 GB에 따라 시간별로 부과됩니다.
* 인바운드 및 아웃바운드 공용 네트워킹의 크기에는 한계가 없습니다. 공용 대역폭에는 GB당 비용이 부과됩니다.

## IBM Cloud for VMware Solutions Shared에 대한 요구사항
{: #shared_ordering_ondemand-req}

### IBM Cloud 인프라 계정
{: #shared_ordering_ondemand-account-req}

{{site.data.keyword.vmwaresolutions_short}}를 사용하여 IBM Cloud for VMware Solutions Shared를 주문하려면 **종량과금제** 또는 **구독** {{site.data.keyword.cloud_notm}} 계정이 있어야 합니다. 주문된 리소스의 비용이 해당 {{site.data.keyword.cloud_notm}} 계정으로 청구됩니다.

### 가상 데이터 센터 이름 요구사항
{: #shared_ordering_ondemand-vdc-name-req}

가상 데이터 센터 이름은 다음 요구사항을 *반드시* 충족해야 합니다. 이름 지정 요구사항은 향후에 적용됩니다.
* 소문자 영문자, 숫자 및 대시(-) 문자만 사용할 수 있습니다.
* 이름은 소문자 영문자로 시작해야 합니다.
* 이름은 소문자 영문자 또는 숫자로 끝나야 합니다.
* 가상 데이터 센터 이름의 최대 길이는 10자입니다.
* 가상 데이터 센터 이름은 계정 내에서 고유해야 합니다.

## Shared On-Demand를 주문하는 프로시저
{: #shared_ordering_ondemand-procedure}

1. {{site.data.keyword.cloud_notm}} 카탈로그에서 왼쪽 탐색 분할창에 있는 **VMware** 아이콘을 클릭한 다음 **VMware 가상 데이터 센터** 섹션에 있는 **IBM Cloud for VMware Solutions Shared** 카드를 클릭하십시오.
2. **IBM Cloud for VMware Solutions Shared** 페이지에서 **On-Demand** 카드를 클릭하고 **작성**을 클릭하십시오.
3. **IBM Cloud for VMware Solutions Shared - On-Demand** 페이지에서 가상 데이터 센터 이름을 입력하십시오. 오퍼링이 사용 가능한 {{site.data.keyword.CloudDataCent_notm}}가 미리 선택되어 있습니다.
4. 사용자의 요구사항에 따라 vCPU 및 RAM 한계를 선택하십시오.
5. 주문하기 전에 **주문 요약** 분할창에서 구성과 예상 비용을 확인하십시오.
6. **프로비저닝**을 클릭하십시오.

## Shared On-Demand를 주문한 후의 결과
{: #shared_ordering_ondemand-results}

* 리소스의 배치가 자동으로 시작되고 주문이 처리 중이라는 확인을 수신합니다. **가상 데이터 센터 상태**를 보고 주의해야 하는 문제가 포함된 배치 상태를 확인할 수 있습니다.
* 리소스가 성공적으로 배치된 경우에는 [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared의 기술 스펙](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs)에서 설명된 컴포넌트가 VMware 가상 플랫폼에 설치됩니다.
* 리소스를 사용할 준비가 되면 상태가 **사용할 준비가 됨**으로 변경됩니다. 

## 관련 링크
{: #shared_ordering_ondemand-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared의 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared 예약 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}

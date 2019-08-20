---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight의 배치 모델
{: #caveonix-deploy}

이 절에서는 솔루션을 설치하는 설치 프로세스와 함께 Caveonix RiskForesight의 배치 모델을 설명합니다.

{{site.data.keyword.vmwaresolutions_full}} RiskForesight 옵션을 선택하면 초기 단계는 자동으로 수행되므로 배치의 모든 단계를 따르지 않아도 됩니다. 그러나 전체 배치와 아키텍처를 이해하고 초기 배치 후에 솔루션의 스케일을 확장하려는 사용자의 경우 자세하게 이해해야 합니다.

RiskForesight 설치는 다음과 같은 상위 레벨 단계로 구성됩니다.

1. [초기 계획 및 전제조건](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – 배치 옵션을 이해하고 선택하며 애플리케이션 컴포넌트에 맞는 FQDN/IP 분석을 제공하도록 DNS를 구성합니다.
2. [가상 머신 배치](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) – OVF 템플리트에서 VM을 배치합니다. VM에서 모든 애플리케이션 컴포넌트를 설치했습니다.
3. [애플리케이션 구성](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – 각 VM에서 애플리케이션 컴포넌트를 구성하는 Caveonix 구성 스크립트를 실행합니다.
4. [애플리케이션 설정](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – 사용자가 애플리케이션에 액세스할 수 있도록 서비스 제공자와 테넌트 또는 조직을 설정합니다.

자동화된 설치에서는 하나의 VM을 프로비저닝하고 해당 VM에 모든 애플리케이션 컴포넌트를 구성합니다.
{:note}

## 배치 규모 지정
{: #caveonix-deploy-sizing}

배치 규모 지정은 다음 볼륨을 사용하여 계산합니다.

표 1. 볼륨

|데이터 유형	|볼륨 |
|---|---|
|일별 스캔	|1 |
|스캔 데이터(MB)	|20 |
|로그 데이터(MB)	| 500 |
|플로우 데이터(MB)	| 200 |
|자산 데이터(MB)	|46 |
|일별 자산당 스토리지 총계(MB)	|766 |
|데이터 복제 승수	|2 |
|총 인덱스 스토리지 / 자산 / 일(MB)	|1532 |

인덱스 저장소(Elastic Search)에서는 기본적으로 인덱스의 n+1 복제를 사용하므로 데이터 복제 승수는 2로 설정됩니다.
{:note}

스케일링 VM의 수는 자산 수와 인덱싱할 데이터 일수로 계산합니다.

표 2. 스케일링 VM 매개변수

|자산 수	|100	|500	|5000 |
|---|---|---|---|
|데이터 일 수	|30	|30	| 30 |
|총 인덱스 스토리지 / 자산 / 일(MB)	|1532	|1532	|1532 |
|총 인덱스 스토리지 / 자산 / 30일(TB)	|4	|22	|219 |
|스케일링 노드당 지원되는 데이터(TB)	|0	|8	|8 |
|필요한 스케일링 VM	|0	|3	|27 |

필요한 스토리지 크기는 다음과 같이 계산됩니다.

표 3. 스토리지 매개변수

|자산 수	|100	|500	|5000 |
|---|---|---|---|
|장기 데이터 보유 기간(월)	|8	|8	|8 |
|일별 자산당 스토리지 총계(MB)	|766	|766	|766 |
|데이터 일 수	|30	|30	| 30 |
|단기 데이터 보유(TB)	|  7	|33	|329 |
|장기 데이터 보유(TB)	|18	|88	|877 |

데이터 관점에서 데이터는 다음과 같이 사용됩니다.

-	스캔 데이터는 규제 준수 관리에서 사용합니다.
-	로그 데이터는 사후조사 관리에서 사용합니다.
-	정책 및 플로우 데이터는 위험 관리에서 사용하며 플로우 데이터는 NSX Manager에서만 사용할 수 있습니다.

데이터 스토리지에는 다음과 같은 세 개의 티어가 있습니다.

-	복제됨
-	단기
-	장기

다음 표에서는 배치 요약을 제공합니다.

표 4. 요약

|배치 모델	|“일체형”	|부분 분배	|완전 분배 |
|---|---|---|---|
|자산 수	|100	|500	|5000 |
|30일 내에 생성된 온라인 데이터(TB)	|4	|22	|219 |
|니어라인 데이터 보유(90일)(TB)	|  7	|33	|329 |
|오프라인 데이터 보유(8개월)(TB)	|18	|88	|877 |
|총 데이터 스토리지 보유(1년)(TB)	|28	|142	|1425 |
|기본 VM	|1	|1	|20 |
|스케일링 VM	|0	|3	|28 |
|VM 총계	|1	|4	|48 |

**참고:**
{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스를 제거하면 {{site.data.keyword.vmwaresolutions_short}} 자동화는 배치되어 있는 단일 "일체형" Caveonix VM 및 이를 위해 주문된 데디케이티드 사설 서브넷만 삭제합니다. 따라서 다음에 유의하십시오.
* Caveonix VM을 여러 VM으로 확장한 경우, 이러한 추가 VM은 제거되지 않습니다.
* 추가 VM에서 데디케이티드 사설 서브넷의 IP 주소를 사용한 경우에는 기능을 계속 수행하도록 이러한 VM에 새 IP 주소를 지정해야 합니다.
* {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스가 설치되어 있는 vCenter Server 인스턴스 A를 삭제할 경우 vCenter Server 인스턴스 B의 서비스에 대해 주문된 데디케이티드 사설 서브넷의 IP 주소를 사용했다면 vCenter Server  인스턴스 A 삭제 시에 데디케이티드 사설 서브넷이 취소됩니다.

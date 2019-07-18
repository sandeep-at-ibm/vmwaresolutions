---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

subcollection: vmware-solutions


---

# 일체형 배치
{: #caveonix-allinone}

모든 RiskForesight 애플리케이션 컴포넌트를 호스팅하는 단일 가상 머신(VM)을 자동으로 배치하고 구성합니다. 이 배치 모델은 최대 100개의 자산을 7 - 30일 간 인덱싱하는 소규모 배치에 적합합니다. “일체형” VM 세부사항은 다음 표에 표시되어 있습니다.

표 1. 일체형 매개변수

|매개변수	|값|
|---|---|
|유형	| Base|
|VM 수량	|1|
|vCPU	|16|
|RAM	|32GB|
|디스크	|80GB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트|	UI, 앱, 플러그인, 중앙 콜렉터, 인덱스 데이터 저장소, 메시징 데이터 저장소, 관계형 데이터 저장소, 인덱스 데이터 저장소, 원격 콜렉터|

추가 원격 콜렉터 VM 세부사항은 다음 표에 표시되어 있습니다.

표 2. 원격 콜렉터

|매개변수	|값|
|---|---|
|VM 수량	|As required|
|vCPU	|8|
|RAM	| 8GB|
|디스크	|1TB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트	|원격 콜렉터|

## 관련 링크
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

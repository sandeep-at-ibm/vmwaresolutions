---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 부분 분배
{: #caveonix-partially}

자동화된 배치가 완료되고 나면 초기 가상 머신(VM)의 RAM과 디스크를 늘려서 수동으로 스케일을 확장하고 세 개의 스케일 확장 VMs을 추가할 수 있습니다. Riskforesight 구성 스크립트를 실행하여 네 개의 VM 모두에서 애플리케이션 컴포넌트를 사용하고 구성할 수 있습니다.

이 배치 모델은 최대 30일 간의 데이터 인덱싱을 통해 최대 500개의 자산을 서비스할 수 있습니다.

{{site.data.keyword.cloud}} 사설 휴대용 서브넷에서 다음으로 사용 가능한 IP 주소를 선택하십시오. ADDNS에서 FQDN 이름을 구성하십시오.

VM의 규모는 다음과 같이 지정합니다.

표 1. 기본 매개변수

|매개변수	|값|
|---|---|
|유형	| Base|
|VM 수량	|1|
|vCPU	|16|
|RAM	|64GB|
|디스크	|1000GB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트	|UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Remote Collector|

스케일 확장 VM 세부사항은 다음과 같습니다.

표 2. 스케일 확장 매개변수

|매개변수	|값 |
|---|---|
|유형	|Scale-out |
|VM 수량	| 3 |
|vCPU	|8 |
|RAM	| 16GB |
|디스크	|4TB |
|OS	| CentOS 7 |
|설치된 애플리케이션 컴포넌트	|Data Nodes(scale-out) |

원격 콜렉터 VM 세부사항은 다음 표에 표시되어 있습니다.

표 3. 원격 콜렉터 매개변수

|매개변수	|값|
|---|---|
|VM 수량	|As required|
|vCPU	|8|
|RAM	| 8GB|
|디스크	|1TB|
|OS	|CentOS 7|
|설치된 애플리케이션 컴포넌트	|원격 콜렉터|

## 관련 링크
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

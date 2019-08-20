---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-21"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM 사용자 ID
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}}는 오퍼레이션(예: 호스트, 클러스터 또는 스토리지를 VMware 인스턴스에 추가)을 수행할 때 {{site.data.keyword.cloud_notm}} 자동화에 사용될 사용자 계정 내에 있는 일련의 사용자를 관리합니다. 사용자 계정의 사용자는 {{site.data.keyword.cloud_notm}} 서비스 자동화를 통해 서비스의 설치 및 구성에도 사용될 수 있습니다. {{site.data.keyword.cloud_notm}} 자동화 사용자 ID에 대한 다음 절을 검토하십시오.

IBM 사용자 ID가 삭제되거나 사용 안함으로 설정되는 경우 또는 비밀번호가 변경되는 경우에는 VMware 인스턴스 오퍼레이션이 실패합니다.
{:important}

## vCenter및 Platform Services Controller 사용자 ID
{: #audit_user_ids-vcenter-psc}

V2.5부터 {{site.data.keyword.vmwaresolutions_short}}는 다음 사용자 ID를 사용하여 기본적으로 임베드된 ID 소스를 vCenter에 추가합니다.

| 사용자   | 사용자 ID    | 메소드 | 설명 |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | VMware 구성(예: VMware 고가용성 설정 및 분배 스위치 작성)에 사용됩니다. 기본 및 보조 vCenter Server 인스턴스를 페어링하는 데 사후 배치가 사용됩니다. |
| 고객     | customerroot | SSH    | 고객용으로만 작성됩니다. |
| IBM      | automation@``root_domain``<br/>(Active Directory 사용자) | HTTP | 호스트 및 클러스터를 추가하고 제거하며, 추가 서비스로 가상 머신을 배치하고 구성하는 데 사후 배치가 사용됩니다. |
| 고객     | Administrator@vsphere.local | HTTP | 고객용으로만 작성됩니다. |
{: caption="표 1. vCenter및 Platform Services Controller 사용자 ID" caption-side="top"}

HTTP는 vCenter 설정 및 구성과 VMware 오퍼레이션(예: vCenter의 리소스 관리를 위한 호스트, 클러스터 또는 스토리지 추가)에 사용됩니다.
{:note}

## NSX Manager 사용자 ID
{: #audit_user_ids-nsx-mgr}

| 사용자   | 사용자 ID      | 설명 |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(Active Directory 사용자) | NSX VTEP IP 주소를 관리하고, 호스트 및 클러스터 구성을 관리하는 데 호스트 및 클러스터를 추가하고 제거하며, 라이센스 부여, 활성화 또는 사용량 보고를 위해 공용 네트워크 액세스 권한이 필요한 추가 서비스로 ESG 구성을 관리할 때 NSX VTEP IP 주소를 관리하고 호스트 및 클러스터 구성을 관리하는 데 사후 배치가 사용됩니다. |
| 고객     | Admin        | 고객용으로만 작성됩니다. |
{: caption="표 2. NSX Manager 사용자 ID" caption-side="top"}

## ESXi 호스트 사용자 ID
{: #audit_user_ids-esxi}

| 사용자   | 사용자 ID    | 설명 |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | 추가 NFS 스토리지를 추가하고 해당 스토리지에 대한 라우트를 구성하며 모든 서버 유효성 검증 코드를 실행하는 데 사후 배치가 사용됩니다. |
| 고객     | root         | 고객용으로만 작성됩니다. |
{: caption="표 3. ESXi 호스트 사용자 ID" caption-side="top"}

## Microsoft Active Directory 사용자 ID
{: #audit_user_ids-ad}

| 사용자   | 사용자 ID     | 설명        |
|:---------|:------------- |:------------|
| IBM      | automation    | 호스트를 추가하고, 가상 머신을 서비스에 추가하고, Active Directory 및 DNS 항목을 설정하는 데 사용됩니다. |
| 고객     | Administrator | 고객용으로만 작성됩니다. |
{: caption="표 4. Active Directory 사용자 ID" caption-side="top"}


## 서비스 사용자 ID
{: #audit_user_ids-services}

| 사용자 ID                                  | 설명        |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamicID``-@``domainName`` | F5 on  {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-Caveonix-``dynamicID``-@``domainName`` | Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-Fortigate-``dynamicID``-@``domainName`` | FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-FortigateVM-``dynamicID``-@``domainName`` | FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-HyTrustCC-``shortID``-@``domainName`` | HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-HyTrustDC-``shortID``-@``domainName`` | HyTrust DataControl on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-HyTrustKC-``shortID``-@``domainName`` | HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-KMIPAdapter-``dynamicID``-@``domainName`` | KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-ICP-``dynamicID``-@``domainName`` | {{site.data.keyword.cloud_notm}} Private Hosted 서비스의 설치 및 구성에 사용됩니다. |
| prod-SPPlus-``dynamicID``-@``domainName`` | IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-Veeam-``dynamicID``-@``domainName`` | Veeam on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-HCX-``dynamicID``-@``domainName`` | VMware HCX on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
| prod-Zerto-``dynamicID``-@``domainName`` | Zerto on {{site.data.keyword.cloud_notm}} 서비스의 설치 및 구성에 사용됩니다. |
{: caption="표 5. 서비스 사용자 ID" caption-side="top"}

여기서,

* ``dynamicID``는 서비스 설치 중에 동적으로 생성된 8 - 10자입니다.
* ``shortID``는 서비스 설치 중에 동적으로 생성된 5자입니다.
* ``domainName``은 인스턴스의 도메인 이름입니다.

## 관련 링크
{: #audit_user_ids-related}

* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

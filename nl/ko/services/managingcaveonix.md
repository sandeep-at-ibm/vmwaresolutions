---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix console, Caveonix RiskForesight license, login Caveonix console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud의 Caveonix RiskForesight 관리
{: #managingcaveonix}

## Caveonix RiskForesight 콘솔에 액세스
{: #managingcaveonix-access-console}

{{site.data.keyword.cloud}}의 Caveonix RiskForesight 서비스를 관리하려면 다음 단계를 완료하여 Caveonix RiskForesight 콘솔에 액세스해야 합니다.

1. {{site.data.keyword.cloud_notm}} 인프라 VPN 또는 점프 서버를 사용하여 Caveonix RiskForesight 가상 머신(VM)의 IP 주소에 대한 액세스를 허용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight에 대한 서비스 세부사항 페이지에서 IP 주소를 찾을 수 있습니다. 구체적으로는 다음과 같습니다.
   1. {{site.data.keyword.cloud_notm}} 인프라 고객 포털에서 VPN 비밀번호를 작성하십시오.
   2. {{site.data.keyword.cloud_notm}} 인프라 VPN 인증 정보를 사용하여 데이터 센터 VPN 포털에 로그인하십시오.
   3. 로컬 컴퓨터에서 IP 주소 및 호스트 이름 맵핑을 `hosts` 파일에 추가하십시오. 다음 형식을 사용하십시오.

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. Caveonix RiskForesight 콘솔에 액세스하려면 {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight에 대한 서비스 세부사항 페이지에서 **RiskForesight 콘솔 보기**를 클릭한 후 동일한 서비스 세부사항 페이지에 나열된 인증 정보를 사용하여 로그인하십시오.

## IBM Cloud의 Caveonix RiskForesight에 업데이트 적용
{: #managingcaveonix-update}

사용자는 Caveonix RiskForesight가 항상 최신 버전으로 업데이트되어 있도록 유지보수해야 합니다. [Caveonix Service Provider Portal](https://support.caveonix.com){:external}에서 필수 업데이트를 다운로드할 수 있습니다.

## Caveonix RiskForesight 라이센스 업데이트

Caveonix RiskForesight 라이센스는 1년 동안 유효합니다. 다음 프로시저를 사용하여 만기되는 경우 Caveonix RiskForesight 라이센스를 업데이트할 수 있습니다.
1. 새 Caveonix RiskForesight 라이센스를 주문하고 이를 Caveonix RiskForesight 콘솔에 복사하십시오. 자세한 정보는 [Caveonix RiskForesight 라이센스 주문 프로시저](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure)의 내용을 참조하십시오.
2. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 **Caveonix RiskForesight 라이센스** 테이블에서 만료된 라이센스를 삭제하십시오. 자세한 정보는 [Caveonix RiskForesight 라이센스 삭제 프로시저](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)의 내용을 참조하십시오.

## 관련 링크
{: #managingcaveonix-related}

* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)

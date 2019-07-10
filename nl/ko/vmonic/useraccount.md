---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 사용자 계정 및 설정 관리
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}}는 {{site.data.keyword.slapi_short}} 호출을 통해 {{site.data.keyword.cloud_notm}} 인프라와 통신합니다. {{site.data.keyword.slapi_short}}에 안전하게 액세스하려면 {{site.data.keyword.cloud_notm}} 인프라 계정의 인증 정보를 {{site.data.keyword.cloud_notm}} 계정에 링크해야 합니다.

다양한 이벤트에 대한 이메일 및 콘솔 알림을 수신하고자 하는지 여부를 지정할 수도 있습니다.

## 시작하기 전에
{: #useraccount-reqs}

* 하나의 {{site.data.keyword.cloud_notm}} 인프라 계정만 하나의 {{site.data.keyword.cloud_notm}} 사용자 계정에 링크할 수 있습니다.
* 사용 중인 {{site.data.keyword.cloud_notm}} 인프라 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 인프라 계정 요구사항](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)을 참조하십시오.
* {{site.data.keyword.cloud_notm}} 인프라 계정의 API 키가 변경된 경우에는 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 **설정** 페이지에서 키를 업데이트해야 합니다.

   사용자는 **설정** 페이지에 저장된 API 키가 올바르고 최신 상태인지 확인해야 합니다. 그렇지 않으면, API 키 유효성 검증이 필요한 오퍼레이션에 실패할 수 있습니다.
   {:important}

## 알림을 설정하는 프로시저
{: #useraccount-set-notif}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **설정**을 클릭하십시오.
2. 이벤트가 발생할 때 이메일로 알림을 받으려면 **이메일 알림 사용**을 클릭하십시오.
3. 이벤트가 발생할 때 콘솔에서 알림을 받으려면 **콘솔 알림 사용**을 클릭하십시오.

## 사용자 계정 인증 정보를 설정하는 프로시저
{: #useraccount-set-cred}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **설정**을 클릭하십시오.
2. **IBM Cloud 인프라 인증 정보** 영역에서 수행해야 하는 단계에 대한 정보를 검토하십시오. 
3. 링크된 {{site.data.keyword.cloud_notm}} 인프라 계정 및 {{site.data.keyword.cloud_notm}} 계정이 있는 경우 **검색**을 클릭하여 인증 정보를 자동으로 완료하십시오. 
4. 링크되지 않은 {{site.data.keyword.cloud_notm}} 인프라 계정 및 {{site.data.keyword.cloud_notm}} 계정이 있는 경우 링크해야 합니다. [IBM ID 계정 링크](/docs/account?topic=account-unifyingaccounts#link_accounts)의 지시사항을 따른 후 **검색**을 클릭하여 인증 정보를 자동으로 완료하십시오. 
5. {{site.data.keyword.cloud_notm}} 인프라 계정이 없고 청구 가능 {{site.data.keyword.cloud_notm}} 계정이 없는 경우 먼저 [계정 업그레이드](/docs/account?topic=account-upgrading-account)를 수행한 후 [클래식 인프라 API 키를 작성](/docs/iam?topic=iam-classic_keys)하십시오.
6. {{site.data.keyword.cloud_notm}} 인프라 계정이 없고 청구 가능 {{site.data.keyword.cloud_notm}} 계정이 있는 경우 [클래식 인프라 API 키를 작성](/docs/iam?topic=iam-classic_keys)하십시오.
7. **인증 정보 저장**을 클릭하십시오.

## 결과
{: #useraccount-results}

{{site.data.keyword.cloud_notm}} 계정과 {{site.data.keyword.cloud_notm}} 인프라 계정이 링크되면 {{site.data.keyword.cloud_notm}}에서 VMware 환경과 통신할 수 있도록 콘솔이 자동으로 {{site.data.keyword.cloud_notm}} 인프라 계정 인증 정보를 검색합니다.

저장된 {{site.data.keyword.cloud_notm}} 인프라 계정 인증 정보는 {{site.data.keyword.cloud_notm}} 인프라와의 상호작용이 필요한 향후 오퍼레이션에서 사용됩니다.

이메일 또는 콘솔 알림이 특정 인스턴스 이벤트에 대해 사용으로 설정되는 경우 이러한 이벤트가 발생할 때 이메일 또는 콘솔 메시지로 알림을 받습니다.

## 관련 링크
{: #useraccount-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [알림](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api)

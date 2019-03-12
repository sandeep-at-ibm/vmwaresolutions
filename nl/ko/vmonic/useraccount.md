---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 사용자 계정 및 설정 관리
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}}는 {{site.data.keyword.slapi_short}} 호출을 통해 {{site.data.keyword.cloud_notm}} 인프라와 통신합니다. {{site.data.keyword.slapi_short}}에 안전하게 액세스하려면 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정의 인증 정보를 {{site.data.keyword.cloud_notm}} 계정에 링크해야 합니다.

{{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정을 이전에는 IBM SoftLayer 계정이라고 했습니다.
{:note}

다양한 이벤트에 대한 이메일 및 콘솔 알림을 수신하고자 하는지 여부를 지정할 수도 있습니다.

## 시작하기 전에
{: #useraccount-reqs}

* 하나의 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정만 하나의 {{site.data.keyword.cloud_notm}} 사용자 계정에 링크할 수 있습니다.
* 사용 중인 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 인프라 계정 요구사항](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)을 참조하십시오.
* {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정의 API키가 변경된 경우에는 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 **설정** 페이지에서 키를 업데이트해야 합니다.

   **중요:** 사용자는 **설정** 페이지에 저장된 API 키가 올바르고 최신 상태인지 확인해야 합니다. 그렇지 않으면, API 키 유효성 검증이 필요한 오퍼레이션에 실패할 수 있습니다.

## 사용자 계정 및 설정을 관리하는 프로시저
{: #useraccount-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **설정**을 클릭하십시오.
2. **알림** 영역에서 알림 설정을 지정하십시오.
   * 이벤트가 발생할 때 이메일로 알림을 받으려면 **이메일 알림 사용**을 클릭하십시오.
   * 이벤트가 발생할 때 콘솔에서 알림을 받으려면 **콘솔 알림 사용**을 클릭하십시오.
3. **IBM Cloud 인프라 인증 정보** 영역에서 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정의 사용자 이름과 API키를 입력하십시오.
   * {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정과 {{site.data.keyword.cloud_notm}} 계정이 연결된 경우 **검색**을 클릭하여 인증 정보를 자동으로 입력하십시오.
   * {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정과 {{site.data.keyword.cloud_notm}} 계정이 연결되지 않은 경우에는 두 계정을 연결해야 합니다. [{{site.data.keyword.cloud_notm}} 인프라 고객 포털](https://control.softlayer.com/)에 로그인하고 콘솔의 지시사항에 따라 인증 정보를 가져온 다음 이를 입력하십시오.
   * {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 없는 경우에는 [계정을 등록](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)하고 콘솔의 지시사항에 따라 인증 정보를 가져온 다음 이를 입력하십시오.
4. **인증 정보 저장**을 클릭하십시오.

## 결과
{: #useraccount-results}

{{site.data.keyword.cloud_notm}} 계정과 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 링크되면 {{site.data.keyword.cloud_notm}}에서 VMware 환경과 통신할 수 있도록 콘솔이 자동으로 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정 인증 정보를 검색합니다.

저장된 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정 인증 정보는 {{site.data.keyword.cloud_notm}} 인프라와의 상호작용이 필요한 향후 오퍼레이션에서 사용됩니다.

이메일 또는 콘솔 알림이 특정 인스턴스 이벤트에 대해 사용으로 설정되는 경우 이러한 이벤트가 발생할 때 이메일 또는 콘솔 메시지로 알림을 받습니다.

## 관련 링크
{: #useraccount-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Cloud Foundation 인스턴스 주문](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [알림](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api){:new_window}

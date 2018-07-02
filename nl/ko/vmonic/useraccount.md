---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# 사용자 계정 및 설정 관리

{{site.data.keyword.vmwaresolutions_full}}는 {{site.data.keyword.slapi_short}} 호출을 통해 {{site.data.keyword.cloud_notm}} 인프라와 통신합니다. 안전하게 {{site.data.keyword.slapi_short}}에 액세스하려면 {{site.data.keyword.vmwaresolutions_short}} 사용자 계정에 {{site.data.keyword.cloud_notm}} 계정의 신임 정보를 연관시켜야 합니다.

**참고**: {{site.data.keyword.cloud_notm}} 계정은 이전에 IBM SoftLayer 계정으로 알려져 있습니다.

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 다양한 이벤트에 대한 이메일 알림을 수신할지 여부도 지정할 수 있습니다.

## 시작하기 전에

* {{site.data.keyword.vmwaresolutions_short}} 사용자 계정에 하나의 {{site.data.keyword.cloud_notm}} 계정만 연관시킬 수 있습니다.
* 사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정 요구사항](slaccountrequirement.html)을 참조하십시오.
* {{site.data.keyword.cloud_notm}} 계정의 API 키가 변경되는 경우 {{site.data.keyword.vmwaresolutions_short}} 사용자 계정의 키를 업데이트해야 합니다.

   **중요**: 사용자는 **설정** 페이지에 저장된 API 키가 올바르고 최신 상태인지 확인해야 합니다.
   그렇지 않으면, API 키 유효성 검증이 필요한 오퍼레이션에 실패할 수 있습니다.

{{site.data.keyword.vmwaresolutions_short}} 계정을 {{site.data.keyword.cloud_notm}} 계정과 연관시키려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 **설정** 페이지에 {{site.data.keyword.cloud_notm}} 계정 신임 정보를 입력하십시오.

{{site.data.keyword.cloud_notm}} 계정을 연관시킨 후 콘솔은 자동으로 {{site.data.keyword.cloud_notm}} 계정 신임 정보를 검색하여 {{site.data.keyword.cloud_notm}}에서 VMware 환경과 통신합니다.

## 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **설정**을 클릭하십시오.
2. 새 이벤트가 발생하는 경우 이메일로 알림을 받으려면 **이메일 알림 사용** 선택란을 선택하십시오.
3. 새 이벤트가 발생하는 경우 콘솔에서 알림을 받으려면 **콘솔 알림 사용** 선택란을 선택하십시오.
4. **IBM Cloud 인프라 신임 정보** 영역에서 {{site.data.keyword.cloud_notm}} 계정의 사용자 이름을 입력한 후 콘솔의 지시사항에 따라 {{site.data.keyword.slapi_short}} 키를 입력하십시오.
5. **신임 정보 저장**을 클릭하십시오.

## 결과

저장된 {{site.data.keyword.cloud_notm}} 계정 신임 정보는 {{site.data.keyword.cloud_notm}}인프라와의 상호작용이 필요한 이후 오퍼레이션에 사용됩니다. 이메일 또는 콘솔 알림이 특정 인스턴스 이벤트에 대해 사용으로 설정되는 경우 이벤트가 발생할 때 이메일 또는 콘솔 메시지로 알림을 받습니다.

## 관련 링크

* [FAQ](faq.html)
* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)
* [알림](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# IBM Cloud 계정으로 V2.5 이전 NetApp ONTAP Select 인스턴스 마이그레이션
{: #np_addinstancetousraccount}

{{site.data.keyword.cloud}} 계정의 V2.5 이상 릴리스에 배치된 NetApp ONTAP Select 인스턴스는 자동으로 사용자 계정에 추가되며 {{site.data.keyword.cloud_notm}} IAM(Identity and Access Management)에 의해 관리됩니다.

V2.4 이하 릴리스에 배치된 인스턴스의 경우에는 IAM-사용 사용자 관리를 위해 지정된 {{site.data.keyword.cloud_notm}} 계정으로 이를 마이그레이션할 수 있습니다.

## 시작하기 전에
{: #np_addinstancetousraccount-prereq}

인스턴스를 마이그레이션하려는 {{site.data.keyword.cloud_notm}} 계정이 IaaS 전용 계정이 아닌지 확인합니다. IaaS 전용 계정은 {{site.data.keyword.cloud_notm}} 계정에 연결되지 않은 {{site.data.keyword.cloud_notm}} 인프라(IBM Cloud) 계정입니다.

IaaS 전용 계정을 PaaS 계정에 연결하는 방법에 대한 자세한 정보는 [다음 단계를 수행하여 IaaS 및 PaaS 계정에 연결](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/)을 참조하십시오.

## 인스턴스를 마이그레이션하는 프로시저
{: #np_addinstancetousraccount-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. 콘솔 배너에서 사용자 계정 아이콘을 클릭한 다음 **계정** 필드를 클릭하여 인스턴스를 마이그레이션하려는 사용자 계정을 선택하십시오.
3. **NetApp ONTAP Select 인스턴스** 테이블에서 V2.5 이전 인스턴스를 찾으십시오.
4. **조치** 열에서 오버플로우 메뉴 아이콘을 클릭한 후에 **계정으로 인스턴스 마이그레이션**을 클릭하십시오.
5. **계정으로 인스턴스 마이그레이션** 창에서 인스턴스가 마이그레이션될 계정을 확인한 후에 **마이그레이션**을 클릭하십시오.

## 결과
{: #np_addinstancetousraccount-results}

1. 지정된 {{site.data.keyword.cloud_notm}} 계정으로 인스턴스를 마이그레이션하는 요청이 승인되었다는 콘솔 알림을 받습니다.
2. 인스턴스 마이그레이션이 완료되면 마이그레이션된 계정 아래의 **리소스** 페이지에 인스턴스가 표시됩니다. 마이그레이션된 인스턴스는 마이그레이션된 원래 계정에서 더 이상 표시되지 않습니다.

## 관련 링크
{: #np_addinstancetousraccount-related}

* [IAM에서 사용자 액세스 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)
* [서비스 및 리소스에 액세스하기 위한 사용자 초대](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [IBM Cloud IAM 개념](/docs/iam?topic=iam-iamoverview)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-26"

---

# IBM Cloud 계정으로 V2.5 이전 vCenter Server 인스턴스 마이그레이션

{{site.data.keyword.cloud}} 계정의 V2.5 이상 릴리스에 배치된 VMware vCenter Server 인스턴스는 자동으로 사용자 계정에 추가되며 {{site.data.keyword.cloud_notm}} IAM(Identity and Access Management)에 의해 관리됩니다. 

V2.4 이하 릴리스에 배치된 인스턴스의 경우에는 IAM-사용 사용자 관리를 위해 지정된 {{site.data.keyword.cloud_notm}} 계정으로 이를 마이그레이션할 수 있습니다. 


## 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오. 
2. 콘솔의 오른쪽 상단 모서리에서 사용자의 아바타를 클릭한 후에 **계정** 필드를 클릭하여 인스턴스가 마이그레이션될 사용자 계정을 선택하십시오. 
3. **vCenter Server 인스턴스** 테이블에서 V2.5 이전 인스턴스를 찾으십시오. 
4. **조치** 열에서 오버플로우 메뉴 아이콘을 클릭한 후에 **계정으로 인스턴스 마이그레이션**을 클릭하십시오. 
5. **계정으로 인스턴스 마이그레이션** 창에서 인스턴스가 마이그레이션될 계정을 확인한 후에 **마이그레이션**을 클릭하십시오. 

## 결과

1. 지정된 {{site.data.keyword.cloud_notm}} 계정으로 인스턴스를 마이그레이션하는 요청이 승인되었다는 콘솔 알림을 받습니다. 
2. 인스턴스의 마이그레이션이 완료되면 마이그레이션된 계정 아래의 **배치된 인스턴스** 페이지에 인스턴스가 표시됩니다. 마이그레이션된 인스턴스는 마이그레이션된 원래 계정에서 더 이상 표시되지 않습니다. 

### 관련 링크

* [IAM에서 사용자 액세스 관리](../vmonic/iam.html)
* [서비스 및 리소스에 액세스하기 위한 사용자 초대](../vmonic/iamuserinvite.html)
* [IBM Cloud IAM 개념](../../../iam/index.html)

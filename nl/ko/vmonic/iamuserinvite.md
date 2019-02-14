---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-11"

---

# 서비스 및 리소스에 액세스하기 위한 사용자 초대

{{site.data.keyword.vmwaresolutions_full}}는 다중 사용자 간의 협업을 위해 {{site.data.keyword.cloud_notm}} IAM(Identity and Access Management)과 통합되어 있습니다. {{site.data.keyword.cloud_notm}} 계정을 등록하고 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 로그인한 후에는 {{site.data.keyword.cloud_notm}} 계정에 사용자를 추가할 수 있습니다. 추가된 사용자는 계정에 대해 프로비저닝된 서비스와 리소스를 공유할 수 있습니다.

## 시작하기 전에

* 자신이 계정 소유자인지 또는 **VMware Solutions** 서비스에 대한 플랫폼 관리 역할이 **관리자**인지 확인하십시오.
* [IAM(Identity and Access Management)으로 사용자 액세스 관리](iam.html)에서 사용자 역할 및 권한을 검토했는지 확인하십시오.

## 서비스 및 자원에 액세스하도록 사용자를 초대하는 프로시저

1. 배너의 왼쪽에서 **관리 > 보안 > ID 및 액세스**를 클릭하십시오.
2. **사용자** 페이지에서 **사용자 초대**를 클릭하십시오.
3. **사용자 초대** 페이지의 **사용자** 섹션에서 **이메일 주소** 필드에 초대할 사용자의 이메일 주소를 입력하십시오.
4. **액세스** 섹션에서 **서비스**를 펼치고 다음 태스크를 완료하십시오.
   1. **액세스 지정 대상** 목록에서 **리소스**를 선택하십시오.
   2. **서비스** 목록에서 **VMware Solutions**를 선택하십시오.
   3. 사용자에 지정할 플랫폼 액세스 역할을 선택하십시오. 역할은 **관리자**, **편집자**, **운영자** 또는 **뷰어**입니다.
5. **사용자 초대**를 클릭하십시오.

## 결과

추가된 사용자는 초대를 수락한 후에 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 로그인하고 계정으로 전환할 수 있습니다. 이렇게 하기 위해 사용자는 프로파일 설정에서 {{site.data.keyword.vmwaresolutions_short}} 콘솔 배너에 있는 사용자 계정 아이콘을 클릭합니다. 그런 다음 추가된 사용자는 지정된 계정에서 사용 가능한 서비스와 리소스에 대해 협업하고 이를 공유할 수 있습니다.

### 관련 링크

* [사용자 초대 및 액세스 지정](../../../iam/iamuserinv.html)
* [ID 및 액세스 관리](../../../iam/quickstart.html)
* [사용자 및 액세스 관리](../../../iam/iamusermanage.html)
* [IAM 개념](../../../iam/index.html)
* [IBM Cloud 계정으로 V2.5 이전 vCenter Server 인스턴스 마이그레이션](../vcenter/vc_addinstancetousraccount.html)
* [IBM Cloud 계정으로 V2.5 이전 vCenter Server with Hybridity Bundle 인스턴스 마이그레이션](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [IBM Cloud 계정으로 V2.5 이전 Cloud Foundation 인스턴스 마이그레이션](../sddc/sd_addinstancetousraccount.html)
* [IBM Cloud 계정으로 V2.5 이전 NetApp ONTAP Select 인스턴스 마이그레이션](../netapp/np_addinstancetousraccount.html)
* [IBM Cloud 계정으로 V2.5 이전 VMware Federal 인스턴스 마이그레이션](../vcenter/vc_fed_addinstancetousraccount.html)

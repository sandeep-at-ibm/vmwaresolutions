---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam을 사용하여 IBM Cloud Object Storage 주문 및 구성
{: #icos_ordering}

Veeam Availability Suite 9.5 Update 4 릴리스를 사용하면 Veeam은 IBM Cloud Object Storage(ICOS)와 호환할 수 있습니다.Veeam on IBM Cloud 주문 시 IBM Cloud Object Storage 주문은 자동화되지 않지만 배치 후 추가될 수 있습니다.

IBM Cloud Object Storage를 주문하려면 지정된 순서대로 다음 태스크를 완료하십시오.

## Object Storage 인스턴스 작성
{: #icos_ordering-obj}

Object Storage 인스턴스를 작성하려면 [새 서비스 인스턴스 작성](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance)을 참조하십시오. 다음 태스크를 계속 수행하려면 단계를 따르고 이 섹션으로 돌아가십시오.

## 버킷 작성
{: #icos_ordering-bucket}

버킷을 작성하려면 [일부 버킷을 작성하여 데이터 저장](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets)을 참조하십시오. 다음 태스크를 계속 수행하려면 단계를 따르고 이 섹션으로 돌아가십시오.

## 서비스 인증 정보 작성
{: #icos_ordering-service-cred}

HMAC 인증 정보를 포함한 서비스 인증 정보를 작성하려면 [서비스 인증 정보](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)를 참조하십시오. 다음 태스크를 계속 수행하려면 단계를 따르고 이 섹션으로 돌아가십시오.

## 스케일 확장 저장소 추가
{: #icos_ordering-scale-repo}

Veeam 내에서 스케일 확장 저장소를 추가하려면 [스케일 확장 저장소 추가](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}를 참조하십시오. 다음 태스크를 계속 수행하려면 단계를 따르고 이 섹션으로 돌아가십시오.

## 클러스터 티어 유지보수 및 관리
{: #icos_ordering-manage-cloud}

클러스터 티어 유지보수 및 관리에 대한 정보는 [용량 티어 데이터 관리](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}를 참조하십시오.

## 관련 링크
{: #icos_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

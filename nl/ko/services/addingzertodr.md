---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Zerto on IBM Cloud 개요

Zerto on {{site.data.keyword.cloud}} 서비스는 복제 및 재해 복구 기능을 제공합니다. 이러한 기능은 {{site.data.keyword.cloud_notm}}의 VMware 가상 환경에서 데이터를 보호하고 복구하도록 배치 오퍼링으로 통합될 수 있습니다.

## Zerto on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 Zerto on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

**참고**: ZVM(Zerto Virtual Manager) 컴포넌트는 기본 클러스터에만 배치됩니다.

### VSI

* 하나의 VSI(Virtual Service Instance) - ZVM(Zerto Virtual Manager)
* 2 x 2.0GHz 코어
* 4GB RAM
* Windows Server 2012 R2 Standard Edition(64비트)

### 스토리지

디스크: 100GB(SAN)

### 네트워킹

* 하나의 기본 사설 IP 주소
* 1Gbps 사설 네트워크 업링크

### 라이센스 및 요금

Zerto Replication V5.5 라이센스

### 관련 링크

* [{{site.data.keyword.vmwaresolutions_short}} 정보](../vmonic/prod_overview.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 주문](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 관리](managingzertodr.html)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](managing_zerto_services.html)
* [zerto.com 웹 사이트](https://www.zerto.com){:new_window}
* [Zerto 기술 문서](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

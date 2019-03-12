---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 구현 및 관리
{: #kmip-implementation}

## 키 관리 서버 연결
{: #kmip-implementation-connecting-kms}

KMIP for VMware on {{site.data.keyword.cloud_notm}}를 사용하여 vSphere 암호화 또는 vSAN 암호화를 사용으로 설정하려면 다음 태스크를 완료해야 합니다.

1. [서비스 엔드포인트에 대한 계정을 사용](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)하십시오.
2. [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) 인스턴스를 작성하십시오.
3. IBM Key Protect 내의 고객 루트 키(CRK)를 작성하십시오.
4. KMIP for VMware에 사용할 IAM(Identity and Access Management) [서비스 ID 및 API 키](/docs/iam?topic=iam-serviceidapikeys)를 작성하십시오. Key Protect 인스턴스에 대한 이 서비스 ID 플랫폼 뷰어 액세스 권한과 서비스 쓰기 액세스 권한을 부여하십시오.
5. {{site.data.keyword.cloud_notm}} 카탈로그에서 [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) 인스턴스를 작성하십시오.
6. VMware vCenter에서 두 개의 서버(선택한 지역의 KMIP for VMware 엔드포인트에 하나씩)가 포함된 키 관리 서버(KMV) 클러스터를 작성하십시오.
7. VMware 방법 중 하나를 선택하여 vCenter에서 KMS 클라이언트 인증서를 생성하거나 설치하십시오.
8. 인증서의 공용 버전을 내보내고 KMIP for VMware 인스턴스에서 허용된 클라이언트 인증서로 인증서의 공용 버전을 구성하십시오.

## 암호화 사용
{: #kmip-implementation-enable-encrypt}

vSAN 암호화를 사용하려면 vCenter 클러스터에서 vSAN 일반 설정을 편집하고 암호화 선택란을 선택하십시오.

vSAN 상태 검사 시 하나 이상의 vSphere 호스트에서 KMS 클러스터에 연결할 수 없다는 경고가 주기적으로 나타날 수 있습니다. 이러한 경고는 vSAN 상태 검사 연결 제한시간이 너무 빨리 초과하기 때문에 발생합니다. 이 경고는 무시해도 됩니다.
{:note}

vSphere 암호화를 사용하려면 디스크 암호화에 필요한 가상 머신 스토리지 정책을 편집하십시오.

## 키 회전
{: #kmip-implementation-key-rotation}

{{site.data.keyword.cloud_notm}} 콘솔 또는 API를 사용하여 [Key Protect 고객 루트 키(CRK)를 회전](/docs/services/key-protect?topic=key-protect-rotating-keys)하십시오.

VMware vSAN 암호화의 경우 키를 암호화하는 VMware 키(KEK)를 회전하고 선택적으로 vCenter 클러스터의 vSAN 일반 설정에서 키를 암호화하는 데이터(DEK)를 회전하십시오.

VMware vSphere 암호화의 경우 **Set-VMEncryptionKey** PowerShell 명령을 사용하여 Mware KEK 및 DEK(선택적으로)를 회전하십시오.

## 키 취소
{: #kmip-implementation-key-revocation}

Key Protect에서 원하는 CRK를 삭제하여 KMIP for VMware로 사용 중인 모든 키를 취소할 수 있습니다.

키가 취소되면 이 키와 KMIP for VMware 인스턴스로 보호되는 모든 데이터가 이 방법을 통해 암호로 제거됩니다. VMware는 ESXi 호스트의 전원이 켜져 있는 동안 일부 키를 보존하므로 모든 암호화된 데이터가 더 이상 사용되지 않는지 확인하려면 vSphere 클러스터를 다시 시작해야 합니다.
{:important}

KMIP for VMware는 VMware에 알려져 있는 키 ID와 연관된 이름을 사용하여 Key Protect 인스턴스에 랩핑된 개별 KEK를 저장합니다. 개별 키를 삭제하여 개별 디스크 또는 드라이브의 암호화를 취소할 수 있습니다.

VMware는 암호화된 디스크가 있는 VM을 인벤토리에서 삭제할 때 KMS에서 키를 삭제하지 않습니다. 이는 백업에서 해당 VM의 복구를 허용하거나 백업이 인벤토리로 복원되는 경우를 위해 수행됩니다. 키를 재확보하고 암호로 모든 백업을 무효화하려면 VM 삭제 후에 Key Protect에서 키를 삭제해야 합니다.
{:note}

## 관련 링크
{: #kmip-implementation-related}

* [솔루션 개요](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [솔루션 디자인](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거

재해 복구 솔루션과 같은 VMware vCenter Server 인스턴스에 대한 서비스를 주문할 수 있습니다. 이 서비스가 더 이상 필요하지 않은 경우 인스턴스에서 이를 제거할 수 있습니다.

## vCenter Server 인스턴스에 사용 가능한 서비스

다음 표에서는 vCenter Server 인스턴스에서 사용 가능한 서비스를 표시합니다.

표 1. vCenter Server 인스턴스에 사용 가능한 서비스

| 서비스 이름 | 버전 번호 | 인스턴스 버전 |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html) | BIG-IP VE v13.1 | V1.9 이상 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | 300 시리즈 | V2.0 이상 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | 5.6 | V2.0 이상 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html) | 5.4.0 | V2.3 이상 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)  | 4.2.1 | V2.3 이상 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)              | 4.2 | V2.5 이상 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html) | 10.1.1 패치 1 | V2.2 이상 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html) |   | V2.2 이상 |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html) | 9.5u3 | V1.8 이상 |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html) | 5.5u4 패치 2 | V1.2 이상 |

## vCenter Server 인스턴스에 서비스를 추가하는 프로시저

vCenter Server 인스턴스에 서비스를 추가하려면 이전 테이블의 해당 서비스 링크를 클릭하여 서비스에 대한 고려사항을 검토하고 배치된 컴포넌트를 확인하십시오. 그런 다음 서비스 주문 주제의 지시사항에 따라 인스턴스에 서비스를 추가하십시오.

### 서비스 설치 결과

서비스 설치가 완료되면 이메일로 알림을 받고 서비스가 **설치됨** 상태로 인스턴스의 **서비스** 페이지에 표시됩니다.

## vCenter Server 인스턴스에 대한 서비스를 보는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 서비스를 볼 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **서비스**를 클릭하십시오.
4. **서비스** 페이지에서 하나의 서비스를 클릭하여 서비스 상태 및 기타 세부사항과 같은 정보를 검토하십시오.
5. 확인한 서비스에 따라 서비스 세부사항에 제공된 인증 정보를 사용하여 서비스 콘솔에 액세스하고 여기에서 서비스를 관리할 수 있습니다.

## vCenter Server 인스턴스에 대한 서비스를 제거하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 서비스를 제거할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **서비스**를 클릭하십시오.
4. **서비스** 페이지에서 제거할 서비스 인스턴스를 찾고 **삭제** 아이콘을 클릭하십시오.
5. 해당되는 경우 **서비스 삭제** 창에서 고려사항 또는 경고를 검토하십시오. **이해함**을 선택하고 **삭제**를 클릭하십시오.

### 서비스 제거 결과

서비스 제거 요청이 허용된 후 서비스 상태가 **제거 중**으로 변경됩니다.

서비스 제거가 완료되면 이메일로 알림을 받고 서비스가 인스턴스의 **서비스** 페이지에서 제거됩니다.

**주의:** 제거된 서비스에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 비용이 청구됩니다.

### 관련 링크

* [FAQ](../vmonic/faq.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 온프레미스 VMware HCX on IBM Cloud 인스턴스에 대한 고려사항

온프레미스 사용을 위해 주문한 HCX on {{site.data.keyword.cloud}} 인스턴스를 설치하거나 삭제하기 전에 다음 고려사항을 검토하십시오.

**참고:** HCX on {{site.data.keyword.cloud_notm}}의 vCenter Server 인스턴스는 온프레미스 사이트의 세 개의 동시 연결로 제한됩니다.

## 온프레미스 HCX on IBM Cloud 인스턴스 설치 시 고려사항

HCX on {{site.data.keyword.cloud_notm}} 컴포넌트는 {{site.data.keyword.cloud_notm}} 및 사용자의 온프레미스 vSphere 환경 모두에 설치되어야 합니다. 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 설치하기 전에 HCX on {{site.data.keyword.cloud_notm}} 서비스를 {{site.data.keyword.cloud_notm}}의 vCenter Server with Hybridity Bundle 인스턴스에 설치하는 것이 좋습니다. 자세한 정보는 [HCX on {{site.data.keyword.cloud_notm}}에 대한 고려사항](../services/hcx_considerations.html)을 참조하십시오.

### IP 주소에 대한 요구사항

전체 HCX 기능을 사용하려면 최소 다섯 개의 사설 IP 주소가 있어야 하고 해당 IP 주소가 인터넷에 액세스할 수 있도록 해야 합니다.

### 온프레미스 HCX on IBM Cloud 인스턴스의 배치 프로세스

온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 설치하려면 다음 태스크를 완료해야 합니다.
1. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 주문하십시오. 자세한 정보는 [온프레미스 VMware HCX on IBM Cloud 인스턴스 주문](standalone_orderingserviceinstances.html)을 참조하십시오.
2. **HCX Cloud 콘솔**에서 다음 단계를 완료하십시오.
    1. **관리** 탭을 클릭하십시오.
    2. **시스템 업데이트** 탭에서 **REQUEST DOWNLOAD LINK**를 클릭하십시오.
    3. **COPY LINK**를 클릭한 후 이 링크를 사용하여 온프레미스 vSphere 환경에 대한 액세스 권한으로 HCX Enterprise Client를 온프레미스 환경에 다운로드하십시오.
3. VMware vSphere Web Client에서 HCX Manager 가상 어플라이언스(HCX Manager)로 HCX Enterprise Client를 온프레미스 환경에 배치하십시오.

   **참고:** 사설 네트워크의 온프레미스 HCX Manager를 배치하고 해당 HCX Manager가 공용 네트워크에 액세스할 수 있도록 해야 합니다. NSX Edge, Vyatta 또는 유사한 게이트웨이를 사용하여 온프레미스 HCX Manager에 대한 인터넷 액세스를 허용할 수 있습니다. 사설 네트워크 액세스와 공용 네트워크 액세스에 사용된 게이트웨이가 서로 다른 경우, 사설 네트워크 액세스에 대한 정적 라우트를 작성하도록 기본 게이트웨이를 사용하여 공용 네트워크 액세스 및 온프레미스 **HCX Manager 관리 콘솔**을 허용하는 것이 좋습니다.
4. HCX Manager 배치가 완료된 후 **HCX Manager 관리 콘솔**을 사용하여 온프레미스 HCX Manager를 활성화하십시오. 온프레미스 HCX Manager의 정품 인증 키를 얻으려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 주문하십시오. 자세한 정보는 [온프레미스 HCX 인스턴스 주문](../services/standalone_orderingserviceinstances.html)을 참조하십시오.
5. HCX on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 자체 서명된 SSL 인증서를 사용한 경우 다음 단계를 완료하여 인증서를 온프레미스 HCX Manager에 가져와야 합니다.
    1. 온프레미스 **HCX Manager 관리 콘솔**에서 **관리** 탭을 클릭하십시오.
    2. 왼쪽 탐색 분할창에서 **신뢰할 수 있는 CA 인증서**를 클릭한 후 오른쪽의 **IMPORT**를 클릭하십시오.
    3. **URL**을 클릭한 후 적용할 인증서의 URL을 입력하십시오. 즉, {{site.data.keyword.vmwaresolutions_short}} 콘솔의 HCX on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 **HCX Cloud IP**(``https://<cloud-side public IP>``)입니다.
    4. **APPLY**를 클릭하십시오.

이제 온프레미스 HCX Manager의 기본 설정을 완료했습니다. 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 사이트와 클라우드 측 HCX 사이트의 페어링을 진행할 수 있습니다.

자세한 정보는 [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)을 참조하십시오.

## 온프레미스 HCX on IBM Cloud 인스턴스 삭제 시 고려사항

온프레미스 사용을 위해 주문한 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 삭제하기 전에 다음 고려사항을 검토하십시오.
1. VMware vSphere Web Client에서 HCX 사용자 인터페이스로 이동한 후 다음 항목을 확인하십시오.
    1. HCX 마이그레이션 또는 재해 복구 오퍼레이션이 실행 중이 아닌지 확인하십시오.
    2. 모든 확장된 네트워크가 제거되었는지 확인하십시오.
    3. 클라이드 사이트가 페어링된 상태에서 모든 상호연결 컴포넌트가 제거되었는지 확인하십시오.

   **중요:** 다음 단계로 진행하기 전에 모든 고려사항을 완료해야 합니다. 그렇지 않은 경우에는 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스에 대한 라이센스가 취소되며, 이는 마이그레이션을 수행할 수 없도록 하고 HCX 컴포넌트에 오류를 발생시킬 수 있습니다.  
2. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서, 온프레미스 HCX Manager에 대한 정품 인증 키를 얻기 위해 주문한 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 삭제하십시오. 다음 단계로 진행하기 전에 삭제된 인스턴스를 더 이상 콘솔에 사용할 수 없음을 확인하십시오.

   자세한 정보는 [온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스 삭제](../services/standalone_deletingserviceinstances.html)를 참조하십시오.
3. VMware vSphere Web Client에서 온프레미스 HCX Manager를 삭제하십시오.

### 관련 링크

* [온프레미스 HCX on {{site.data.keyword.cloud_notm}} 인스턴스 보기](../services/standalone_viewingserviceinstances.html)
* [HCX 용어집](hcx_glossary.html)
* [VMware Hybrid Cloud Extension 문서](https://hcx.vmware.com/#vm-documentation)
* [VMware HCX 리소스](https://hcx.vmware.com/#/docs)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

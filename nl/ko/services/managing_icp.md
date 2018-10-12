---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-31"

---

# IBM Cloud Private Hosted 요청

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}}는 {{site.data.keyword.cloud_notm}} Private Hosted on your VMware vCenter Server 인스턴스를 자동으로 배치합니다.

{{site.data.keyword.cloud_notm}} Private Hosted는 마이크로서비스 및 컨테이너의 기능을 {{site.data.keyword.cloud_notm}}의 VMware 환경에 제공합니다. 이 서비스를 사용하면 익숙한 동일 VMware 및 {{site.data.keyword.cloud_notm}} Private 운영 모델과 도구를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장할 수 있습니다.

## IBM Cloud Private Hosted의 기술 스펙

다음은 {{site.data.keyword.cloud_notm}} Private Hosted 서비스를 요청하기 위한 최소 요구사항입니다.

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
  **참고**: VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle은 지원되지 않습니다.
* VMware NSX Advanced 또는 Enterprise 에디션
* 세 개의 {{site.data.keyword.baremetal_long}}
* 듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz
* 서버당 384GB RAM
* 4IOPS/GB의 8,000GB가 있는 공유 NFS 스토리지의 한 개의 파일 공유
* 33개의 IBM Cloud Private 가상 프로세서 코어 라이센스
* 데이터 백업의 경우 Veeam on IBM Cloud 서비스가 권장됩니다.

## IBM Cloud Private Hosted 요청 프로시저

1. [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)의 단계에 따라 새 vCenter Server 인스턴스를 주문하십시오. 또한 기존 인스턴스를 위한 IBM Cloud Private Hosted를 요청할 수 있습니다.
  **중요**: 사용자 환경이 이전에 나열된 최소 요구사항을 충족하는지 확인하십시오.
2. IBM Cloud Private 권한 부여가 있는지 확인하십시오.
3. vCenter Server 인스턴스를 사용할 준비가 되었다는 확인을 받은 후 다음 단계를 진행하여 IBM Cloud Private Hosted를 요청하십시오.
4. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **시작하기**를 클릭하십시오.
5. 페이지 아래로 스크롤하고 **추가 서비스 주문**에서 **IBM Cloud Private Hosted** 카드를 클릭하십시오.
6. **IBM Cloud Private Hosted on vCenter Server on IBM Cloud** 페이지의 **IBM Cloud Private Hosted DevOps 팀에 문의** 상자에 요구사항에 대한 설명을 입력하고 **상담 요청**을 클릭하십시오.

{{site.data.keyword.cloud_notm}} Private Hosted DevOps 담당자는 {{site.data.keyword.cloud_notm}} 연락처 정보를 통해 사용자에게 연락하여 시작을 돕습니다.

### 관련 링크

* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)(PDF 다운로드)
* [IBM Cloud Private의 티켓 열기](https://www.ibm.com/mysupport/s/?language=en_US)

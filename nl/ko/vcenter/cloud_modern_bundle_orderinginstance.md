---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스의 주문, 보기 및 삭제

마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스를 주문하기 전에 계획 요구사항을 검토하십시오. 

## 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스 주문의 요구사항 및 계획

다음 요구사항을 확인하고 다음 태스크를 완료해야 합니다.

### 온프레미스 HCX 인스턴스에 대한 전제조건

* VMware vSphere 및 vCenter 5.5 이상이 필요합니다.
* vSphere 환경에 {{site.data.keyword.cloud_notm}}로 마이그레이션될 VM에 대한 분배 스위치가 있어야 합니다.
* HCX Manager Virtual Appliance가 온프레미스 환경의 사설 네트워크에 배치될 수 있어야 하고 공용 인터넷에 액세스하도록 허용되어야 합니다.

### IBM Cloud 인프라 계정

* {{site.data.keyword.vmwaresolutions_short}}를 사용하여 인스턴스를 주문하려면 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 있어야 합니다. 인스턴스에 주문된 컴포넌트의 비용이 해당 {{site.data.keyword.cloud_notm}} 계정으로 청구됩니다.
*  **설정** 페이지에서 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **설정**을 클릭하십시오.

### 인스턴스 이름 요구 사항

인스턴스 이름 요구사항을 검토하십시오.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 인스턴스 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 인스턴스 이름의 최대 길이는 10자입니다.
* 인스턴스 이름은 계정 내에서 고유해야 합니다.

## 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스의 주문 프로시저

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **마이그레이션 및 앱 현대화를 위한 단일 노드 평가판**을 클릭하십시오.
2. **마이그레이션 및 앱 현대화를 위한 단일 노드 평가판** 페이지에서 **계속**을 클릭하십시오.
3. {{site.data.keyword.cloud_notm}} 인프라 계정을 요청하는 단계를 완료하거나 기존의 **사용자 이름** 및 **API 키**를 제공하고 **검색**을 클릭하십시오.

 API 키가 있는 경우 이 섹션은 숨겨집니다.
 {:note}
4. 인스턴스 이름을 입력하십시오.
5. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.  

 기본적으로 DAL09 {{site.data.keyword.CloudDataCent_notm}}가 미리 선택되어 있습니다. 필요한 경우 다른 {{site.data.keyword.CloudDataCent_notm}} 위치를 선택하십시오.
 {:note}
6. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
   1. 인스턴스의 설정을 검토하십시오.
   2. 인스턴스의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 인스턴스를 주문하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

### 결과

인스턴스의 배치가 자동으로 시작되고 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 서비스 활성 키가 주문됩니다.

#### HCX on IBM Cloud에 대한 배치 프로세스

HCX on {{site.data.keyword.cloud_notm}}의 배치가 자동화됩니다. 다음 단계는 {{site.data.keyword.vmwaresolutions_short}} 자동화 프로세스에 의해 완료됩니다.
1. {{site.data.keyword.cloud_notm}} 인프라에서 HCX에 대해 3개의 서브넷이 주문됩니다.
   * HCX 관리를 위한 두 개의 사설 포터블 서브넷.
   * VMware의 활성화와 유지보수를 위한 하나의 공인 포터블 서브넷. 이 서브넷은 HCX 상호연결에도 사용됩니다.

   HCX에 대해 주문된 서브넷의 IP 주소는 VMware on {{site.data.keyword.cloud_notm}} 자동화로 관리되어야 합니다. 사용자가 작성한 VMware 리소스(예: VM 및 NSX Edge)에 이 IP 주소를 지정할 수 없습니다. VMware 아티팩트에 대한 추가 IP 주소가 필요한 경우 {{site.data.keyword.cloud_notm}}에서 고유한 서브넷을 주문해야 합니다.
   {:important}
3. HCX 상호연결, 로컬 HCX 컴포넌트 및 원격 HCX 컴포넌트에서 필요로 하는 3개의 HCX용 리소스 풀 및 VM 폴더가 작성됩니다.
4. HCX 관리 트래픽을 위한 VMware NSX ESG(Edge Services Gateway)의 쌍이 배치되고 구성됩니다.
   * 주문된 서브넷을 사용하여 공용 및 사설 업링크 인터페이스가 구성됩니다.
   * ESG가 고가용성(HA)을 사용하는 추가 대형 에지 어플라이언스의 쌍으로 구성됩니다.
   * HCX Manager 간에 인바운드 및 아웃바운드 HTTPS 트래픽을 허용하도록 방화벽 규칙 및 네트워크 주소 변환(NAT) 규칙이 구성됩니다.
   * 로드 밸런서 규칙 및 리소스 풀이 구성됩니다. 이러한 규칙 및 리소스 풀은 HCX Manager 및 vCenter Server(Platform Services Controller가 임베드됨)의 적절한 가상 어플라이언스로 HCX 관련 인바운드 트래픽을 전달하는 데 사용되는 리소스 풀입니다.
   * ESG를 통해 수신되는 HCX 관련 인바운드 HTTPS 트래픽을 암호화하는 SSL 인증서가 적용됩니다.

   HCX 관리 에지는 온프레미스 HCX 컴포넌트와 클라우드 측 HCX 컴포넌트 간의 HCX 관리 트래픽에만 사용됩니다. HCX 관리 에지를 수정하거나 HCX 네트워크 확장에 이를 사용하지 마십시오. 대신, 네트워크 확장을 위한 별도의 에지를 작성하십시오. 또한 방화벽을 사용하거나 사설 IBM 관리 컴포넌트 또는 공용 인터넷과의 HCX 관리 에지 통신을 사용 안함으로 설정하면 HCX 기능에 부정적인 영향을 줄 수 있습니다.
   {:important}

5. HCX Manager on {{site.data.keyword.cloud_notm}}가 배치되고 활성화되고 구성됩니다.
   * HCX Manager는 vCenter Server에 등록됩니다.
   * HCX Manager, vCenter Server(Platform Services Controller가 임베드됨) 및 NSX Manager가 구성됩니다.
   * HCX Fleet가 구성됩니다.
   * 로컬 및 원격 HCX 배치 컨테이너가 구성됩니다.
6. HCX Manager의 호스트 이름 및 IP 주소가 VMware vCenter Server on {{site.data.keyword.cloud_notm}}의 DNS 서버에 등록됩니다.

#### 인스턴스 세부사항 보기

인스턴스 세부사항을 보고 배치 상태를 확인할 수 있습니다. 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하고 **vCenter Server 인스턴스** 또는 **온프레미스 HCX 인스턴스** 테이블을 찾아 주문한 인스턴스에 대한 정보를 보십시오.

인스턴스가 성공적으로 배치되는 경우 이 주제의 *기술 스펙* 섹션에 설명되어 있는 컴포넌트가 VMware 가상 플랫폼에 설치되며, 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 서비스 정품 인증 키는 **온프레미스 HCX 인스턴스**에 나열됩니다. 

인스턴스의 상태가 **사용할 준비가 됨**으로 변경되고 이메일로 알림을 받습니다.

### 수행할 작업

온프레미스 HCX Enterprise Manager를 설치하고 HCX on {{site.data.keyword.cloud_notm}} 인스턴스에 대한 연결을 구성하십시오.

1. **배치된 인스턴스** 페이지에서 온프레미스 정품 인증 키를 찾으십시오.
  1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
  2. **vCenter Server 인스턴스** 테이블에서 **유형** 열을 검토하여 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스를 찾고 인스턴스 이름을 기록해 두십시오. 
  3. **온프레미스 HCX 인스턴스** 테이블로 스크롤하고 **이름** 열을 검토하여 *-OnPrem* 접두어로 정렬한 단일 노드 인스턴스와 동일한 이름을 가진 인스턴스를 찾으십시오. 
  4. **정품 인증 키** 필드에 있는 키를 기록해 두십시오.
2. HCX on {{site.data.keyword.cloud_notm}} HCX Manager 콘솔에서 온프레미스 HCX Enterprise Manager OVA(Open Virtual Appliance)를 얻으십시오.
  1. HCX Cloud 콘솔에 연결하십시오.
    1. **vCenter Server 인스턴스** 테이블에서 인스턴스 세부사항을 확인할 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스를 클릭하십시오.
    2. **액세스 정보**에서 vCenter 인증 정보를 찾아서 기록해 두십시오.
    3. 왼쪽 탐색 분할창에서 **서비스**를 클릭하십시오.
    4. **서비스** 페이지에서 **HCX on IBM Cloud**를 클릭하십시오.
    5. **HCX on IBM Cloud** 세부사항 페이지에서 **HCX Cloud IP**를 찾아서 기록해 두십시오.
    6. {{site.data.keyword.cloud_notm}} 사설 네트워크에 액세스하기 위해 VPN에 연결되었는지 확인하십시오.
    7. **HCX Cloud 콘솔 보기**를 클릭하십시오.
  2. **HCX Cloud 콘솔**에서 다음 단계를 완료하십시오.
      1. **관리** 탭을 클릭하십시오.
      2. **시스템 업데이트** 탭에서 **REQUEST DOWNLOAD LINK**를 클릭하십시오.
      3. **COPY LINK**를 클릭한 후 이 링크를 사용하여 온프레미스 vSphere 환경에 대한 액세스 권한으로 HCX Enterprise Client를 온프레미스 환경에 다운로드하십시오.
3. VMware vSphere Web Client에서 HCX Manager 가상 어플라이언스(HCX Manager)로 HCX Enterprise Client를 온프레미스 환경에 배치하십시오. 자세한 정보는 [Installing the HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html)를 참조하십시오.

사설 네트워크의 온프레미스 HCX Manager를 배치하고 해당 HCX Manager가 공용 네트워크에 액세스할 수 있도록 해야 합니다. NSX Edge, Vyatta 또는 유사한 게이트웨이를 사용하여 온프레미스 HCX Manager에 대한 인터넷 액세스를 허용할 수 있습니다. 사설 네트워크 액세스와 공용 네트워크 액세스에 사용된 게이트웨이가 서로 다른 경우, 사설 네트워크 액세스에 대한 정적 라우트를 작성하도록 기본 게이트웨이를 사용하여 공용 네트워크 액세스 및 온프레미스 **HCX Manager 관리 콘솔**을 허용하는 것이 좋습니다.  
    {:note}
4. 1단계에서 기록한 온프레미스 정품 인증 키를 사용하여 온프레미스 HCX Enterprise Manager VM을 활성화하십시오.
  1. OVA 배치 시 지정된 인증 정보를 사용하여 온프레미스 HCX Enterprise Manager VM에 로그인하십시오.
  2. 프롬프트가 표시되면 정품 인증 키를 입력하십시오.

  자세한 정보는 [HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html)을 참조하십시오.
  {:note}
5. 자체 서명된 SSL 인증서가 HCX on {{site.data.keyword.cloud_notm}} 서비스에서 생성되었습니다. 다음 단계를 완료하여 인증서를 온프레미스 HCX Manager로 가져와야 합니다.
    1. 온프레미스 **HCX Manager 관리 콘솔**에서 **관리** 탭을 클릭하십시오.
    2. 왼쪽 탐색 분할창에서 **신뢰할 수 있는 CA 인증서**를 클릭한 후 오른쪽의 **IMPORT**를 클릭하십시오.
    3. **URL**을 클릭한 후 적용할 인증서의 URL을 입력하십시오. 즉, {{site.data.keyword.vmwaresolutions_short}} 콘솔의 HCX on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 **HCX Cloud IP**(``https://<cloud-side public IP>``)입니다.
    4. **APPLY**를 클릭하십시오.
6. 초기 구성을 계속하고 상호연결을 빌드하십시오. 자세한 정보는 [Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html)를 참조하십시오.
7. VMware HCX의 네트워크를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장하십시오. 자세한 정보는 [Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g)를 참조하십시오.
8. 온프레미스와 {{site.data.keyword.cloud_notm}} 간에 VM을 마이그레이션하십시오. 자세한 정보는 [Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA)를 참조하십시오.

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 {{site.data.keyword.cloud_notm}} 계정에만 작성되는 {{site.data.keyword.vmwaresolutions_short}} 인프라 컴포넌트 관리해야 합니다.
{{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항이 콘솔과 동기화되지 않으며 환경을 불안정하게 할 수 있습니다.
{:important}

## 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스의 삭제 프로시저

마이그레이션 및 앱 현대화를 위한 단일 노드 평가판을 삭제하는 경우 다음 컴포넌트가 순차적으로 릴리스됩니다.

1. 배치된 모든 서비스
3. VMware 제품 라이센스
4. ESXi 서버
5. 서브넷
6. VLAN

리소스 종속성으로 인해 인스턴스 삭제 시 인스턴스의 컴포넌트가 즉시 릴리스되지 않습니다. 예를 들어, {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기의 종료 시에 발생하는 {{site.data.keyword.cloud_notm}} 인프라에 의한 ESXi 서버의 완전한 재확보 시점까지는 서브넷과 VLAN을 삭제할 수 없습니다. {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 일반적으로 청구 주기는 30일이고 서브넷 및 VLAN이 삭제되며 인스턴스 삭제가 완료됩니다.

삭제된 인스턴스에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
{:note}

마이그레이션 및 현대화를 위한 단일 노드 평가판 인스턴스를 삭제하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 삭제할 인스턴스를 찾으십시오.
3. **조치** 열에서 삭제 아이콘을 클릭하십시오.
   인스턴스의 상태가 **삭제 중**으로 변경됩니다. 인스턴스가 삭제되면 인스턴스의 컴포넌트가 릴리스되고 인스턴스의 상태가 **삭제됨**으로 변경됩니다.
4. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스 레코드를 제거하려면 다음 단계를 완료하십시오.
   1. **조치** 열에서 삭제 아이콘을 다시 클릭하십시오.
   2. **인스턴스 삭제** 창에서 **확인**을 클릭하십시오.

### 관련 링크

* [vCenter Server 및 IBM Cloud Private 안내서](../archiref/vcsicp/vcsicp-intro.html)
* [IBM Cloud Private의 티켓 열기](https://www.ibm.com/mysupport/s/?language=en_US)
* [VMware Hybrid Cloud Extension 문서](https://hcx.vmware.com/#/vm-documentation)
* [Obtaining the HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)

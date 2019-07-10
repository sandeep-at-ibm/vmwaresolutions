---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud 관리
{: #managinghtcc}

HyTrust CloudControl on {{site.data.keyword.cloud}} 서비스(HTCC)를 관리하려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 HTCC WebGUI에 액세스하거나 vSphere Web Client에서 HTCC 콘솔에 액세스하십시오.

## IBM Cloud for VMware Solutions 콘솔에서 HyTrust CloudControl WebGUI에 액세스
{: #managinghtcc-accessing-webgui}

기본 또는 보조 HTCC 어플라이언스의 WebGUI에 로그인하려면 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 WebGUI 인증 정보를 사용하십시오.

## vSphere Web Client에서 HyTrust CloudControl 콘솔에 액세스
{: #managinghtcc-accessing-console}

HTCC 콘솔을 vSphere Web Client에서 액세스하려면 다음 프로시저를 사용하십시오.
1. vSphere Web Client에서 이름이 **CC1** 및 **CC2**인 가상 머신을 찾으십시오.
2. **CC1** 또는 **CC2**를 마우스 오른쪽 단추로 클릭한 후 **콘솔 열기**를 클릭하십시오.
3. HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 콘솔 인증 정보를 사용하여 콘솔에 로그인하십시오.

자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)를 참조하십시오.

## HyTrust CloudControl VM에 대한 인터넷 액세스 사용
{: #managinghtcc-internet-access}

HTCC 5.5.1 이상의 경우 {{site.data.keyword.vmwaresolutions_short}}는 콜홈 기능이 사용으로 설정된 HyTrust 라이센스의 자동 갱신 기능을 제공합니다. 사설 전용이 아닌 vCenter Server 인스턴스의 경우 HTCC는 방화벽 및 관리 서비스 ESG **mgmt-nsx-edge**에서 정의되는 SNAT(Source Network Address Translation) 규칙으로 배치됩니다. 

이 규칙을 통해 HyTrust 가상 머신(VM)에 대한 인터넷 액세스를 사용으로 설정할 수 있습니다. 인터넷 액세스가 사용으로 설정되지 않으면 HTCC 설치에 적용되는 라이센스가 1년 후에 만료됩니다. 

사설 전용 vCenter Server 환경의 경우 VMware NSX Edge Services Gateway(ESG) **mgmt-nsx-edge**가 추가되지 않습니다. 이에 따라 펌웨어 및 SNAT 규칙이 정의되지 않습니다. 결과적으로 인터넷 연결은 사설 전용 인스턴스에 대해 사용으로 설정되지 않으며 HyTrust 라이센스는 매년 만료됩니다.
{:note}

### 정의된 방화벽 및 SNAT 규칙을 찾는 프로시저
{: #managinghtcc-proc-find-firewall}

1. VMware vSphere Web Client(FLEX)에 로그인하여 ESG **mgmt-nsx-edge**를 찾으십시오.
2. **홈 > 네트워킹 및 보안 > NSX Edges**를 클릭하십시오.
3. ESG **mgmt-nsx-edge**를 두 번 클릭하고 **관리** 탭을 클릭하십시오.
4. **펌웨어** 탭으로 이동하여 HyTrust 규칙을 찾으십시오. 소스 IP 주소를 적어 두십시오. 이 주소는 HyTrust VM의 주소입니다. 
5. **NAT** 탭으로 이동하여 HyTrust VM에 대해 작성된 SNAT 규칙을 찾으십시오. 소스 IP 주소는 이전 단계에서 적어 놓은 IP 주소와 일치합니다. 

### HTCC에 대한 인터넷 연결을 사용으로 설정하는 프로시저
{: #managinghtcc-enable-internet}

다음 단계는 라이센스 업그레이드에 사용되는 기본 가상 머신(VM)에서 HTCC 네트워크 설정을 업데이트하는 데 적용됩니다. 보조 VM에 대한 설정을 업데이트할 필요는 없습니다.
{:note}

1. 이전 프로시저의 1 - 3단계를 완료하십시오. 
2. **설정**을 클릭한 후 **인터페이스**를 클릭하십시오. 사설 업링크의 IP 주소를 적어 두십시오. 이 주소는 새 기본 게이트웨이가 됩니다. 
3. HyTrust CloudControl on IBM Cloud 서비스 세부사항 페이지로 이동하여 **HTCC 웹 UI 보기**를 클릭하고 서비스 세부사항 페이지에서 인증 정보로 로그인하십시오. 
4. 기존의 기본 게이트웨이를 적어 두십시오. 예를 들어, HTCC 5.5.1의 경우 **구성 > 네트워크**를 클릭하십시오. 나열된 게이트웨이 IP 주소를 적어 두십시오. 이 주소는 정적 라우트의 게이트웨이가 됩니다. 
5. 정적 라우트를 추가하십시오. 예를 들어, HTCC 5.5.1의 경우 **구성 > 정적 라우트**를 클릭하십시오. **추가**를 클릭하고 다음 정보를 입력한 후 **확인**을 클릭하십시오.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. 기본 게이트웨이를 변경하십시오. 예를 들어, HTCC 5.5.1의 경우 **구성 > 네트워크**를 클릭하고 **게이트웨이** 필드의 IP 주소를 3단계에서 적어 놓은 IP 주소로 대체한 후 **저장**을 클릭하십시오. 

  기본 게이트웨이를 변경하기 전에 정적 라우트를 설정했는지 확인하십시오. 그렇지 않으면, 웹 콘솔에 도달할 수 없게 됩니다.
  {:important}

  이제 기본 VM에 인터넷에 대한 액세스 권한이 제공됩니다. 

7. 기본 VM에 액세스 권한이 있는지 확인하려면 공인 IP 주소 또는 웹 사이트에 대해 `ping` 명령을 실행하십시오. 이를 수행하려면 vCenter로 다시 돌아가서 **CC1 > Open 콘솔 열기**를 마우스 오른쪽 단추로 클릭하십시오. HyTrust CloudControl on IBM Cloud service 세부사항 페이지의 콘솔 인증 정보를 사용하여 콘솔에 로그인하십시오. `ping` 명령(예: `ping www.ibm.com`)을 실행하면 즉각적인 응답을 받게 됩니다. `Ctrl + C`를 눌러 Ping을 종료하고 패킷 손실이 0%인지 확인하십시오.

## 관련 링크
{: #managinghtcc-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: HTKC WebGUI, HTKC console, enable internet HTKC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl on IBM Cloud 관리
{: #managinghtkc}

HyTrust KeyControl on {{site.data.keyword.cloud}} 서비스(HTKC)를 관리하려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 HTKC Web GUI에 액세스하거나 vSphere Web Client에서 HTKC 콘솔에 액세스하십시오.

## IBM Cloud for VMware Solutions 콘솔에서 HyTrust KeyControl Web GUI에 액세스
{: #managinghtkc-accessing-webgui}

기본 또는 보조 HTKC 어플라이언스의 Web GUI에 로그인하려면 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 WebGUI 인증 정보를 사용하십시오.

## vSphere Web Client에서 HyTrust KeyControl 콘솔에 액세스
{: #managinghtkc-accessing-console}

HTKC 콘솔을 vSphere Web Client에서 액세스하려면 다음 프로시저를 사용하십시오.
1. vSphere Web Client에서 {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지의 HyTrust KeyControl에서 찾은 IP 주소와 일치하는 이름이 **KC1** 및 **KC2**로 시작하는 가상 머신을 찾으십시오.
2. **KC1** 또는 **KC2**를 마우스 오른쪽 단추로 클릭한 후 **콘솔 열기**를 클릭하십시오.
3. HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 콘솔 인증 정보를 사용하여 콘솔에 로그인하십시오.

자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)를 참조하십시오.

## HyTrust KeyControl VM에 대한 인터넷 액세스 사용
{: #managinghtkc-internet-access}

HTKC 4.3.2 이상의 경우 {{site.data.keyword.vmwaresolutions_short}}는 콜홈 기능이 사용으로 설정된 HyTrust 라이센스의 자동 갱신 기능을 제공합니다. 사설 전용이 아닌 vCenter Server 인스턴스의 경우 HTKC는 방화벽 및 관리 서비스 ESG **mgmt-nsx-edge**에서 정의되는 SNAT(Source Network Address Translation) 규칙으로 배치됩니다.

이 규칙을 통해 HyTrust 가상 머신(VM)에 대한 인터넷 액세스를 사용으로 설정할 수 있습니다. 인터넷 액세스가 사용으로 설정되지 않으면 HTKC 설치에 적용되는 라이센스가 1년 후에 만료됩니다.

사설 전용 vCenter Server 환경의 경우 VMware NSX Edge Services Gateway(ESG) **mgmt-nsx-edge**가 추가되지 않습니다. 이에 따라 펌웨어 및 SNAT 규칙이 정의되지 않습니다. 결과적으로 인터넷 연결은 사설 전용 인스턴스에 대해 사용으로 설정되지 않으며 HyTrust 라이센스는 매년 만료됩니다.
{:note}

### 정의된 방화벽 및 SNAT 규칙을 찾는 프로시저
{: #managinghtkc-proc-find-firewall}

1. VMware vSphere Web Client(FLEX)에 로그인하여 ESG **mgmt-nsx-edge**를 찾으십시오.
2. **홈 > 네트워킹 및 보안 > NSX Edges**를 클릭하십시오.
3. ESG **mgmt-nsx-edge**를 두 번 클릭하고 **관리** 탭을 클릭하십시오.
4. **펌웨어** 탭으로 이동하여 HyTrust 규칙을 찾으십시오. 소스 IP 주소를 적어 두십시오. 이 주소는 HyTrust VM의 주소입니다.
5. **NAT** 탭으로 이동하여 HyTrust VM에 대해 작성된 SNAT 규칙을 찾으십시오. 소스 IP 주소는 이전 단계에서 적어 놓은 IP 주소와 일치합니다.

### HTKC에 대한 인터넷 연결을 사용으로 설정하는 프로시저
{: #managinghtkc-proc-enable-internet}

1. 이전 프로시저의 1 - 3단계를 완료하십시오.
2. **설정**을 클릭한 후 **인터페이스**를 클릭하십시오. 사설 업링크의 IP 주소를 적어 두십시오. 이 주소는 새 기본 게이트웨이가 됩니다.
3. **홈 > 호스트 및 클러스터**를 클릭하고 HyTrust VM을 찾으십시오. VM 중 하나를 오른쪽 단추로 클릭하고 **콘솔 열기**를 클릭하십시오.
4. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있는 콘솔 인증 정보를 사용하여 콘솔에 로그인하십시오.
5. VM에서 현재 게이트웨이 IP 주소를 가져오려면 **네트워크 설정 관리 > 현재 네트워크 구성 표시**를 클릭하십시오. **게이트웨이**에 대해 나열된 IP 주소를 적어 두십시오. 이 주소는 정적 라우트에 사용되는 게이트웨이가 됩니다.
6. VM에 대한 정적 라우트를 설정하려면 **네트워크 설정 관리 > 정적 라우트 관리 > 정적 라우트 추가**를 클릭하십시오. **네트워크 주소**를 `10.0.0.0/8`로 설정하고 **게이트웨이**를 이전 단계에서 적어 놓은 IP 주소로 설정하십시오.
7. VM에 대한 기본 게이트웨이를 설정하려면 **네트워크 설정 관리 > 현재 네트워크 구성 변경**을 클릭하십시오. 경고 메시지가 표시되면 **확인**을 클릭한 후 **사용자 정의 구성**을 클릭하십시오. **게이트웨이** 필드를 2단계에서 적어 놓은 사설 업링크 IP 주소로 설정한 후 **확인**을 클릭하십시오. 새 네트워크 구성이 설치되고 네트워크 서비스가 다시 시작될 때까지 기다리십시오.
8. HyTrust SecureOS 재인증을 묻는 메시지가 표시되면 **확인**을 클릭하고 이 설치를 위해 다른 HyTrust VM의 IP 주소를 입력하십시오. 16자의 비밀번호 문구가 요청되면 Enter를 눌러 기본 메뉴로 돌아가십시오. 현재 네트워크 구성을 확인하여 변경사항이 적용되었는지 알아보십시오.
9. VM에 인터넷에 대한 액세스 권한이 있는지 확인하려면 공인 IP 주소 또는 웹 사이트에 ping을 실행하십시오. **네트워크 설정 관리 > 네트워크 진단 도구 > 다른 서버의 인바운드 포트 테스트**를 클릭하십시오. 공용 웹 사이트 주소(예: `www.ibm.com`)를 입력하고 **확인**을 클릭하고 포트(또는 테스트할 다른 포트)에 대해 `80 443`을 입력하면 `80 (OK) 443 (OK)`와 유사한 메시지와 함께 인바운드 포트를 표시하는 즉각적인 응답을 받게 됩니다.
10. 다른 HyTrust VM에 대해 3 - 9단계를 반복하십시오.

## 관련 링크
{: #managinghtkc-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 웹 사이트](https://www.hytrust.com/){:external}

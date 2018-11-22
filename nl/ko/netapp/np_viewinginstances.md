---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select 인스턴스 보기

서로 다른 사용자 계정에 대해 프로비저닝된 NetApp ONTAP Select 인스턴스의 요약과 자세한 정보를 봅니다.

## NetApp ONTAP Select 인스턴스 요약을 보는 프로시저

사용자 계정에 대해 프로비저닝된 모든 NetApp ONTAP Select 인스턴스의 요약을 보려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.vmwaresolutions_full}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. 콘솔 배너에서 사용자 계정 아이콘을 클릭한 다음 **계정** 필드를 클릭하여 인스턴스를 확인하려는 사용자 계정을 선택하십시오.
3. **NetApp ONTAP Select 인스턴스** 테이블에서, 선택된 사용자 계정에서 프로비저닝된 인스턴스의 목록을 보십시오.

표 1. NetApp ONTAP Select 인스턴스 항목

|항목        |설명       |  
|:------------- |:--------------- |
|이름 |인스턴스의 이름입니다. |
|버전 |인스턴스의 버전입니다. |  
|위치 |인스턴스가 호스팅되는 데이터 센터입니다. |
|작성 시간 |인스턴스가 작성된 날짜 및 시간입니다. |   
|상태 |인스턴스의 상태입니다. 상태는 다음 값 중 하나를 포함할 수 있습니다.<ul><li>작성 중: 인스턴스가 작성되는 중입니다.</li><li>빌드 중: 인스턴스가 구성되는 중입니다.</li><li>사용할 준비가 됨: 인스턴스가 사용할 준비가 되었습니다.</li><li>수정 중: 인스턴스가 수정되는 중입니다.</li><li>실패: 작성, 구성 또는 수정 프로세스가 실패했습니다.</li><li>삭제 중: 인스턴스가 삭제되는 중입니다.</li><li>삭제 오류: 인스턴스가 삭제되는 중에 오류가 발생했습니다.</li><li>삭제됨: 인스턴스가 삭제되었습니다.</li></ul>|

## NetApp ONTAP Select 인스턴스 특성 세부사항을 보는 프로시저

인스턴스의 특성 세부사항을 보려면 다음 작업을 수행하십시오.

1. **NetApp ONTAP Select 인스턴스** 테이블에서 인스턴스 이름을 클릭하십시오.
2. **특성**에서 인스턴스의 세부사항을 보십시오.

표 2. NetApp ONTAP Select 인스턴스 특성

|특성        |설명       |
|:--------------- |:----------------- |
|이름 |인스턴스의 이름입니다. |
|ID |인스턴스의 ID입니다. |
|위치 |인스턴스가 호스팅되는 데이터 센터입니다. |
|배치된 버전 |{{site.data.keyword.vmwaresolutions_short}}의 배치된 버전입니다. |
|vCenter 버전 |VMware vCenter Server의 버전입니다.<br><br>**참고**: {{site.data.keyword.vmwaresolutions_short}} 콘솔에 표시된 vCenter Server 버전과 VMware vSphere Web Client 사이에 약간의 차이점이 있습니다. 그러나 모두 올바릅니다. |
|NSX for vSphere |VMware NSX for vSphere 제품 버전입니다. |
|NSX 라이센스 에디션 |VMware NSX 라이센스의 버전 및 에디션입니다. |
|NetApp 버전 |NetApp ONTAP Select의 버전입니다. |
|NetApp 라이센스 유형 |NetApp ONTAP Select 라이센스의 유형입니다. |
|DNS, 루트 도메인 |루트 도메인 이름은 인스턴스의 DNS(Domain Name System) 도메인 이름 및 Microsoft Active Directory(AD) 포리스트 루트 이름입니다. |
|DNS, SSO 도메인 |SSO 도메인은 vSphere Single Sign-On 도메인입니다. SSO 도메인 이름은 배치된 모든 NetApp ONTAP Select 인스턴스(`vsphere.local` 값 포함)에 대해 설정됩니다. |
|DNS, 하위 도메인 |하위 도메인은 로컬 NetApp ONTAP Select 인스턴스 호스트 이름이 상주하는 루트 도메인 이름의 DNS 하위 도메인 이름입니다. 하위 도메인 이름은 `<subdomain_label>.<root_domain>` 형식으로 되어 있습니다. |
|상태 |인스턴스의 상태입니다. |

## NetApp ONTAP Select 인스턴스에 대한 액세스 정보를 보는 프로시저

**액세스 정보**에서 인스턴스 관련 컴포넌트의 액세스 정보를 보십시오. 이 비밀번호는 시스템에서 생성된 초기 비밀번호입니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 비밀번호를 변경하는 경우 이 비밀번호는 인스턴스 요약 페이지에서 업데이트되지 않습니다.

표 3. NetApp ONTAP Select 인스턴스 관련 컴포넌트의 액세스 정보

|컴포넌트        |설명       |
|:---------------- |:----------------- |
|AD/DNS IP |두 AD 서버의 IP 주소입니다. |
|AD/DNS FQDN |AD/DNS 서버의 완전한 도메인 이름입니다. |
|AD/DNS ADMIN(원격 데스크탑) |원격 데스크탑 연결을 통해 AD 서버에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |
|NSX Manager IP |NSX Manager의 IP 주소입니다. |
|NSX Manager FQDN |NSX Manager의 완전한 도메인 이름입니다. |
|NSX Manager HTTP |NSX Manager 웹 콘솔에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |
|NetApp 클러스터 IP |NetApp ONTAP Select 클러스터의 IP 주소입니다. |
|NetApp 클러스터 FQDN |NetApp ONTAP 클러스터의 완전한 도메인 이름입니다. |
|NetApp 클러스터 HTTPS |NetApp ONTAP Select 클러스터에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |
|NetApp Deploy 도구 IP |NetApp ONTAP Select Deploy 가상 머신의 IP 주소입니다. |
|NetApp Deploy 도구 FQDN |NetApp ONTAP Select Deploy의 완전한 도메인 이름입니다. |
|NetApp Deploy 도구 HTTPS |NetApp ONTAP Select Deploy 가상 머신에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |
|PSC IP |Platform Services Controller의 IP 주소입니다. |
|PSC FQDN |PSC의 완전한 도메인 이름입니다. |
|PSC ADMIN |PSC 웹 콘솔에 액세스하는 데 사용할 수 있는 VMware vCenter Single Sign-On 사용자 이름 및 비밀번호입니다. |
|PSC SSH |SSH 연결을 통해 PSC VM에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |
|vCenter IP |vCenter Server의 IP 주소입니다. |
|vCenter FQDN |vCenter Server의 완전한 도메인 이름입니다. |
|vCenter ADMIN |vSphere Web Client를 사용하여 vCenter Server에 로그인하는 데 사용할 수 있는 VMware vCenter Single Sign-On 사용자 이름 및 비밀번호입니다. |
|vCenter SSH |SSH 연결을 통해 vCenter Server VM에 액세스하는 데 사용할 수 있는 사용자 이름 및 비밀번호입니다. |

## NetApp ONTAP Select 인스턴스에 대한 배치 히스토리를 보는 프로시저

왼쪽 탐색 분할창에서 **배치 히스토리**를 클릭하여 인스턴스에 대한 배치 히스토리를 보십시오.

표 4. NetApp ONTAP Select 인스턴스 배치 히스토리

|항목        |설명       |  
|:------------|:------------- |
|날짜 |인스턴스 상태가 변경된 날짜 및 시간입니다. |
|요약 |변경의 세부사항입니다. |

인스턴스 배치 또는 인스턴스 삭제 중에 오류가 발생하는 경우 {{site.data.keyword.cloud_notm}} 지원 팀에 자동으로 알림이 전송됩니다. 티켓의 상태에 대해 문의하려는 경우에는 [IBM 지원 센터에 문의](../vmonic/trbl_support.html)할 수 있습니다.

## NetApp ONTAP Select 클러스터 보기

1. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오.
2. **클러스터**에서 NetApp ONTAP Select 클러스터에 대한 요약을 보십시오.

	표 5. NetApp ONTAP Select 클러스터 항목

	 <table>
	   <tr>
	     <th>항목</th>
	     <th>설명</th>
	   </tr>
	   <tr>
	     <td>이름</td>
	     <td>클러스터의 이름입니다.</td>
	   </tr>
	   <tr>
	     <td>ESXi 서버</td>
	     <td>클러스터에 있는 ESXi 서버의 수입니다.</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>클러스터에 있는 ESXi 서버의 CPU 스펙입니다.</td>
	   </tr>
	   <tr>
	      <td>유효 스토리지</td>
	      <td>클러스터에 있는 ESXi 서버의 총 디스크 용량입니다.</td>
	   </tr>
	   <tr>
	      <td>메모리</td>
	      <td>클러스터에 있는 ESXi 서버의 총 메모리 크기입니다.</td>
	   </tr>
	   <tr>
	      <td>데이터 센터 위치</td>
	      <td>클러스터가 호스팅되는 데이터 센터입니다. 인스턴스의 데이터 센터 위치와 동일합니다.</td>
	   </tr>
		 <tr>
		   <td>팟(Pod)</td>
			 <td>클러스터가 작성된 팟(Pod)입니다.</td>
		 </tr>
		 <tr>
		  <td>상태</td>
			<td>클러스터의 상태입니다. 상태는 다음 값 중 하나를 포함할 수 있습니다.<ul><li>초기화 중: 클러스터가 작성되어 구성되는 중입니다.</li><li>수정 중: 클러스터가 수정되는 중입니다.</li><li>사용할 준비가 됨: 인스턴스가 사용할 준비가 되었습니다.</li></ul></td>
		 </tr>
		 <tr>
		  <td>조치</td>
			<td>클러스터를 삭제하려면 **삭제** 아이콘을 클릭하십시오.</td>
		 </tr>
	 </table>

3. 클러스터 이름을 클릭하여 ESXi 서버 세부사항을 보십시오.

표 6. NetApp ONTAP Select 클러스터의 ESXi 서버 세부사항

|항목        |설명       |  
|:------------|:----------------- |
|이름 |ESXi 서버의 이름으로, 형식은 `<host_prefix><n>.<subdomain_label>.<root_domain>`이며 여기서<br><br>`host_prefix`는 호스트 이름 접두부입니다. `n`은 서버의 순서입니다. `subdomain_label`은 하위 도메인 레이블입니다. `root_domain`은 루트 도메인 이름입니다. |
|버전 |ESXi 서버의 버전입니다. |
|인증 정보 |ESXi 서버에 액세스하는 데 사용되는 사용자 이름 및 비밀번호입니다. |
|사설 IP |ESXi 서버의 사설 IP 주소입니다. |
|상태 |ESXi 서버의 상태이며, 다음 값 중 하나일 수 있습니다.<ul><li>활성: ESXi 서버가 사용할 준비가 되었습니다.</li><li>삭제 중: ESXi 서버가 삭제되는 중입니다.</li></ul> |

## 수행할 작업

{{site.data.keyword.vmwaresolutions_short}} 콘솔, VMware vSphere Web Client 또는 NetApp 콘솔에서 인스턴스를 관리하십시오.

인스턴스 요약 페이지에서 **vCenter 콘솔**을 클릭하여 vSphere Web Client로 이동하고 ESXi 서버 관리를 시작하기 전에, {{site.data.keyword.CloudDataCent_notm}}의 VPN 포털에 로그인해야 합니다. vSphere Web Client에 액세스하기 전에 **vCenter 콘솔** 단추 위에 마우스를 올려 놓고 지시사항에 따라 모든 요구사항을 충족하고 필요한 단계를 완료했는지 확인하십시오.
{:important}

로그인 지시사항을 완료하는 데 도움이 되는 자세한 정보는 다음 주제를 검토하십시오.

*  vSphere Web Client에 액세스하기 전의 요구사항 및 필요한 단계는 [vSphere Web Client에 연결하는 중에 제한시간이 초과함](../vmonic/trbl_timeout_vc_console.html)을 참조하십시오.
*  VPN을 사용하여 {{site.data.keyword.cloud_notm}} 인프라 사설 네트워크에 로그인하기 위한 액세스 지점의 목록은 [VPN 액세스](http://www.softlayer.com/vpn-access){:new_window}를 참조하십시오.
*  vSphere Web Client를 사용하여 OVF(Open Virtualization Format) 파일을 배치할 때 문제점이 발생하면 [vSphere Web Client를 사용하여 OVF 파일 배치](../vmonic/trbl_deploy_ovf.html)를 참조하십시오.

### 관련 링크

* [NetApp ONTAP Select 인스턴스 주문](np_orderinginstances.html)
* [NetApp ONTAP Select 인스턴스 삭제](np_deletinginstance.html)
* [NetApp ONTAP Select 배치에 전용 스토리지 연결](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)

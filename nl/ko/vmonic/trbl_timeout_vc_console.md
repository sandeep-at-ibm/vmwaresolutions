---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

# VMware vSphere Web Client에 연결하는 중에 제한시간 초과
{: #trbl_timeout_vc_console}

## 문제점
{: #trbl_timeout_vc_console-problem}

vSphere Web Client로 연결을 시도할 때 다음 제한시간 초과 오류가 발생할 수 있습니다.

`The server at <IP_address> is taking too long to respond.`

## 해결
{: #trbl_timeout_vc_console-resolution}

다음 단계를 사용하여 문제점을 조사하고 수정하십시오.

1. **vCenter 콘솔** 단추 위에 마우스를 올려 놓을 때 표시되는 단계를 완료했는지 확인하십시오. 사용자의 편의를 위해
   단계도 다음과 같이 표시됩니다.   
   1. 브라우저용 Adobe Flash Player 플러그인을 설치하십시오.   
   2. {{site.data.keyword.slportal_full}}에서 VPN 비밀번호를 작성하십시오.    
   3. {{site.data.keyword.cloud_notm}} 인프라 VPN 인증 정보를 사용하여 [데이터 센터 VPN에 로그인](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#login-to-the-vpn)하십시오.    
   4. 로컬 컴퓨터에서 IP 주소 및 PSC(Platform Services Controller)의 호스트 이름 맵핑을 호스트 파일에 추가하십시오. 다음 형식을 사용하십시오. 

      ```javascript
      IPAddress              HostName
      ```

2. 다음 단계에서 필요하므로 표시되는 IP 주소를 기록해 놓으십시오.
3. {{site.data.keyword.cloud_notm}} 인프라 VPN에 대한 액세스 권한이 있는지 확인하십시오. {{site.data.keyword.slportal}}에서 다음 단계를 완료하십시오.
   1. **계정 > VPN 액세스**를 클릭하십시오.
   2. **VPN 액세스** 열에서 **SSL 링크**를 클릭하십시오.
   3. **사용자 이름에 대한 VPN 액세스** 페이지에서 **서브넷 액세스** 옵션을 **수동**으로 설정하십시오.
   4. 같은 페이지에서 IP 주소/호스트 이름 쌍의 서브넷을 찾으십시오. 자세한 정보는 **2단계**를 참조하십시오.    

      예를 들어, 인스턴스의 IP 주소가 `xx.yyy.zz.15`이고 vCenter의 IP 주소가 `xx.yyy.zz.10`인 경우 서브넷 `xx.yyy.zz.0/26`에 대한 액세스 권한을 부여해야 합니다.

   5. 해당 서브넷의 **액세스 부여** 선택란을 선택한 후 **저장**을 클릭하십시오.

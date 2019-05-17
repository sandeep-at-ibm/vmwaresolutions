---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

# VMware vSphere Web Client를 사용하여 OVF 파일 배치
{: #trbl_deploy_ovf}

## 해결
{: #trbl_deploy_ovf-resolution}

vSphere Web Client를 사용하여 OVF(Open Virtualization Format) 파일을 배치하려면 다음 프로시저를 수행하십시오.
1. OVF 파일 배치 시도 전에 다음 호스트 정보를 `/etc/hosts` 파일에 추가하십시오.

   * PSC(Platform Services Controller)를 위한 호스트 정보
   * VMware ESXi 서버를 위한 호스트 정보
   * vCenter를 위한 호스트 정보
2. 정보가 추가되었는지 확인하려면 `/etc/hosts` 파일을 검사하십시오. 호스트 파일의 예는 다음 목록과 같습니다.

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. {{site.data.keyword.slportal_full}}에서 필요한 모든 가상 사설망(VPN)에 대한 액세스 권한이 있는지 확인하십시오. 이 예에서는 `10.131.7.xx` 및 `10.131.9.xxx`입니다.
4. 데이터 센터의 VPN에 로그인하십시오.
5. **vCenter**를 클릭하여 vSphere Web Client에 액세스하십시오.
6. 호스트를 오른쪽 마우스 단추로 클릭하고 `.ovf` 파일을 배치하십시오.

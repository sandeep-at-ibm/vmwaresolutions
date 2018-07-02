---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# Virtual SAN 상태 경보 및 경고

## 문제점
VMware vSphere Web Client **모니터** 페이지에서 Virtual SAN 상태 문제와 관련된 경보 및 경고가 표시될 수 있습니다.

## 해결
경고가 문제가 되지 않으며 기능상의 문제점을 표시하지 않습니다. 그러나 vSphere Web Client에서 경고를 지우려면
다음 프로시저를 수행하십시오.

1. http://partnerweb.vmware.com/service/vsan/all.json 사이트로 이동한 후 로컬 시스템에서 `all.json`이라는 이름으로 JSON 파일을 저장하십시오.
2. [vCenter 콘솔 제한시간 초과](trbl_timeout_vc_console.html)의 단계를 완료했는지 확인하십시오.
3. Cloud Foundation 인스턴스의 세부사항 페이지에서 **vCenter 콘솔** 단추를 클릭한 후 {{site.data.keyword.vmwaresolutions_full}} 콘솔에 표시된 신임 정보를 사용하여 vSphere Web Client에 로그인하십시오.
4. vSphere Web Client에서 **관리 > 설정**으로 이동하여 **Virtual SAN > 상태 > HCL 데이터베이스** 섹션을 여십시오. **파일에서 업데이트**를 클릭한 후 이전에 저장한 `all.json` 파일을 업로드하십시오.
5. 경고를 지우려면 vSphere Web Client의 오른쪽 상단에 있는 **알람** 분할창으로 이동하십시오. 각 알람을 오른쪽 마우스 단추로 클릭하고 **초록색으로 재설정**을 선택하십시오.

자세한 정보는 [How to download offline vSAN HCL file for vSAN Health Check Plugin](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}을 참조하십시오.

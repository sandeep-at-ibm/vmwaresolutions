---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# VCSA 업데이트 및 SSO 링크된 vCenter
{: #vum-updating-vcsa}

## PSC 및 VCSA 업데이트
{: #vum-updating-vcsa-psc-vcsa-update}

이 섹션은 VCSA(vCentre Server Appliance) 및 PSC(Platform Services Controller) 둘 다와 관련되어 있습니다. 두 어플라이언스는 모두 VCSA 어플라이언스이지만 역할은 서로 다릅니다. 외부 PSC로 vSphere를 업그레이드하는 경우에는 우선 PSC를 업그레이드한 후에 VCSA, 그리고 ESXi 호스트를 업그레이드하고 마지막으로 가상 머신의 VMware 도구와 하드웨어 버전을 업그레이드하십시오.

VUM은 PSC/VCSA를 업데이트하지 않습니다. 다음 정보는 이러한 어플라이언스를 업데이트하는 프로세스에 대해 설명합니다. VMware vCenter Server on {{site.data.keyword.cloud}} 인스턴스에 배치된 PSC/VCSA에는 인터넷 액세스가 없으므로 먼저 업데이트 번들을 점프 서버에 다운로드해야 합니다.

PSC/VCSA는 vSphere Web Client가 아닌 어플라이언스 관리 콘솔을 통해 업데이트됩니다. PSC/VCSA 어플라이언스 관리 콘솔은 브라우저, PSC/VCSA IP 주소 및 포트 5480을 사용하여 액세스됩니다.

업데이트하려면 우선 어플라이언스의 스냅샷 또는 PSC/VCSA의 백업을 시작해야 합니다. 모든 항목이 예상대로 작동하는지 확인한 후 성능 저하를 방지하기 위해 며칠 내에 스냅샷을 제거하십시오. 또한 업그레이드를 시도하기 전에 VMware 릴리스 정보를 검토하여 지정된 릴리스에 대한 특정 지시사항을 파악하십시오.

PSC/VCSA를 업데이트하려면 다음 단계를 따르십시오.
1. VMware 패치 [다운로드 센터](https://my.vmware.com/group/vmware/patch#search)로 이동하여 로그인한 후 **제품별 검색** 메뉴에서 VC를 선택하여 업데이트를 다운로드할 수 있습니다. 적절한 패치를 선택하고 **다운로드**를 클릭하십시오.
2. vSphere Web Client를 사용하여 ISO 파일을 vCenter 데이터 저장소로 업로드하십시오.
3. 업데이트 ISO 파일을 vCenter 서버에 마운트하십시오.
4. vCenter 서버의 스냅샷을 작성하십시오.
5. `https://pscip:5480`(PSC의 경우) 또는 `https://vcenterip:5480`(VCSA의 경우)에서 vCenter 어플라이언스 관리 콘솔에 로그인하십시오.
6. **업데이트** 섹션으로 이동하여 **업데이트 확인**을 선택한 후 **CDROM 확인**을 클릭하십시오. 업데이트가 나열됩니다.
7. **업데이트 설치**를 선택하고 EULA에 **동의**하십시오. 업데이트가 설치됩니다.
8. 업데이트가 완료된 후 어플라이언스 관리 콘솔로 되돌아가서 콘솔을 다시 시작하도록 선택해야 합니다.
9. vSphere Web Client에 다시 로그인하여 오류가 있는지 확인하십시오. **홈** > **호스트 및 클러스터**를 선택한 후 데이터 센터 또는 클러스터를 선택하고 **Update Manager 탭**을 선택한 후 **업데이트 스캔**을 클릭하여 VUM의 수동 스캔을 완료하십시오. 매뉴얼 스캔으로 오류가 발생하는 경우 [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284)를 참조하십시오.
10. 테스트 후 취소해야 하는 경우 스냅샷으로 되돌리거나 이전 백업을 사용하여 vCenter를 복원하십시오.

## SSO 링크된 vCenter Server 인스턴스
{: #vum-updating-vcsa-sso-vcenter}

기본 및 보조 vCenter Server 인스턴스가 있는 경우 VCSA가 단일 vCenter 싱글 사인온(SSO) 도메인에 있도록 구성됩니다. 각 VCSA에는 배치된 VUM 인스턴스가 있습니다. 수정하는 구성 특성은 사용자가 지정하는 VLM 인스턴스에만 적용되며 그룹에 있는 다른 인스턴스에 전파되지 않습니다.

탐색줄에서 VUM 인스턴스가 등록된 VCSA의 이름을 선택하여 VUM 인스턴스를 지정할 수 있습니다. 기준선, 기준선 그룹, 스캔을 관리하고 VUM 인스턴스가 등록된 VCSA에서 관리되는 인벤토리 오브젝트만 수정할 수도 있습니다.

## 관련 링크
{: #vum-updating-vcsa-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 디지털 기술 업무](https://ibm-dte.mybluemix.net/ibm-vmware)(데모)

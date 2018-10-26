---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

# 원시 NIC 드라이버 적용

ESXi 6.5에는 이전 vmklinux 드라이버를 대체하는 많은 새 원시 드라이버가 포함되어 있습니다. 대부분의 새 원시 드라이버는 설치 또는 업그레이드 후 기본적으로 사용으로 설정되지만 새 원시 드라이버 중 세 개는 기본적으로 사용 안함으로 설정됩니다. 이러한 원시 드라이버가 해당 vmklinux 드라이버의 기능을 완전히 지원하지 않기 때문입니다.

ixgben은 vmklinux net-ixgbe 드라이버를 대체하지만 SR-IOV 및 SW FcOE를 지원하지 않는 원시 드라이버입니다. vSphere ESXi 호스트가 프로비저닝될 때 ICVS 자동화가 이 드라이버를 사용으로 설정하지 않았을 수 있습니다. 이 드라이버가 제공하는 성능 이점을 얻으려면 이 드라이버를 사용으로 설정하는 것이 좋습니다. 이 부록에 설명된 다음 프로시저는 vSphere 명령행(vCLI)을 사용하여 원시 드라이버를 사용으로 설정하고 사용 안함으로 설정하는 방법을 보여줍니다.

이 태스크를 시작하기 전에 [IBM Cloud 인프라 포털](https://control.softlayer.com/devices)에서 모든 실제 호스트 IPMI IP 주소, 로그인 ID 및 비밀번호를 검색하십시오. 이는 백아웃에서 또는 호스트에 대한 직접 네트워크 액세스가 없는 경우에 업그레이드의 진행상태를 확인하기 위해 필요합니다.

각 호스트에 대해 다음을 연속하여 수행하십시오.
1. vSphere Web Client에서 **홈** > **호스트 및 클러스터**를 선택하여 vSphere ESXi 호스트를 유지보수 모드로 전환하십시오. 네비게이터 분할창에서 vSphere ESXi 호스트를 선택하고 해당 호스트를 마우스 오른쪽 단추로 클릭한 후 **유지보수 모드** > **유지보수 모드로 전환**을 선택하십시오. 호스트가 자동화된 DRS 클러스터의 일부이므로 호스트가 유지보수 모드로 전환될 때 가상 머신이 다른 호스트로 마이그레이션됩니다.
2. IC4VS 콘솔의 세부사항을 사용하여 vSphere ESXi 호스트에 SSH로 연결하십시오.
3. 다음 vCLI 명령을 실행하여 ixgben 기본 드라이버를 사용으로 설정하십시오.
  `esxcli system module set --enabled=true --module=ixgben`
4. 다음 vCLI 명령을 실행하여 vSphere ESXi 호스트를 다시 시작하십시오.
  `system shutdown reboot --reason “Install ixgben driver”`
5. vSphere ESXi 호스트가 다시 부팅된 후 SSH를 사용하여 호스트에 다시 로그인하십시오. 다음 vCLI 명령을 실행하고 ixgben 드라이버가 "로드"되고(첫 번째 열) "사용으로 설정"(두 번째 열)되었는지 확인하십시오. `esxcli system module list |grep ixg`
6. 드라이버가 사용으로 설정된 경우 vSphere Web Client를 사용하여 네비게이터 분할창에서 호스트를 선택하고 마우스 오른쪽 단추를 클릭한 후 **유지보수 모드** > **유지보수 모드 종료**를 선택하십시오. 다음 호스트를 선택하고 모든 호스트가 완료될 때까지 드라이버를 사용으로 설정하십시오.
7. 변경사항이 작동하지 않는 경우 되돌리려면 다음 명령을 실행하십시오. `esxcli system module set --enabled=false --module=ixgben`

8. 네트워크를 통해 호스트에 연결할 수 없는 경우에 IBM Cloud 제어 창을 사용하여 IPMI 콘솔에서 이전 명령을 실행하십시오.
9. vSphere ESXi 호스트를 다시 부팅하면 이제 로드되어 사용으로 설정된 기본 ixgbe 드라이버를 볼 수 있습니다.

되돌려야 하고 vSphere ESXi 호스트에 SSH로 연결할 수 없는 경우 IBM Cloud 제어 창을 통해 되돌려야 하는 호스트에 대한 KVM 콘솔에 로그인해야 합니다.

IPMI IP 주소와 함께 IBM Cloud 제어 창에 나열된 ID 및 비밀번호를 사용하여 IPMI 웹 인터페이스에 로그인하십시오. VPN을 통해 호스트가 있는 데이터 센터에 연결되어야 합니다. 자세한 정보는 [IBM Cloud VPN 시작하기](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn)를 참조하십시오.

1. 디바이스 세부사항, vSphere ESXi 호스트에 대한 원격 관리 페이지로 이동하여 **조치** > **KVM 콘솔**을 선택하십시오. IPMI 사용자 및 비밀번호를 입력할 수 있는 다른 창이 열립니다.
2. **원격 제어** > **iKVM/HTML5**를 선택하고 **iKVM/HTML5**를 클릭하여 재실행하십시오. 이제 vSphere ESXi 호스트의 콘솔에 액세스할 수 있습니다.
3. 호스트가 명령에 응답하는 경우 콘솔에서 **ALT-F1**을 사용하여 ESXi 호스트 콘솔에 액세스하십시오. 호스트의 인증 정보를 사용하여 로그인하십시오.
4. 호스트가 응답하지 않는 경우 IPMI 메뉴를 사용하여 호스트의 전원 주기를 수행하십시오.
5. 호스트가 다시 시작될 때 HTML5 콘솔을 주의하여 보십시오. ESXi가 다시 시작되기 시작할 때 몇 초 내에 복구 모드로 전환됩니다.
6. **CMD+R** 키를 동시에 눌러 복구 모드에 진입하십시오.
7. **“Y”**를 입력하여 복구 모드에 진입하고 이전 버전을 사용하여 ESXi 서버를 부팅하십시오.
8. 콘솔을 통해 진행상태를 모니터하십시오. 10 - 20분이 걸릴 수 있습니다.

### 관련 링크

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud 디지털 기술 업무](https://ibm-dte.mybluemix.net/ibm-vmware)(데모)

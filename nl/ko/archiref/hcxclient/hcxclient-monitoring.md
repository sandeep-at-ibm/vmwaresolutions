---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 매개변수 및 컴포넌트 모니터링
{: #hcxclient-monitoring}

## 모니터링에 WAN 최적화 프로그램 사용
{: #hcxclient-monitoring-using-wan}

HCX의 일부로 배치된 Silver Peak WAN 최적화 어플라이언스에서는
관리 인터페이스가 구성되지 않습니다. 웹 사용자 인터페이스(UI)는
트래픽 처리량의 기준선을 지정하고 네트워크 마이그레이션 대역폭 사용을 조절할 때
사용하는 유용한 도구입니다.

HCX CGW 게이트웨이 WAN 터널 트래픽만 WAN 최적화 프로그램 어플라이언스를
통해 이동합니다. 따라서 확장 L2 트래픽을 모니터링할 수 없습니다.
{:note}

### UI 구성
{: #hcxclient-monitoring-config-ui}

{{site.data.keyword.IBM}} 또는 VMware 지원 직원이 지시하지 않는 경우
웹 UI의 IP 주소를 구성하는 작업 외에는 WWAN 최적화 프로그램 어플라이언스의
구성을 변경하지 마십시오.

WAN Opt 웹 UI를 구성하려면 다음을 수행하십시오.

1. vCenter 클라이언트에서 WAN Opt 가상 머신(VM) 어플라이언스를 찾습니다.
2. vCenter 클라이언트를 사용하는 VM에 연결하는 콘솔을 엽니다.
3. 콘솔에서 **F4**를 클릭하여 관리 인터페이스를 구성합니다.
4. 정적 IP를 구성하도록 선택합니다.
5. 관리 {{site.data.keyword.cloud}} 지정 포터블 IP 범위의 IP 주소와
기본 게이트웨이를 사용합니다.
6. 다음 화면에서 **적용**을 클릭하여 저장하십시오.
7. vCenter 콘솔에서 WAN Opt VM의 편집 설정을 클릭하십시오.
8. **전원 공급 시 연결** 및 **네트워크 어댑터 1용으로 연결**을 선택하십시오.
9. **확인**을 클릭하여 저장하십시오.
10. vCenter에서 CGW-<xxx>-WANOPT를 찾으십시오.
11. VM의 설정을 편집하십시오.
12. 네트워크 어댑터 1을 연결하려면 선택란을 클릭하십시오.
13. **확인**을 클릭하십시오.
14. `https://<configured_WAN_OPT_IP>`로 이동하십시오.
15. `admin` 기본 사용자와 `admin` 비밀번호로 로그인하십시오.

이제 WAN Opt 웹 UI를 사용하여 처리량 비율, 압축 비율 및 세트 대역폭 제한사항을 모니터링할 수 있습니다.

### 마이그레이션 대역폭 조절
{: #hcxclient-monitoring-mig-bandwidth}

VM을 마이그레이션하기 전에 사용되는 네트워크 링크에 대한 평가를 수행하십시오. vSphere의 소스 인스턴스를 포함하는 네트워크의 네트워킹 전문가와 작업하거나 매주 및 매달 트래픽 사용을 검토하십시오. 링크가 1Gbps 미만인 경우
특히 비즈니스에 중요한 링크를 통해 트래픽이 순회하면 마이그레이션에
사용할 대역폭을 제한할 수 있습니다. 대역폭이 가장 제한된
측을 사용하십시오. 일반적으로 클라이언트 측이
이에 해당합니다.

HCX 클라이언트 UI에 Fleet 컴포넌트를 배치할 때 이와 같이
수행하지만 사후 배치에서는 WAN Opt UI로 이동해야 합니다.

HCX 웹 UI에서 HCX CGW를 재배치하는 경우 변경사항이 유실됩니다. 그러면 마이그레이션 트래픽의 대역폭 한계만 설정됩니다. 확장 L2
트래픽은 이 설정의 영향을 받지 않습니다.
{:note}

1. WAN Opt Web UI에 로그인하십시오.
2. **구성** 탭의 메뉴에서 **셰이퍼(Shaper)**를 선택하십시오.
3. **최대 대역폭** 상자에서 WAN Opt 어플라이언스에 사용할 수 있는 최대 대역폭을 설정하십시오. WAN 링크의 최대 대역폭을 초과하지 마십시오. 값을 Mbps로 설정하려면 1,000을 곱하십시오. 값을 Gbps로 설정하려면 1,000,000을 곱하십시오. 기본값은 10Gbps(10,000,000Kbps)입니다.
4. **적용**을 클릭하십시오.

확장 L2 대역폭 조절의 경우 L2C 어플라이언스 간 터널 트래픽을 위해
UPD 500과 4500에 QoS를 사용할 수 있습니다.

## HCX 컴포넌트 모니터링
{: #hcxclient-monitoring-hcx-comp}

HCX Manager, 클라우드 게이트웨이, WAN opt 및 계층 2 집선기 조작과 같은
HCX 컴포넌트를 다음과 같은 방법으로 모니터링하십시오.

- syslog 서버에 로그를 보내도록 HCX Manager를 구성하십시오. HCX 관리자
어플라이언스 관리 유틸리티를 사용하여 `https://<hcxhostname or
IP>:9443` 명령을 실행하십시오.
- 각 확장 L2 네트워크의 네트워크 전환 전에 마이그레이션된
VM에 대한 ping을 설정하십시오.
- VMware vRealize Operations Manager 또는 기타 VMware VM 모니터링
도구를 사용하여 HCX 컴포넌트 VM 상태를 모니터링하십시오.

## 대역폭 사용량
{: #hcxclient-monitoring-band-use}

다음 방법을 사용하여 대역폭 사용량과 대기 시간을 모니터링하십시오.

- vMotion 트래픽은 WAN Opt 웹 UI를 사용하면 가장 잘 수행할 수 있습니다. WAN
Opt를 사용하면 WAN으로 이동하는 트래픽이 현저히 감소되고 중복 패킷을
보내 발생하는 패킷 손실을 줄입니다. LAN과 WAN 대역폭 사용의 일반적인 비율은 약 3:1(350Mbps LAN = 90-120Mbps WAN)인 것으로 관찰되었습니다.
- HCX 내에서 복제를 기반으로(대량) VM을 마이그레이션하면 씩 프로비저닝으로 이동됩니다. 이는 바람직하지 않지만 사용자가 사용되지 않는 디스크 데이터를 이동할 때 LAN 및 WAN 사이의 높은 사용 비율을 표시합니다. 반대로 DB 데이터 및 디지털 매체와 같이 압축 불가능 데이터를 마이그레이션할 때 LAN 사용에 근접하므로 WAN 사용이 최고조에 이릅니다.

관찰:
- HCX 내에서 VM의 vMotion 마이그레이션은 단일 ESXi 호스트를 위한 vMotion 네트워킹보다 더 많은 처리량을 생성하지 않습니다.
- 대량 마이그레이션에서는 여러 마이그레이션이
동시에 진행될 수 있으므로 vMotion 마이그레이션보다
대역폭을 많이 사용합니다. ESX 호스트에 1Gbps vMotion 링크가 되어 있는
고객 측에서 관찰된 비율은 8개의 복제 = 1 vMotion의 대역폭
사용입니다.
- 디스크에서 비어 있는 공간을 이동하면 높은 비율의 높은 LAN 사용이 표시되므로 WAN 사용이 줄어듭니다. 1Gbps가 한계인 것으로
보입니다. 물론 이 특정 경우에는 vMotion 네트워크에서 병목 현상인 1Gbps만 가능합니다.
- 다중 TB Oracle DB의 vMotion 마이그레이션입니다. 1Gbps의 WAN 링크를 사용하면
한계는 1Gbps의 vMotion 네트워크입니다.

## 확장 계층 2 트래픽
{: #hcxclient-monitoring-stretched-layer-2-traffic}

HCX Fleet 컴포넌트 Layer 2 Concentrator에서는 순회하는 모든 L2 네트워크 트래픽의 대역폭 한계가 약 4Gbps입니다. 개별 확장 네트워크의 대역폭 한계는 트래픽 유형에 따라 1Gbps 이하입니다. 단일 L2C 쌍 전체에 여러 확장 L2
네트워크가 있을 수 있습니다(L2C 쌍당 이론적으로 허용되는
최대값은 4096개의 네트워크임). L2C는 동일한 L2C 쌍에서
대형 플로우에 작은 트래픽 플로우가 압도되는지 감지하여
보호하도록 엔지니어링된 한편 이 상황이 발생하여 더 많은
L2C를 시작하므로 전체 대역폭 기능이 증가하는지 파악하는 데도
유리할 수 있습니다.

고객 사이트와 {{site.data.keyword.cloud}} 간에 직접 링크 및 인터넷과 같은 여러 경로가 있으면 여러 L2C를 배치하는 것도 유리할 수 있습니다. 단일 네트워크는
중복하거나 여러 L2C 쌍에서 대역폭을 늘릴 수 없습니다.

L2C VM의 모니터링 탭을 사용하는 모든 인터페이스에서 트래픽을
모니터링하십시오. 총 데이터 비율이 8Gbps(4Gbps 입력/출력)에
도달하면 다른 L2 쌍을 추가하고 확장 네트워크를 재배포하여 재조정해
보십시오.

## 관련 링크
{: #hcxclient-monitoring-related}

* [HCX 컴포넌트 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 클라이언트 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 온프레미스 서비스 메시](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

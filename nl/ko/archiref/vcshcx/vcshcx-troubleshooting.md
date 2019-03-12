---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# HCX 문제점 해결
{: #vcshcx-troubleshooting}

일반 HCX 문제와 수정사항을 위해 다음을 검토하십시오.

## HCX 클라이언트 사용자 인터페이스 문제
{: #vcshcx-troubleshooting-hcx-client-issues}

### HCX 사용자 인터페이스 토큰 제한시간 초과
{: #vcshcx-troubleshooting-hcx-ui-issues}

일반적으로 vCenter 사용자 인터페이스(UI)가 일정 시간 동안 개방된 상태로 남은 경우 HCX UI에서 제한시간 초과가 발생할 수 있습니다. HCX 관리자 서버에 사용하는 로그인 토큰의 제한시간이 초과되었기 때문일 수 있습니다. vSphere 웹 UI에서 로그아웃하고 다시 로그인하여 토큰을 새로 고치십시오.

### 대시보드 화면의 모든 메트릭에 대해 "NaN"을 표시하는 HCX 클라이언트 UI
{: #vcshcx-troubleshooting-nan-display}

이 문제는 현재 로그인된 vCenter 계정의 권한과 관련되어 있습니다. 엔터프라이즈 관리자 그룹이 HCX 클라우드 측 어플라이언스 관리자 UI에 설정되어 있는지 확인하십시오.

## 마이그레이션 문제
{: #vcshcx-troubleshooting-mig-issues}

현재 버전의 HCX에 있는 마이그레이션 문제는 일반적으로 라이센싱, 클라우드 게이트웨이 네트워킹 연결 및 대상 하드웨어 호환성과 같은 세 가지 카테고리로 나눕니다.

### 라이센싱
{: #vcshcx-troubleshooting-licensing}

라이센싱 문제 때문에 마이그레이션에 실패하면 현재 버전의 HCX가 vCenter UI의 클라이언트 웹 UI와 함께 오류 메시지에 이 내용을 명확하게 표시합니다.

### 네트워크(WAN) 연결
{: #vcshcx-troubleshooting-wan-connect}

WAN 연결에 문제가 있으면 HCX UI의 **상호 연결 -> HCX 컴포넌트** 화면에서
항상 터널 상태를 확인하십시오. 일반적으로 Fleet 컴포넌트는 재설정하거나 다시 부팅하지 않아도 됩니다. WAN 연결이 복원되면 자동으로 다시 연결됩니다.

HCX 관리자(클라이언트와 클라우드)에 적용된 업데이트와 수정사항이 있고 해당 업데이트에서 Fleet 컴포넌트의 문제도 패치하는 경우 배포된 모든 L2C와 클라우드 게이트웨이를 다시 배포해야 합니다. ccli와 같은 SSH 클라이언트를 통해 HCX 관리자에 연결하여 터널 상태를 더 자세히 디버깅할 수 있습니다.  

1. 관리자 계정과 제공된 비밀번호를 사용하여 HCX 관리자에 SSH를 수행합니다.
2. `su –` 명령과 root 비밀번호(관리자 비밀번호와 동일)를 사용하여 root로 변경하십시오.
3. `/opt/vmware/bin`으로 디렉토리를 변경하고 `./ccli` 명령을 실행하십시오. 환경이 root용으로 설정되지 않아서 이 명령에 실패하면 `./ccliSetup.pl` 명령을 실행하십시오.
4. ccli 쉘에서 `list` 명령을 실행하여 HCX 관리자에 등록된 Fleet 컴포넌트를 나열하십시오.
5. Fleet 컴포넌트용으로 나열된 ID를 입력하여 ccli의 초점을 선택합니다. 예를 들어 `go 8`입니다.
6. SSH를 사용하여 원하는 Fleet 컴포넌트에 연결하려면 `debug remoteaccess enable` 명령을 실행합니다.
7. ccli를 종료하고 SSH를 사용하여 SSH 사용 Fleet 컴포넌트의 IP 주소에 연결합니다.
9. 계속하여 문제를 해결합니다.
10. ccli로 돌아와서 컴포넌트의 ssh 서비스를 사용하지 않게 설정합니다.
11. 필요한 경우 `hc` ccli 명령을 사용하여 컴포넌트의 상태 검사를 실행합니다.

## 대상 하드웨어 호환성 문제
{: #vcshcx-troubleshooting-hw-compatibility}

클라이언트 소스 측의 하드웨어 버전과 vSphere 릴리스가 클라우드보다 최신이면 vMotion 마이그레이션은에 문제가 있을 수 있습니다. 복제 기반 마이그레이션에서는 대상 측의 새로 빌드된 가상 머신(VM)에 데이터를 복사하므로 마이그레이션 유형을 "대량 마이그레이션"으로 변경하면 대부분의 경우 마이그레이션이 성공할 수 있어야 합니다.

## 확장 L2 문제
{: #vcshcx-troubleshooting-stretched-l2}

L2 집선기 조작에 문제가 발생하는 경우는 거의 없습니다. CGW와 비슷하게 L2C에서 연결이 끊기면 네트워크 연결이 복원된 후 자동으로 다시 연결합니다. ccli 셀을 사용하여 상태와 조작을 확인하십시오. SSH가 사용되고 L2C가 연결되고 나면 `ip tunnel`과 `ip link |grep t_` 명령을 실행하여 터널의 상태를 보십시오.

## 관련 링크
{: #vcshcx-troubleshooting-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 개요](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

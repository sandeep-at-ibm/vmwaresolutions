---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-27"

subcollection: vmware-solutions


---
# vCenter에 HCX Manager 등록
{: #hcx-archi-reg-vcenter}

VMware vSphere Web Client에 하이브리드 클라우드 서비스 플러그인을 등록하고 하이브리드 클라우드 서비스 관리 서비스를 시작하십시오.

## 시작하기 전에
{: #hcx-archi-reg-vcenter-prereq}

하이브리드 클라우드 서비스 가상 어플라이언스를 등록하려면 전원을 켜야 합니다.

## vCenter에 HCX Manager를 등록하는 프로시저
{: #hcx-archi-reg-vcenter-proc-register}

1. 하이브리드 클라우드 서비스의 서비스 가상 어플라이언스에 로그인하십시오. 예를 들어, `https:My-HCX-Manager:9443/`입니다.
2. **설정 관리** 타일을 클릭하십시오.
  1. 왼쪽 분할창의 **시스템 구성**에서 vCenter를 선택하십시오.
  2. 오른쪽 상단의 **vCenter 추가**를 클릭하십시오.
  3. `https:vCenter-host-name` 또는 `https:vCenter-IP-address` 양식으로 된 vCenter Server의 IP 주소를 입력하십시오. 예를 들면, `https:My-vCenter` 또는 `https:10.108.26.211`입니다.
  4. vCenter Server 사용자 이름 및 비밀번호를 입력하십시오. 사용된 계정에는 vCenter 관리자 역할이 있어야 합니다.
  5. **확인**을 클릭하십시오. _앱을 다시 시작해야 합니다._ 메시지가 표시되면 다시 시작하지 마십시오.
3. 검색 서비스를 구성하십시오.
  1. **관리** 탭을 클릭하십시오.
  2. **검색 서비스 URL** 텍스트 상자의 맨 오른쪽에 있는 **편집** 단추를 클릭하십시오.
  3. 다음 양식으로 검색 네트워크 서비스 엔드포인트를 입력하십시오.
    * vCenter Server 5.5u3: `https://ssoip:/7444/lookupservice/sdk`
    * vCenter Server 6.0u2: `https://ssoip/lookupservice/sdk`
  4. **확인**을 클릭하십시오. 웹 엔진을 다시 시작해야 하는 메시지가 표시되면 다시 시작하지 마십시오.
4. **요약** 탭을 클릭하고 **하이브리디티 관리 컴포넌트** 섹션을 찾으십시오. 애플리케이션 엔진과 웹 엔진을 모두 중지한 후 시작하십시오.
5. 등록을 완료하려면 vSphere Web Client를 로그아웃하십시오. 화면 업데이트가 발생했는지 확인하려면 다시 로그인하십시오.

## 결과
{: #hcx-archi-reg-vcenter-results}

기존의 **하이브리드 클라우드** 아이콘과 왼쪽에 있는 **하이브리드 클라우드 서비스** 메뉴 항목에 유의하십시오. 하이브리드 클라우드 서비스 등록에서 이 레이블을 업데이트합니다. 인벤토리에서 아이콘 레이블은 **하이브리드 클라우드 서비스**가 됩니다.

## 관련 링크
{: #hcx-archi-reg-vcenter-related}

* [하이브리드 서비스 설치 및 구성](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)

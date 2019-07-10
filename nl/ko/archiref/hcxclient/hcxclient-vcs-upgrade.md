---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 컴포넌트 업그레이드
{: #hcxclient-vcs-upgrade}

HCX 업그레이드는 클라이언트 측 HCX 관리자 업데이트 시에는
클라이언트 웹 사용자 인터페이스(UI)를 사용하고 클라우드 측 HCX 관리자 업데이트 시에는
클라우드 웹 UI를 사용하는 간단한 프로세스입니다.

Fleet 컴포넌트 업데이트를 수행하면 HCX Manager가 설치된 코드 레벨로 Fleet 컴포넌트를 다시 배포하므로 양측 모두 업그레이드해야 합니다. 

VMware 지원에서 시스템 ID를 요청하면 클라이언트와 클라우드 측 모두를 제공하십시오. HCX 관리자(클라이언트 또는 클라우드)에 SSH를 사용하고 `cat /common/location`을 실행하여 시스템 ID를 찾으십시오.

## 관련 링크
{: #hcxclient-vcs-upgrade-related}

* [HCX 컴포넌트 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 클라이언트 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 온프레미스 서비스 메시](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [매개변수 및 컴포넌트 모니터링](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

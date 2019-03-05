---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 3단계 - 애플리케이션 구성
{: #caveonix-step3}

이 단계에서는 Caveonix RiskForesight 구성 스크립트를 사용합니다. “일체형” 배치에서는 IC4VS 자동화를 통해 이 스크립트가 시작됩니다. 스케일링의 경우 클라이언트에서 스크립트를 호출하여 부분 또는 완전 분배 배치 토폴로지를 배치해야 합니다. 이 스크립트에서 RiskForesight 서비스를 구성합니다.
-	Caveonix 앱(API, 중앙 콜렉터)
-	Elastic Search
- PostgresSQL
-	원격 콜렉터
-	UI
-	Kafka
-	Kibana
-	모든 서비스의 인증서

이 단계가 종료되면 필수 가상 머신(VM)에 애플리케이션 컴포넌트가 설치됩니다.

## 관련 링크
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)

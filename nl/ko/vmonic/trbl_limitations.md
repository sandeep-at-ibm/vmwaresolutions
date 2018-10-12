---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 추가 제한사항 및 고려사항

{{site.data.keyword.vmwaresolutions_full}}에 대한 작업을 수행할 때 다음 고려사항 및 제한사항을 검토하십시오.

## Windows 업데이트 자동 설치

Microsoft Active Directory(AD)/DNS(Domain Name Server)는 업데이트만 다운로드하도록 자동으로 설정됩니다. 자동으로 이러한 업데이트를 설치하거나 다시 시작하지 않습니다. 지속적인 AD 서버 구성 및 기타 백업 작업의 중단이 발생하지 않도록 스케줄된 시간에 업데이트를 수동으로 설치하고 다시 시작해야 합니다. Windows 업데이트를 적용하려면 업데이트를 수동으로 설치하십시오.

## Cloud Foundation 인스턴스의 루트 도메인 이름 선택 시 고려사항

기본 또는 보조 Cloud Foundation 인스턴스 배치 중에 도메인 이름을 선택할 때 `sddcmanager.<subdomain>` 호스트 이름이 `ping` 또는 `nslookup` 명령을 사용하여 외부 도메인으로 분석되지 않는지 확인해야 합니다.

Cloud Foundation 인스턴스 하위 도메인의 구조는 `<VCF instance name>.<domain name>`입니다. 예를 들어, `<domain name>`이 `test.local`이고 Cloud Foundation 인스턴스 이름이 `mytest`인 경우에는 Cloud Foundation 인스턴스를 배치하기 전에 `sddcmanager.mytest.test.local` 호스트 이름이 IP 주소로 분석되지 않습니다. 그렇지 않으면 인스턴스 배치에 실패할 수 있습니다.

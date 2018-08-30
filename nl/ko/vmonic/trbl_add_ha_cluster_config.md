---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# HA 클러스터 추가 시 발생하는 vSphere 콘솔 구성 문제

## 문제점
하나의 파일 공유만 포함하여 HA(High Availability) 클러스터 구성을 추가하는 경우 ESXi 호스트에서 다음 구성 문제가 발생합니다.

`The number of heartbeat datastores for host is 1, which is less than required: 2`

## 해결
공유 스토리지에 데이터 저장소 하트비트를 허용하기 위한 중복성이 없는 경우 이 문제가 발생합니다.

문제점 해결 방법에 대한 정보 및 단계는 [HA error: "The number of heartbeat datastores for host is 1, which is less than required: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739)를 참조하십시오.

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Zerto Virtual Replication Appliances가 새로 작성된 ESXi 서버에 대해 표시되지 않음

## 문제점
ESXi 서버를 Zerto 재해 복구가 설치된 VMware vCenter Server 인스턴스에 추가한 후 VRA(Virtual Replication Appliances)가 Zerto Virtual Replication 콘솔에 표시되지 않습니다.

## 해결
vCenter Server 인스턴스의 경우, Zerto 재해 복구 서비스가 기본 클러스터인 **cluster1**의 ESXi 서버에만 설치됩니다. 동일한 vCenter Server 환경의 추가 클러스터에는 추가 클러스터가 작성되거나 ESXi 서버가 추가 클러스터에 추가되는 경우 Zerto 재해 복구가 자동으로 설치되지 않습니다.

추가 클러스터에서 개별적으로 Zerto 재해 복구를 설치해야 합니다.

{{site.data.keyword.vmwaresolutions_short}} 콘솔 대신 Zerto 콘솔에서 VRA를 설치할 수 있도록 {{site.data.keyword.cloud}} 지원 티켓을 열고 IBM 지원 센터에 문의하여 사용 가능한 IP 주소를 가져오십시오.

Zerto 콘솔에 액세스하려면 인스턴스의 **서비스** 탭에서 Zerto 카드를 클릭하고 **세부사항 보기**를 클릭한 후 **Zerto 콘솔 보기**를 클릭하십시오.

IBM 지원 센터 문의에 대한 자세한 정보는 [IBM 지원 센터에 문의](/docs/services/vmwaresolutions//vmonic/trbl_support.html)를 참조하십시오.

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Zerto on IBM Cloud에 대한 제거 프로세스

Zerto on {{site.data.keyword.cloud}} 서비스의 제거 프로세스가 자동화되었습니다. Zerto on {{site.data.keyword.cloud_notm}} 서비스의 성공적인 제거를 위해 다음 단계가 완료됩니다.

## Zerto on IBM Cloud를 제거하는 방법

1. 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하고 서비스를 제거할 인스턴스를 클릭하십시오.
2. **서비스** 탭을 클릭하십시오.
3. **설치된 서비스** 탭에서 서비스 카드의 오른쪽 상단에 있는 오버플로우 메뉴 아이콘을 클릭한 후 **서비스 제거**를 클릭하십시오.
4. 해당되는 경우, **서비스 제거** 창에서 고려사항 또는 경고를 검토하십시오. **이해함**을 클릭하십시오.
5. 서비스 제거 요청이 허용된 후 서비스 상태가 **제거 중**으로 변경되고 다음 제거 단계가 완료됩니다.   
   1. 모든 ESXi 서버에 배치된 Zerto Virtual Replication Appliances를 제거하십시오.
   2. Zerto Virtual Replication을 설치 제거하십시오.
   3. Zerto Virtual Replication이 설치된 Windows VSI(Virtual Service Instance)를 삭제하십시오.
   4. {{site.data.keyword.cloud_notm}} 인프라에 대한 Zerto Virtual Replication 통신을 위해 주문된 사설 포터블 서브넷을 리턴하십시오.   
   5. {{site.data.keyword.cloud_notm}} 청구서에서 Zerto 재해 복구 서비스의 비용을 제거하십시오.

      **참고:** 제거된 Zerto 재해 복구 서비스에 대한 비용 청구 주기 종료 시 비용이 청구됩니다.

## 결과

서비스 제거가 완료된 후 이메일 및 **설치된 서비스** 탭에서 제거된 서비스 항목을 통해 알림을 받습니다.

### 관련 링크

* [Zerto on {{site.data.keyword.cloud_notm}} 주문](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 관리](managingzertodr.html)
* [Cloud Foundation 인스턴스](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 인스턴스](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com 웹 사이트](https://www.zerto.com){:new_window}
* [Zerto 기술 문서](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

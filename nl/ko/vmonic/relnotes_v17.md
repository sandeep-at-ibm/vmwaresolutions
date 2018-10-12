---

copyright:

  years:  2016, 2018

lastupdated: "2017-07-05"

---

# V1.7 릴리스 정보

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VMware Cloud Foundation 인스턴스에 대한 업데이트

이 업데이트는 다음 업그레이드 및 개선사항에 적용됩니다.
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* IBM CloudDriver 컴포넌트에 대한 안전성 개선
* EVC 모드(Intel “Haswell” 2690-V3 프로세서 기반)는 업그레이드 시 V3 서버에 있는 기존의 이전 VMware 배치에서 사용으로 설정됩니다.

  **참고**: EVC 모드는 V4 서버의 기존 또는 새 배치에 사용으로 설정되지 않습니다.

* 5월 22일 이전에 배치되었으며 이에 따라 V3 서버를 사용 중인 VMware Cloud Foundation 배치는 이제 새 노드를 인스턴스에 추가할 때 V4 서버를 주문합니다. 이 서버에는 256GB의 메모리가 있습니다. 512GB 메모리가 필요하면 서버를 추가한 후 지원 티켓을 열어 521GB 메모리로 서버 업그레이드를 요청하십시오. IBM 지원 센터 문의에 대한 자세한 정보는 [IBM 지원 센터에 문의](trbl_support.html)를 참조하십시오.

컴포넌트에 대한 자세한 정보는 [Cloud Foundation 인스턴스의 기술 스펙](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)을 참조하십시오.

### 업그레이드 프로세스 요구사항

Cloud Foundation 인스턴스 배치의 복잡도 및 다중 사이트 구성의 보유 여부에 따라 업데이트 프로세스에는 콘솔의 **업데이트 및 패치** 탭에 표시된 대로 완료해야 하는 단계의 순서가 필요할 수 있습니다. 자세한 정보는 [Cloud Foundation 인스턴스에 업데이트 적용](../sddc/sd_applyingupdates.html#applying-updates-to-cloud-foundation-instances)을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트

### 클러스터 지원

더 나은 리소스 관리 및 고가용성을 위해 V1.7 릴리스부터 클러스터를 사용하여 vCenter Server 인스턴스의 ESXi 서버를 관리할 수 있습니다. 인스턴스를 주문할 때 구성한 ESXi 서버는 기본적으로 **cluster1**로 그룹화됩니다. 클러스터 새부사항을 보거나 인스턴스 세부사항 페이지에 있는 새로 도입된 **인프라** 탭의 인스턴스에 총 다섯 개의 클러스터를 추가할 수 있습니다. 인스턴스의 용량을 확장하거나 축소하는 경우 ESXi 서버를 추가할 클러스터 또는 ESXi 서버를 제거할 클러스터를 선택할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](../vcenter/vc_addingviewingclusters.html)를 참조하십시오.

### Zerto 재해 복구의 배치에 대한 개선사항

이제 Zerto 재해 복구의 배치가 지원 티켓을 통해 처리되지 않고 자동화됩니다. 주문하기 전에 검토할 수 있도록 예상 비용에 모든 Zerto 컴포넌트(예: 사설 포터블 서브넷), Windows VSI(Virtual Service Instance) 및 Zerto 라이센스 비용이 나열됩니다. 자세한 정보는 [Zerto 재해 복구의 배치 프로세스](../services/addingzertodr.html)를 참조하십시오.

### NSX 라이센스 업그레이드 기능

vCenter Server 인스턴스의 **요약** 탭에서 NSX 라이센스 에디션을 업그레이드할 수 있습니다. 라이센스 업그레이드는 계정에 있는 기존의 모든 NSX SoftLayer 라이센스를 새 라이센스로 대체합니다. 자세한 정보는 [vCenter Server 인스턴스 보기](../vcenter/vc_viewinginstances.html)를 참조하십시오.

## 사용성 개선사항

개선사항은 사용자 인터페이스를 통해 수행됩니다.
* Cloud Foundation 인스턴스 세부사항 페이지의 **특성** 탭이 **요약**으로 이름이 바뀝니다. 이제 이 탭에서 인스턴스, 인스턴스 관련 컴포넌트의 액세스 정보 및 인스턴스 배치 히스토리의 세부사항을 볼 수 있습니다.
* 새 **인프라** 탭이 Cloud Foundation 인스턴스 세부사항 페이지에 도입되었습니다. 이제 이 탭에서 ESXi 서버를 보거나 추가하거나 제거할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}}에 대한 문서는 새 형식을 갖게 되고 이제 Bluemix 문서 세트와 함께 Bluemix 카탈로그로 완전히 통합됩니다. 다음과 같은 방식으로 문서에 액세스할 수 있습니다.
  * {{site.data.keyword.vmwaresolutions_short}}의 배너 왼쪽에서 **문서**를 클릭하십시오.
  * Bluemix 문서 카탈로그에서 **컴퓨팅 및 서비스** 섹션 아래로 스크롤하고 **{{site.data.keyword.vmwaresolutions_short}}**를 클릭하십시오.

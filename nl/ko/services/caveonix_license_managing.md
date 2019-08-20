---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight 라이센스 관리
{: #caveonix_license_managing}

독립형 사용을 위해 주문한 Caveonix RiskForesight 라이센스를 보거나 참고를 편집하거나 삭제할 수 있습니다.

## Caveonix RiskForesight 라이센스를 보기 위한 프로시저
{: #caveonix_license_managing_procedure-view}

1. 왼쪽 탐색 분할창에서 **리소스**를 클릭하고 **Caveonix RiskForesight 라이센스** 테이블로 스크롤하십시오.

   | 항목 |설명 |
   |:-----|:------------|
   |이름 |라이센스의 이름입니다. |
   |작성 시간 |라이센스가 작성된 날짜 및 시간입니다. |
   |상태 |라이센스의 상태입니다. <br>수정: 라이센스를 작성하는 중입니다.<br>설치됨: 라이센스가 이미 사용 중입니다.<br>제거: 라이센스를 삭제하는 중입니다. |
   {: caption="표 1. Caveonix RiskForesight 라이센스 항목 설명" caption-side="top"}

2. 특정 라이센스의 세부사항을 보려면 해당 라이센스를 클릭하십시오.

## Caveonix RiskForesight 라이센스의 참고를 편집하기 위한 프로시저
{: #caveonix_license_managing_procedure-edit}

1. 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **Caveonix RiskForesight 라이센스** 테이블로 스크롤하여 참고를 편집할 라이센스를 클릭하십시오.
3. 라이센스 세부사항 페이지에서 라이센스 참고를 편집한 다음 **확인**을 클릭하십시오.

## 라이센스 날짜 표시에 대한 알려진 문제
{: #caveonix_license_considerations-date}

Mozilla Firefox를 브라우저로 사용 중인 경우 라이센스 시작 및 종료 날짜가 Caveonix RiskForesight 콘솔에 값 없이 표시될 수 있습니다. 이 문제를 해결하려면 Google Chrome과 같은 다른 브라우저에서 라이센스 정보를 보십시오.

문제점이 발생하고 사용할 수 있는 유일한 브라우저가 Firefox이면 [Caveonix 지원 센터](https://www.caveonix.com/support/){:external}에 문의하여 도움을 받으십시오.
{:note}

## Caveonix RiskForesight 라이센스 삭제 프로시저
{: #caveonix_license_managing_procedure-delete}

Caveonix RiskForesight 라이센스를 삭제해도 vCenter Server 인스턴스에 설치된 {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스는 제거되지 않습니다. 이 서비스를 제거하려면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 이를 수행해야 합니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 서비스를 제거하는 프로시저](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure)의 내용을 참조하십시오.
{:note:}

1. 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **Caveonix RiskForesight 라이센스** 테이블로 스크롤하여 삭제할 라이센스를 찾으십시오.
3. **조치** 열에서 삭제 아이콘을 클릭하십시오.
4. **라이센스 삭제** 창에서 **확인**을 클릭하십시오.
   라이센스의 상태가 **제거 중**으로 변경됩니다. 라이센스 삭제가 완료되면 **Caveonix RiskForesight 라이센스** 테이블에서 더 이상 라이센스를 사용할 수 없습니다.

## 관련 링크
{: #caveonix_license_managing-related}

* [Caveonix RiskForesight 개요]()
* [Caveonix RiskForesight 라이센스 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 인스턴스에 대한 라이센스 업그레이드
{: #vc_upgrade-lic}

인스턴스가 V2.3 이상에 배치된 경우에만 VMware vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle로 업그레이드할 수 있습니다. 

IBM Business Partner 사용자에게는 Hybridity Bundle로 업그레이드할 수 있는 옵션이 없습니다.
{:note}

## 라이센스를 Hybridity Bundle로 업그레이드하기 전에
{: #vc_upgrade-lic-upgrade-prereq}

Hybridity Bundle로 업그레이드할 때 취하는 다음 조치를 검토하십시오. 

* vCenter Server 인스턴스에 VMware NSX Base 에디션이 설치된 경우 NSX 라이센스는 NSX Advanced 에디션으로 자동 업그레이드됩니다. 
* vCenter Server 인스턴스에 NFS 스토리지가 있는 경우 VMware vSAN 스토리지에 대한 비용이 청구되지 않습니다. Hybridity Bundle에 포함된 vSAN 라이센스에 대한 비용은 청구됩니다.

## Hybridity Bundle로 업그레이드하는 프로시저(V2.3 이상 인스턴스)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 Hybridity Bundle로 업그레이드할 인스턴스를 클릭하십시오.
3. **요약** 페이지에서 모든 인스턴스 세부사항이 올바르게 표시되는지 확인하십시오. 그런 다음 왼쪽 탐색 분할창의 **인프라**를 클릭하여 **인프라** 페이지에서 세부사항을 확인하십시오.

   세부사항이 표시되지 않는 경우, 이는 방화벽 규칙이나 기타 네트워킹 문제로 인한 IBM CloudDriver VSI(Virtual Server Instance)의 연결 문제점을 표시할 수 있습니다. 다음 단계를 계속하기 전에 문제점을 해결하십시오. 그렇지 않으면, 업그레이드에 실패할 수 있습니다.

4. 왼쪽 탐색 분할창에서 **업데이트 및 패치**를 클릭하십시오.
5. **라이센스 업그레이드** 테이블에서 Hybridity Bundle 라이센스 업그레이드를 적용하려면 **조치** 열의 **업그레이드**를 클릭하십시오. 예상 비용을 검토하고 **업그레이드**를 클릭하십시오.
6. 선택적으로 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 배치할 수 있습니다. **라이센스 업그레이드** 테이블에서 Hybridity Bundle이 사용으로 설정되면 다음 단계를 완료하십시오.
  1. **라이센스 업그레이드** 테이블에서 **조치** 열의 **HCX on {{site.data.keyword.cloud_notm}} 배치**를 클릭하십시오.
  2. **HCX on {{site.data.keyword.cloud_notm}}** 카드로 스크롤하여 **서비스 선택**을 클릭하십시오.
  3. 아래로 스크롤하여 서비스의 필수 설정을 지정하고 **다음**을 클릭하십시오.
  4. 서비스에 적용되는 이용 약관과 예상 비용을 검토하고 **주문하기**를 클릭하십시오.

## NSX 라이센스를 업그레이드하는 프로시저(V2.1 이상 인스턴스)
{: #vc_upgrade-lic-nsx}

이 프로시저는 2.1 이상에 배치된 인스턴스에 적용됩니다. V2.0 이전에 배치된 인스턴스의 경우, NSX 라이센스를 수동으로 업그레이드해야 합니다.

사용자 인스턴스에 맞게 NSX 라이센스를 최신 에디션으로 업그레이드할 수 있습니다. 라이센스 에디션 다운그레이드는 지원되지 않습니다. 

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 NSX 라이센스를 업그레이드할 인스턴스를 클릭하십시오.
3. **요약** 페이지에서 모든 인스턴스 세부사항이 올바르게 표시되는지 확인하십시오. 그런 다음 왼쪽 탐색 분할창의 **인프라**를 클릭하여 **인프라** 페이지에서 세부사항을 확인하십시오.

   세부사항이 표시되지 않는 경우, 이는 방화벽 규칙이나 네트워킹 문제로 인한 IBM CloudDriver VSI(Virtual Server Instance)의 연결 문제점을 표시할 수 있습니다. 다음 단계를 계속하기 전에 문제점을 해결하십시오. 그렇지 않으면, 업그레이드에 실패할 수 있습니다.

4. 왼쪽 탐색 분할창에서 **업데이트 및 패치**를 클릭하고 **업그레이드**를 클릭하십시오. **NSX 라이센스 에디션 업그레이드** 창에서 업그레이드할 에디션을 선택하고 **업그레이드**를 클릭하십시오.

   라이센스 업그레이드는 인스턴스에 있는 기존의 모든 NSX 라이센스를 대체합니다. 비용 청구 주기 중에 업그레이드하는 경우 이전 및 새 라이센스의 겹침으로 인해 추가 비용이 발생할 수 있습니다. 추가 비용이 발생하지 않도록 비용 청구 주기 종료 시 라이센스를 업그레이드하는 것이 좋습니다.
   {:note}

## 관련 링크
{: #vc_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

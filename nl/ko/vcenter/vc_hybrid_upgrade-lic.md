---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle 인스턴스에 대한 NSX 라이센스 업그레이드
{: #vc_hybrid_upgrade-lic}

사용자 인스턴스에 맞게 VMware NSX 라이센스를 최신 에디션으로 업그레이드할 수 있습니다. 라이센스 에디션 다운그레이드는 지원되지 않습니다. 

## NSX 라이센스를 업그레이드하는 프로시저
{: #vc_hybrid_upgrade-lic-nsx}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 NSX 라이센스를 업그레이드할 인스턴스를 클릭하십시오.
3. **요약** 페이지에서 모든 인스턴스 세부사항이 올바르게 표시되는지 확인하십시오. 그런 다음 왼쪽 탐색 분할창의 **인프라**를 클릭하여 **인프라** 페이지에서 세부사항을 확인하십시오.

   세부사항이 표시되지 않는 경우, 이는 방화벽 규칙이나 네트워킹 문제로 인한 IBM CloudDriver VSI(Virtual Server Instance)의 연결 문제점을 표시할 수 있습니다. 다음 단계를 계속하기 전에 문제점을 해결하십시오. 그렇지 않으면, 업그레이드에 실패할 수 있습니다.

4. 왼쪽 탐색 분할창에서 **업데이트 및 패치**를 클릭하고 **업그레이드**를 클릭하십시오.**NSX 라이센스 에디션 업그레이드** 창에서 업그레이드할 에디션을 선택하고 **업그레이드**를 클릭하십시오.

   라이센스 업그레이드는 인스턴스에 있는 기존의 모든 NSX 라이센스를 대체합니다. 비용 청구 주기 중에 업그레이드하는 경우 이전 및 새 라이센스의 겹침으로 인해 추가 비용이 발생할 수 있습니다. 추가 비용이 발생하지 않도록 비용 청구 주기 종료 시 라이센스를 업그레이드하는 것이 좋습니다.
   {:note}

## 관련 링크
{: #vc_hybrid_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

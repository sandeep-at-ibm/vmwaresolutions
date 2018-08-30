---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# 오퍼링 비교 차트

VMware Cloud Foundation 인스턴스, VMware vCenter Server 인스턴스, VMware vCenter Server with Hybridity Bundle 인스턴스 및 VMware vSphere 클러스터에 대한 기능 지원의 차이점을 이해하려면 다음 차트를 검토하십시오.

표 1. Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle 및 vSphere 클러스터에 지원되는 기능

|기능                          |Cloud Foundation    |vCenter Server | vCenter Server with Hybridity |VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| {{site.data.keyword.IBM}} 고급 자동화로 작동됨 <sup>1</sup> |예 |예 |예 |아니오. 자체 빌드되고 구성됨 |
|스토리지 옵션        |vSAN                |vSAN 또는 공유 파일 레벨 스토리지(NFS) |vSAN |vSAN 또는 공유 파일 레벨 스토리지(NFS) |
|초기 클러스터의 ESXi 서버 수 |4개 | vSAN의 경우 4개, NFS의 경우 최소 2개(3개 권장) |4개 |기존 클러스터를 스케일링는 경우 1개, 새 vSAN 클러스터의 경우 4개, NFS가 사용된 새 클러스터의 경우 최소 3개 |
| ESXi 서버의 최대 수 <sup>2</sup> |클러스터당 32개      |클러스터당 59개     |클러스터당 59개 |클러스터당 60개     |
|Cloud 자동화된 다중 사이트 배치 | V2.0 이상에 배치된 새 인스턴스에 지원됨 | V2.0 이상에 배치된 새 인스턴스에 지원됨 |지원됨 |지원됨. 자동화된 구성이 포함되지 않음 |
|ESXi 서버 추가              |지원됨           |지원됨 |지원됨 |지원됨. 자동화된 구성이 포함되지 않음 |
|ESXi 서버 제거           |지원됨           |지원됨 |지원됨 |지원됨. 자동화된 구성이 포함되지 않음 |
|다중 클러스터 지원         | 5개의 클러스터 | 10개의 클러스터 | 10개의 클러스터 |지원됨. 자동화된 구성이 포함되지 않음 |
|VMware 스택의 클라이언트 관리 업데이트 및 패치 | VMware 업데이트 |포함되지 않음 |포함되지 않음 |포함되지 않음 |
|백업 및 복원            |수동으로 IBM Spectrum Protect Plus 또는 Veeam 사용 |수동으로 IBM Spectrum Protect Plus 또는 Veeam 사용 |수동으로 IBM Spectrum Protect Plus 또는 Veeam 사용 | 백업 및 복원 솔루션이 포함되지 않음 |
|소프트웨어 정의 네트워킹   |NSX Enterprise   |NSX Base, Advanced 또는 Enterprise |NSX Advanced 또는 Enterprise |NSX Standard, Base 또는 Enterprise. 자동화된 구성이 포함되지 않음 |
|vSphere 및 vSAN용 BYOL |클러스터당 전체 지원됨   |클러스터당 전체 지원됨     |지원되지 않음 |지원됨 |
|vCenter 및 NSX용 BYOL |인스턴스당 전체 지원됨   |인스턴스당 전체 지원됨     |지원되지 않음 |지원됨 |
|NSX 라이센스 업그레이드 옵션           |없음   |NSX Base에서 Advanced 또는 Enterprise로, NSX Advanced에서 Enterprise로 업그레이드할 수 있음. vCenter Server with Hybridity Bundle로 업그레이드할 수 있음. |NSX Advanced에서 Enterprise로 업그레이드할 수 있음  |없음 |
|vSAN 라이센스 에디션         |vSAN Advanced 또는 Enterprise  |vSAN Advanced 또는 Enterprise  |vSAN Advanced 또는 Enterprise |vSAN Advanced 또는 Enterprise  |
|추가 기능 서비스               |지원됨(HCX on {{site.data.keyword.cloud_notm}} 미포함).  |지원됨(HCX on {{site.data.keyword.cloud_notm}} 미포함). vCenter Server with Hybridity Bundle로 업그레이드할 수 있음 |지원됨(HCX on {{site.data.keyword.cloud_notm}} 포함). |이 솔루션의 자동화로 지원되지는 않지만 자체 소프트웨어를 가져와서 설치할 수 있습니다. |

**참고**:

<sup>1</sup> 유효성 검증된 디자인에 따라 그리고 배치 중에 확인하여.

<sup>2</sup> vSAN 클러스터에서 최대 64개까지 ESXi 서버 수를 늘릴 수 있습니다. 자세한 정보는 [ESXi 서버에 대한 FAQ](faq_esxi.html)의 _몇 개의 ESXi 서버를 클러스터에 추가할 수 있습니까?_를 참조하십시오.

### 관련 링크

* [FAQ](faq.html)
* [Cloud Foundation 개요](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server with Hybridity 개요](../vcenter/vc_hybrid_overview.html)
* [VMware vSphere 개요](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation BOM](../sddc/sd_bom.html)
* [vCenter Server BOM](../vcenter/vc_bom.html)
* [VMware vSphere BOM](../vsphere/vs_bom.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# IBM Spectrum Protect Plus on IBM Cloud 주문

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 IBM Spectrum Protect Plus on IBM Cloud 주문

다음 방법 중 하나를 사용하여 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **IBM Spectrum Protect Plus on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **IBM Spectrum Protect Plus on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 IBM Spectrum Protect Plus on IBM Cloud 주문

다음 방법 중 하나를 사용하여 기존 인스턴스에 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **IBM Spectrum Protect Plus on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## IBM Spectrum Protect Plus on IBM Cloud 서비스 구성

서비스를 주문할 때 다음 설정을 제공하십시오.

### 스토리지 볼륨 수

스토리지 요구에 맞는 볼륨 수입니다.

### 볼륨당 스토리지 크기

볼륨당 스토리지 용량입니다.

### 스토리지 성능

워크로드 요구사항에 기반한 GB당 IOPS(Input/output Operations Per Second)입니다.
* IBM Spectrum Protect Plus의 라이센스를 주문하려면 **라이센스 주문** 탭에 **라이센스를 부여할 VM 수**를 지정하십시오.
* BYOL(Bring Your Own License)을 사용하려는 경우에는 **IBM Spectrum Protect Plus 라이센스** 탭을 클릭한 후 **라이센스 파일 추가**를 클릭하여 소유하고 있는 IBM Spectrum Protect Plus 라이센스 파일을 업로드하십시오.

## IBM Spectrum Protect Plus on IBM Cloud에 대한 배치 프로세스

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}의 배치가 자동화됩니다. 이 서비스가 포함된 인스턴스를 주문하거나 나중에 인스턴스에 서비스를 배치할 때 {{site.data.keyword.vmwaresolutions_short}} 자동화 프로세스를 통해 다음 단계가 완료됩니다.

1. 지정한 설정에 따라, IBM Spectrum Protect Plus 백업 저장소를 위해 {{site.data.keyword.cloud_notm}} 인프라에서 Endurance NFS 스토리지가 주문됩니다.
2. 지정한 설정에 따라, {{site.data.keyword.cloud_notm}} 인프라에서 IBM Spectrum Protect Plus에 대한 여러 라이센스가 주문됩니다. 라이센스는 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 라이센싱하도록 지정한 VM의 수에 따라 10개 가상 머신(VM) 라이센스 팩의 증분으로 주문됩니다. 기존 IBM Spectrum Protect Plus 라이센스를 가져오도록 선택한 경우에는 {{site.data.keyword.cloud_notm}} 인프라에서 라이센스가 주문되지 않습니다.
3. 각 ESXi 서버의 올바른 정적 라우트를 스토리지 사설 서브넷에 추가하는 작업을 포함하여 이 서비스에 대해 주문된 NFS 스토리지가 인스턴스의 기본 클러스터에 있는 모든 ESXi 서버에 마운트됩니다.
4. ESXi 서버에 마운트된 모든 NFS 스토리지 볼륨에 대해 vCenter Server 서버에 NFS 데이터 저장소가 작성됩니다.
5. IBM Spectrum Protect Plus VM은 인스턴스의 기본 클러스터에서 배치되고 활성화되며 구성됩니다.
6. 이 서비스에 대해 주문된 NFS 스토리지가 IBM Spectrum Protect Plus VM에 연결되며 백업 저장소가 구성됩니다.
7. IBM Spectrum Protect Plus VM의 호스트 이름 및 IP 주소가 인스턴스의 DNS 서버에 등록됩니다.

### 관련 링크

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services/spp_considerations.html)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service 계획](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services/managingspp.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus 문서](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

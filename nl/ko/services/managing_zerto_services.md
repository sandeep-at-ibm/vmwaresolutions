---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Zerto on IBM Cloud에 대한 관리 서비스 요청

Zerto on {{site.data.keyword.cloud}} 서비스는 복제 및 재해 복구 기능을 제공합니다. 이러한 기능은 {{site.data.keyword.cloud_notm}}의 VMware 가상 환경에서 데이터를 보호하고 복구하도록 배치 오퍼링으로 통합될 수 있습니다.

Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스를 요청하는 경우, Zerto DR 소프트웨어 및 IBM Resiliency Services를 모두 사용하여 완전히 관리된 재해 복구(DR) 환경을 배치할 수 있습니다.

Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스의 사용 가능한 모델은 다음과 같습니다.

## IBM Orchestrated Managed Services for Zerto

이 모델은 Zerto on {{site.data.keyword.cloud_notm}} 오퍼링을 사용하는 경우 적합합니다.

이 모델에서 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 서비스는 Zerto on {{site.data.keyword.cloud_notm}}에 프로비저닝됩니다. 이 모델에서는 DR 테스팅, RTO/RPO(Recovery Time Objective/Recovery Point Objective) 가시성, 장애 복구 및 장애 조치 기능의 중단 없이 가상 머신, 운영 체제 및 {{site.data.keyword.cloud_notm}}의 데이터에 대한 연속적인 보호가 가능합니다.

모든 기능은 IBM Resiliency Services Global Command Center의 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 대시보드를 통해 관리됩니다.

자세한 정보는 [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration)을 참조하십시오.

## IBM Managed Services for Zerto(Orchestration 없음)

이 모델에서 완전히 관리된 DR 솔루션은 Zerto on {{site.data.keyword.cloud_notm}}에 프로비저닝됩니다. 이 모델은 {{site.data.keyword.cloud_notm}}의 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 서비스 없이 Zerto Virtual Replication에 대한 관리 서비스만 사용하려는 경우 적합합니다.

자세한 정보는 [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top)를 참조하십시오.

## Zerto on IBM Cloud에 대한 관리 서비스를 요청하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **시작하기**를 클릭하십시오.
2. 페이지를 아래로 스크롤하여 **추가 관리 서비스 주문**에서 **Zerto on IBM Cloud에 대한 관리 서비스** 카드를 클릭하십시오.
3. **Zerto on IBM Cloud** 페이지에서 관리 서비스로서 Zerto on {{site.data.keyword.cloud_notm}}에 대한 설명과 기술 스펙을 검토한 후에 **작성**을 클릭하십시오.
4. 사용자의 요구사항에 따라 구성 설정을 지정하거나 기본값을 수락하십시오.
5. **vCenter Server** 또는 **Cloud Foundation**을 클릭하여 서비스를 인스턴스 중 하나에 추가하십시오.
6. 새 인스턴스를 주문하면서 서비스를 추가하려면 **새 인스턴스에 추가**를 클릭한 후에 새 [vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html), [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html) 또는 [Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html) 인스턴스 주문을 계속 진행하십시오.
7. 기존 인스턴스에 서비스를 추가하려면 **기존 인스턴스에 추가**를 클릭하고 목록에서 원하는 인스턴스를 선택한 후에 **프로비저닝**을 클릭하여 주문을 진행하고자 하는지 확인하십시오.

### 관련 링크

* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

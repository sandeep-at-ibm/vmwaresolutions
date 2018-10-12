---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# V1.3 릴리스 정보

이 릴리스에는 새 기능, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## vCenter Server 인스턴스에 대한 공유 파일 레벨 스토리지

이제 공유 NAS(Network Attached Storage)를 vCenter Server 인스턴스에 추가할 수 있습니다. 이 기능을 추가하면 vCenter Server에서 프로덕션 워크로드를 실행할 수 있고 노드 실패가 발생하는 경우 데이터의 유실을 방지할 수 있습니다. NFS(Network File System) File Storage가 vCenter Server 인스턴스에 대한 주문 프로세스의 옵션으로 제공됩니다. 자세한 정보는 [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)을 참조하십시오.

## Zerto 재해 복구 제거

인스턴스의 일부로 Zerto 재해 복구를 주문했거나 기존 인스턴스에 이를 추가했는지에 관계 없이 이제 더 이상 이 서비스가 필요하지 않을 때 이 서비스를 제거할 수 있습니다. 콘솔에서 서비스 제거를 요청한 후 제거 프로세스를 완료할 수 있도록 IBM 지원 센터에서 안내합니다.

자세한 정보는 다음 주제를 참조하십시오.

* [재해 복구 제거](../services/removingzertodr.html)
* [Cloud Foundation 인스턴스 보기](../sddc/sd_viewinginstances.html)
* [vCenter Server 인스턴스 보기](../vcenter/vc_viewinginstances.html)

## VMware NSX Edge for Cloud Foundation 인스턴스

NSX Edge는 이제 주문 중인 새 Cloud Foundation 인스턴스의 일부로 포함됩니다. NSX Edge는 네트워크 에지 보안 및 게이트웨이 서비스를 제공하여 가상화된 네트워크를 격리합니다.

인스턴스 배치 중에 IBM에서 관리 VMware NSX Edge Services Gateway(ESG)가 배치됩니다. 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 가상 머신에서 사용됩니다. 이 ESG는 2개의 인터페이스를 포함하기 위해 배치됩니다. 하나의 인터페이스는 {{site.data.keyword.cloud_notm}} 사설 VLAN에 연결되고, 다른 하나의 인터페이스는 {{site.data.keyword.cloud_notm}} 공용 VLAN에 연결됩니다.

보안을 보장하기 위해 관리 가상 머신에서 시작된 아웃바운드 HTTPS 통신만 허용하도록 방화벽 규칙이
제공됩니다. 이 ESG는 대형 구성에 배치되고 IBM 지원 센터만 구성을 수정할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.

* [Cloud Foundation 인스턴스의 기술 스펙](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [관리 서비스 NSX Edge는 보안 문제점을 발생시킵니까?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 인스턴스 주문 프로세스

두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스에 대한 인스턴스 주문 프로세스가 개선되었습니다.

* 요약 페이지는 주문하기 전에 이용 약관을 검토하고 동의하는 데 쉽게 액세스할 수 있도록 주문된 모든 컴포넌트 및 서비스에 적용 가능한 모든 이용 약관을 표시합니다.
* 주문하기 전에 인스턴스에 대한 주문 요약을 저장하고 인쇄할 수 있습니다. 새 기능을 사용하여 인스턴스 설정 및 비용을 검토하고, 필요한 경우 주문된 컴포넌트를 수정한 후 주문으로 다시 돌아올 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.

* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)

## 인스턴스 관리

인스턴스 관리 프로세스에 대한 새 기능 및 개선사항은 다음과 같습니다.

* 두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스의 경우, ESXi 서버를 인스턴스에 추가하도록 결정하기 전에 ESXi 서버의 예상 비용을 확인하고 검토할 수 있습니다. 추가할 서버의 수를 지정한 후 서버당 매월 예상 비용이 콘솔에 표시됩니다. 자세한 정보는 [Cloud Foundation 인스턴스에 대한 용량 확장 및 축소](../sddc/sd_addingremovingservers.html) 및 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](../vcenter/vc_addingremovingservers.html)를 참조하십시오.
* 두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스의 경우, 총 인스턴스 수는 요약 페이지의 상단에 표시됩니다. 인스턴스 요약 페이지에서 한 번의 클릭만으로 인스턴스를 주문할 수도 있습니다. 또한 요약 페이지에서 프로비저닝 중에 자세한 주문 상태를 볼 수 있습니다. 표시된 상태 위에 마우스를 올려 놓으면 해당 경우 현재 단계 또는 오류에 대한 추가 세부사항을 볼 수 있습니다.
* Cloud Foundation 인스턴스의 경우, 인스턴스 세부사항 페이지는 인스턴스의 배치 히스토리 및 단계별 배치 상태에 대한 정보를 표시합니다. 자세한 정보는 [Cloud Foundation 인스턴스 보기](../sddc/sd_viewinginstances.html)를 참조하십시오.
* Cloud Foundation 인스턴스의 경우, 업데이트 및 패치 프로세스의 사용성이 **업데이트 및 패치** 페이지의 업데이트에 대한 추가 세부사항(예: 패치에 필요한 작동 중단, 업데이트가 스케줄된 시간 및 현재 배치 전에 필수 패치를 적용해야 하는 경우의 시각적 표시)을 제공하여 개선됩니다. 자세한 정보는 [Cloud Foundation 인스턴스에 업데이트 및 패치 적용](../sddc/sd_applyingupdates.html)을 참조하십시오.

## 이메일 알림

이제 인스턴스 배치를 위해 새로 주문되거나 서비스가 인스턴스에서 추가되거나 배치되거나 제거될 때 알림을 받습니다. 기본적으로 알림 설정은 사용으로 설정됩니다. 사용자의 환경 설정에 따라 **설정** 페이지에서 받을 알림을 설정할 수 있습니다. 자세한 정보는 [사용자 계정 및 설정](useraccount.html)을 참조하십시오.

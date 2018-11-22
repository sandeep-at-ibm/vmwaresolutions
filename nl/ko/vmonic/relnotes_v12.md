---

copyright:

  years:  2016, 2018

lastupdated: "2016-12-12"

---

# V1.2 릴리스 정보

이 릴리스에는 새 기능, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 컴포넌트 업데이트

VMware ESXi의 새 버전은 이전 릴리스의 ESXi 6.0 u2에서 업데이트된 vSphere 6.0 u2 p03입니다.

## IBM ID 및 Bluemix 계정 연관

{{site.data.keyword.vmwaresolutions_full}}는 IBM Bluemix® 카탈로그의 인프라 솔루션으로 제공됩니다. **IBM ID** 계정을 Bluemix 계정과 연관시켜야 **IBM ID** 계정으로 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 로그인할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [시작하기](../index.html)
* [Troubleshooting for accessing Bluemix](../../../account/ts_accessing.html){:new_window}

## Zerto 재해 복구

인스턴스를 주문할 때 포함된 Zerto 재해 복구와 함께 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스를 둘 다 주문할 수 있습니다. 또한 인스턴스 세부사항 페이지의 기존 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스에 Zerto 재해 복구를 추가할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)
* [Cloud Foundation 인스턴스 보기](../sddc/sd_viewinginstances.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)
* [vCenter Server 인스턴스 보기](../vcenter/vc_viewinginstances.html)
* [Zerto 재해 복구](../services/addingzertodr.html)

## 가격 정보

이제 주문을 결정하기 전에 주문된 인스턴스의 예상 비용을 확인하고 검토할 수 있습니다. 컴포넌트를 선택한 후 인스턴스를 주문하는 경우 총 비용 및 모든 컴포넌트의 세부 가격이 **요약** 페이지에 표시됩니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)

## 인스턴스 주문 프로세스에 대한 개선사항

인스턴스 주문 프로세스는 다음 개선사항을 통해 크게 향상되었습니다.
* 두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스의 경우, 사용 중인 SoftLayer® 사용자 계정에 필요한 사용자 권한이 있는지, VLAN Spanning이 사용으로 설정되어 있는지, 올바른 API 키가 제공되는지 확인하는 새 유효성 검증 검사가 제공됩니다. 요구사항이 충족되지 않으면 문제점을 해결할 수 있도록 사용자 인터페이스에서 직접 지시사항을 얻으십시오.
*  vCenter Server 인스턴스의 경우, 사용 가능한 하드웨어 및 필요한 ESXi 서버를 갖고 있는 데이터 센터만 표시되도록 인스턴스 컴포넌트를 선택하는 주문이 최적화됩니다. 이 변경은 나중에 발생할 수 있는 오류의 가능성을 최소화합니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)

## 추가 이메일 알림

이제 새 ESXi 서버가 인스턴스에 추가되고 기존 ESXi 서버가 다시 이동될 때 이메일로 알림을 받습니다. 또한 인스턴스가 삭제될 때 이메일로 알림을 받습니다. 기본적으로 알림 설정은 사용으로 설정됩니다. 사용자의 환경 설정에 따라 **설정** 페이지에서 받을 알림을 설정할 수 있습니다.

자세한 정보는 [사용자 계정 및 설정](useraccount.html)을 참조하십시오.

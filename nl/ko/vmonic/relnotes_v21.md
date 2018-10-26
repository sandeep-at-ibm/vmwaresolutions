---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# V2.1 릴리스 정보

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)으로 알려진 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

자세한 정보는 [스펙터(Spectre) 및 멜트다운(Meltdown) 취약점 해결](../vmonic/trbl_fix_spectre.html)을 참조하십시오.

## VMware HCX on IBM Cloud

HCX on {{site.data.keyword.cloud_notm}} 서비스는 이제 vSphere 6.5에서 실행되고 V2.1 이상 릴리스에 배치되거나 V2.1 이상 릴리스로 업그레이드되는 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 이 서비스는 {{site.data.keyword.cloud_notm}}로 온프레미스 데이터 센터의 네트워크를 원활하게 확장할 수 있으며, 이를 통해 변경사항 없이 온프레미스 데이터 센터와 {{site.data.keyword.cloud_notm}} 간에 가상 머신(VM)의 양방향 마이그레이션을 수행할 수 있습니다. 계층 2 브릿지를 구축함으로써, HCX는 WAN 최적화, 중복 제거, 압축 및 암호화를 사용하여 더 빠르고 안전하게 Direct Link 또는 VPN 터널을 통해 데이터를 마이그레이션합니다. VM의 대량 마이그레이션이 VMware vSphere 5.1 이상과 역호환됩니다. vSphere 6.0 이상 온프레미스를 사용하는 경우에는 온프레미스와 {{site.data.keyword.CloudDataCent_notm}} 간의 vMotion 라이브(전원 켜기) VM을 수행할 수 있습니다. HCX 사용 시 데이터 센터에 VMware NSX를 설치할 필요는 없습니다.

인스턴스를 주문할 때 포함된 HCX on {{site.data.keyword.cloud_notm}} 서비스와 함께 Cloud Foundation 또는 vCenter Server 인스턴스를 주문하거나 인스턴스 세부사항 페이지에 있는 **서비스** 탭에서 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

온프레미스 HCX 설치의 라이센스 부여 및 활성화를 위해 온프레미스 HCX 인스턴스도 주문할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [HCX on {{site.data.keyword.cloud_notm}}에 대한 고려사항](../services/hcx_considerations.html)
* [HCX on {{site.data.keyword.cloud_notm}} 관리](../services/managinghcx.html)
* [온프레미스 HCX 인스턴스에 대한 고려사항](../services/standalone_considerations.html)
* [온프레미스 HCX 인스턴스 주문](../services/standalone_orderingserviceinstances.html)

## VMware Cloud Foundation 및 vCenter Server에 대한 좀 더 유연한 고유한 라이센스 모델 가져오기

새 클러스터 작성 시 BYOL(Bring Your Own Licence) 또는 IBM 제공 구독 라이센스 구매는 이제 2.1 이상 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 이러한 옵션을 통해 기존의 컴포넌트 키를 사용하거나 IBM에서 라이센스를 임대할 수 있습니다. V2.1 이전에는 BYOL을 수행하는 경우 특정 VMware 컴포넌트에 대한 IBM 제공 라이센스를 구매할 수 없었습니다. 현재는 클러스터당 라이센싱에 VMware vSphere 및 VMware vSAN만 사용 가능합니다.

또한 키에 대한 라이센스가 부여된 클러스터에 노드를 추가하는 경우 콘솔은 노드의 수가 키 용량을 초과하면 새 라이센스 키를 제공하도록 프롬프트를 표시합니다.

자세한 정보는 다음 주제를 참조하십시오.

* [Cloud Foundation 인스턴스에 대한 클러스터 추가 및 보기](../sddc/sd_addingviewingclusters.html)
* [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](../vcenter/vc_addingviewingclusters.html)
* [BYOL에 대한 FAQ](../vmonic/faq_byol.html)

## Zerto on IBM Cloud 서비스 컴포넌트 업데이트

V2.1 이상 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스에 배치되는 Zerto on {{site.data.keyword.cloud_notm}} 서비스의 경우, Zerto Virtual Replication 5.5u2가 프로비저닝됩니다. Zerto VRA(Virtual Replication Appliances)는 이제 성능상의 이유로 로컬 데이터 저장소가 아닌 관리 데이터 저장소(vSAN 또는 Endurance)에 배치됩니다. 기존 VRA가 있는 경우에는 더 나은 성능을 위해 스토리지를 관리 데이터 저장소로 마이그레이션하는 것을 고려하십시오.

자세한 정보는 [Zerto on {{site.data.keyword.cloud_notm}} 개요](../services/addingzertodr.html)를 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트

### 네트워크 MTU 구성 설정

V2.1 이상 릴리스의 경우 새 vCenter Server 인스턴스는 공용 분산 가상 스위치(DVS)가 MTU 1500(기본값)으로 설정된 상태로 주문됩니다. 자세한 정보는 [vCenter Server 명세서](../vcenter/vc_bom.html)의 _네트워크 MTU 구성 설정_을 참조하십시오.

### VMware ESXi 패치 및 업데이트를 호스트로 자동 적용

V2.0 이전 VMware vCenter Server 인스턴스에서 패치가 클러스터에 추가된 ESXi 호스트로 자동 적용되지 않았습니다.

V2.1 이상 인스턴스에서 패치 레벨이 초기 인스턴스가 프로비저닝되었던 때의 패치 레벨과 일치하도록 자동화가 패치를 새 ESXi 호스트에 적용합니다. 이후 패치 및 업데이트를 수동으로 적용해야 합니다.
VMware 패치 및 업데이트가 향후 릴리스에서 사용 가능할 때 자동화 서비스에서 기존 인스턴스의 ESXi 호스트를 스캔하고 최신 패치 및 업데이트를 수동으로 적용하도록 이메일로 리마인더를 전송합니다.

자세한 정보는 [vCenter Server 인스턴스에 업데이트 적용](../vcenter/vc_applyingupdates.html)을 참조하십시오.

### VMware NSX 라이센스 업그레이드에 대한 가격 예상

이제 VMware NSX Advanced 또는 Enterprise 에디션으로 업그레이드하도록 주문을 제출하기 전에 가격 예상을 확인할 수 있습니다. 가격은 vCenter Server 인스턴스의 ESXi 호스트 수를 기반으로 합니다. 이 구매는 NSX 라이센스 키만 변경하고 VMware NSX Base 에디션을 Advanced 또는 Enterprise 에디션으로 업그레이드합니다. 구매는 NSX 소프트웨어 버전을 업그레이드하지 않습니다.

자세한 정보는 [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)를 참조하십시오.

### 클러스터 최대 서버가 32개에서 증가함

인스턴스의 기본 클러스터의 경우, 최대 51개의 서버를 배치하거나 확장할 수 있습니다. 인스턴스의 모든 후속 클러스터의 경우, 최대 59개의 서버를 배치하거나 확장할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](../vcenter/vc_addingviewingclusters.html)를 참조하십시오.

**참고:** 이 기능은 V2.1 이상에 배치된 인스턴스에서만 사용할 수 있습니다. V2.1 이전 릴리스에서 V2.1로 업그레이드된 인스턴스에는 이 옵션이 없습니다.

### IBM Cloud Bare Metal Server 구성 옵션을 사용자 정의한 사용자

Bare Metal Server 구성을 사용자 정의한 사용자는 이제 듀얼 Intel Xeon Gold 6140(총 36개의 코어, 2.3 GHz 포함)를 제공합니다.

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)

### 개별 NFS 파일 공유 구성

이제 개별적으로 NFS 파일 공유를 구성할 수 있습니다. 각 개별 파일 공유에 대해 파일 크기 및 성능 레벨을 선택하거나 주문하는 모든 파일의 공유에 대해 동일한 파일 크기 및 성능 레벨을 선택하십시오.

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)
* [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](../vcenter/vc_addingviewingclusters.html)

## 사용자 인터페이스 업데이트 및 개선사항

개선사항은 사용자 인터페이스를 통해 수행됩니다.

* 왼쪽 탐색 분할창에서 더 이상 **인스턴스 주문** 옵션을 사용할 수 없습니다. **시작하기**를 클릭하여 인스턴스 주문을 위한 단계를 완료하십시오.
* 인스턴스 주문 시 **기본** 페이지의 **하위 도메인 접두부** 필드의 이름이 **하위 도메인 레이블**로 변경됩니다.
* 기본 또는 보조 vCenter Server 또는 Cloud Foundation 인스턴스 주문 시 **요약** 페이지의 가격 예상을 확인하는 것 외에도, 이제 인스턴스 주문에 대한 세부사항을 제공할 때 페이지에서 가격 예상을 계산할 수 있습니다.
* 탐색의 대체 방법으로 이동 경로 탐색이 **배치된 인스턴스** 페이지에 추가됨에 따라 상위 페이지에 도달하는 데 필요한 단계의 수가 줄어듭니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

## 새로 작성되고 업데이트된 문서

새 developerWorks 레시피는 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}를 사용하여 전용 스토리지를 기존 {{site.data.keyword.vmwaresolutions_full}} 배치에 연결하는 방법에 대한 단계별 지시사항에서 찾을 수 있습니다. 자세한 정보는 [Steps to attach dedicated storage to VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)를 참조하십시오.

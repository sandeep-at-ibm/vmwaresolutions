---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: FAQ, host, ESXi server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# ESXi 서버에 대한 FAQ
{: #faq_esxi}

{{site.data.keyword.vmwaresolutions_full}} 콘솔에서 관리되는 ESXi 서버에 대한 자주 묻는 질문의 답을 찾으십시오.

## 몇 개의 ESXi 서버를 내 인스턴스에 추가할 수 있습니까?
{: #faq_esxi-instance}
{: faq}

vCenter Server 인스턴스를 사용하여 최대 51개의 ESXi 서버를 보유하도록 기본 클러스터를 확장할 수 있습니다. 기본이 아닌 각 클러스터는 최대 59개의 ESXi 서버를 보유하도록 확장할 수 있습니다. 최대 10개의 클러스터를 인스턴스에 추가할 수 있으므로 모든 클러스터의 각 배치된 인스턴스에는 최대 51 + 9x59 = 582개의 ESXi 서버가 있을 수 있습니다.

## 몇 개의 ESXi 서버를 클러스터에 추가할 수 있습니까?
{: #faq_esxi-cluster}
{: faq}

V2.2 이상에 배치된 인스턴스의 경우, 최대 51개의 ESXi 서버를 초기 클러스터에 추가하고 최대 59개의 ESXi 서버를 추가된 클러스터에 추가할 수 있습니다.

V2.1 이전에 배치된 인스턴스의 경우, 필요한 vSAN 지원을 사용으로 설정하여 32개가 초과하도록 클러스터 크기를 늘려야 합니다. 필요한 vSAN 지원을 사용으로 설정하려면 다음 단계를 완료하십시오.

1. 각 배치된 ESXi 서버에서 다음 명령을 실행하십시오.

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 각 ESXi 서버를 다시 시작하십시오. 자세한 정보는 [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081)를 참조하십시오.
3. 추가된 가상 머신 및 ESXi 서버를 포함하도록 vCenter Server의 크기를 늘려야 합니다.
4. IBM 지원 센터 티켓을 열어 1 - 3단계를 완료하여 vSAN 변경사항을 수동으로 적용했음을 표시하십시오. 티켓에서 업그레이드된 인스턴스가 32개가 넘는 ESXi 서버에 사용되도록 요청하십시오.

## ESXi 서버 이름 및 IP 주소를 변경할 수 있습니까?
{: #faq_esxi-change-name-ip}
{: faq}

ESXi 서버 이름 및 IP 주소는 Windows DNS 해석을 위해 등록되었으므로 변경할 수 없습니다. 변경하면 배치 중에 실패가 발생하거나 vCenter Server 기능의 실패가 발생할 수 있습니다.

{{site.data.keyword.cloud_notm}} 사용자 인터페이스에서 **디바이스 이름 바꾸기** 기능을 사용하여 ESXi 서버 이름을 변경하지 마십시오. 이 기능은 실제로 ESXi 서버의 FQDN을 변경하지만 구성된 vCenter Server 및 Windows VSI 호스트 등록이 올바르지 않고 실패가 발생할 수 있습니다.
{:note}

## ESXi 서버에 루트 액세스를 사용 안함으로 설정할 수 있습니까?
{: #faq_esxi-disable-root}
{: faq}

ESXi 서버에서 루트 액세스가 계속해서 사용으로 설정되는 것이 좋습니다. 그렇지 않으면 {{site.data.keyword.vmwaresolutions_short}} 기능의 실패가 발생할 수 있습니다.

필요한 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 ESXi 서버의 상태가 **사용할 준비가 됨**으로 설정된 후 루트 액세스를 사용 안함으로 설정할 수 있습니다.

후속 자동화 오퍼레이션(예: 파일 공유를 추가하거나 제거하는 경우 또는 Zerto on {{site.data.keyword.cloud_notm}}와 같은 추가 기능 서비스를 설치하는 경우)에 대한 루트 액세스를 다시 사용으로 설정해야 합니다.

## 다른 위치에서 스토리지를 마운트하도록 내 ESXi 서버에서 정적 라우트를 추가할 수 있습니까?
{: #faq_esxi-static-routes}
{: faq}

스토리지에 맞는 정적 라우트를 추가할 수 있지만 주의하여 수행해야 합니다. 그렇지 않으면 기존 공유가 마운트 해제될 수 있습니다.

vMotion에 대한 정적 라우트 추가는 지원되지 않습니다. vMotion 서브넷 구성을 변경하면 {{site.data.keyword.vmwaresolutions_short}} 기능의 실패가 발생할 수 있습니다.
{:note}

## 관련 링크
{: #faq_esxi-related}

* [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingviewingclusters#vc_hybrid_addingviewingclusters)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

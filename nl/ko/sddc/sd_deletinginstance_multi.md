---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 다중 사이트 구성에서 Cloud Foundation 인스턴스 삭제
{: #sd_deletinginstance_multi}

다중 사이트 구성에서 Cloud Foundation 인스턴스를 삭제하려고 계획하기 전에, 다음 고려사항을 검토하십시오.

Cloud Foundation 인스턴스를 삭제하는 경우 다음 컴포넌트가 순차적으로 릴리스됩니다.
1. 배치된 모든 서비스
2. 지원 및 서비스 요금
3. VMware 제품 라이센스
4. ESXi 서버
5. 서브넷
6. VLAN

리소스 종속성으로 인해 인스턴스 삭제 시 인스턴스의 컴포넌트가 즉시 릴리스되지 않습니다. 예를 들어, {{site.data.keyword.cloud_notm}} 비용 청구 주기 종료 시 발생하는 {{site.data.keyword.cloud}} 인프라로 ESXi 서버가 완전히 재확보될 때까지 서브넷 및 VLAN을 삭제할 수 없습니다. {{site.data.keyword.cloud_notm}} 비용 청구 주기 종료 시 일반적으로 청구 주기는 30일이고 서브넷 및 VLAN이 삭제되며 인스턴스 삭제가 완료됩니다.

삭제된 인스턴스에 대한 {{site.data.keyword.cloud_notm}} 비용 청구 주기 종료 시까지 비용이 청구됩니다.
{:note}

## 다중 사이트 구성에서 Cloud Foundation 인스턴스를 삭제하는 프로시저
{: #sd_deletinginstance_multi-procedure}

1. 보조 Cloud Foundation 인스턴스에서 모든 서비스를 제거하십시오.
2. 삭제할 보조 인스턴스로 확장되는 NSX 오브젝트가 없는지 확인하십시오.
3. 기본 SSO(Single Sign-On) 도메인에서 보조 vCenter 및 PSC(Platform Services Controller)를 삭제하십시오. 자세한 정보는 [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}을 참조하십시오.
4. 로컬 도메인 컨트롤러 VSI(Virtual Service Instance)를 내리십시오. 자세한 정보는 [내리기 도메인 컨트롤러 및 도메인](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}을 참조하십시오.
5. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 보조 Cloud Foundation 인스턴스를 삭제하십시오.
6. 다중 사이트 구성에서 모든 보조 Cloud Foundation 인스턴스에 대해 1 - 5단계를 반복하십시오.
7. 모든 보조 인스턴스를 삭제하고 나면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 기본 인스턴스도 삭제할 수 있습니다.

## 관련 링크
{: #sd_deletinginstance_multi-related}

* [Cloud Foundation 인스턴스 삭제](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance)
* [Cloud Foundation 인스턴스에서 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)

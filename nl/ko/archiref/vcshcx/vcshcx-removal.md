---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# HCX 제거
{: #vcshcx-removal}

HCX 제거에서는 확장 네트워크가 더 이상 사용되지 않는다고 가정합니다. 다음 프로시저에 따라 HCX를 제거하십시오.

1. 모든 확장 네트워크의 확장을 해제합니다.
2. 클라이언트 사용자 인터페이스(UI)에서 모든 L2C 어플라이언스를 삭제합니다. L2C 어플라이언스가 웹 UI에서 사라질 때까지 기다립니다.
3. CGW를 삭제합니다. 그러면 WAN Opt도 제거됩니다. CGW와 WAN Opt 어플라이언스가 제거될 때까지 기다립니다.
4. 클라이언트와 클라우드 특에서 HCX 관리자 어플라이언스 가상 머신(VM)을
종료하고 삭제합니다.
5. NSX 클라우드 측에서 HCX ESG를 제거합니다.
6. vCenter Mob 브라우저를 사용하여 HCX 스냅인을 제거합니다.

## 관련 링크
{: #vcshcx-removal-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 개요](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   

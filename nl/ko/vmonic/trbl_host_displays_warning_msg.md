---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# ESXi 서버에 구성 문제가 표시됨
{: #trbl_host_displays_warning_msg}

## 문제점
{: #trbl_host_displays_warning_msg-problem}

구성 문제가 vSphere 클라이언트의 VMware ESXi 서버에 있는 **모니터** 탭의 **문제** 탭에 표시됩니다.

다음 메시지가 ESXi 서버의 **문제** 탭에 표시됩니다.

`This host currently has no management network redundancy`

이 메시지는 중복성을 제공하는 사설 분배 스위치에 사용할 수 있는 두 개의 업링크가 있는 경우에도 표시됩니다.

## 해결
{: #trbl_host_displays_warning_msg-resolution}

이는 VMware의 알려진 문제입니다. 문제점을 해결하려면 [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/s/article/2008602){:new_window}의 지시사항을 따르십시오.

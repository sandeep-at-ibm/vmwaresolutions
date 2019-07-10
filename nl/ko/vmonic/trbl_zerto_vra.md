---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Zerto VRA, Zerto uninstall

subcollection: vmware-solutions


---

# Zerto on IBM Cloud가 설치 제거된 후 vCenter 콘솔의 ESXi 호스트에 Zerto VRA가 표시됨
{: #trbl_zerto_vra}

## 문제점
{: #trbl_zerto_vra-problem}

{{site.data.keyword.slportal}}을 사용하여 Zerto on {{site.data.keyword.cloud}} 서비스를 설치 제거한 후 Zerto Virtual Replication Appliances(VRA)가 제거되지 않습니다.

## 해결
{: #trbl_zerto_vra-resolution}

vCenter 콘솔에서 VRA를 수동으로 제거하십시오.

1. vCenter 콘솔에 로그인하십시오.
2. **호스트 및 클러스터**를 클릭하고 이름이 **Z-VRA-**로 시작하는 가상 머신을 찾으십시오. 예를 들면, **Z-VRA-host0-vcs40dal.vcs.icvs.org**입니다.
3. **Z-VRA-** 가상 머신을 오른쪽 마우스로 클릭하고 **디스크에서 삭제**를 클릭하십시오.

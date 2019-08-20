---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Shared 리소스 관리
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared는 시범 오퍼링으로 제공됩니다.
{:note}

고객은 {{site.data.keyword.vmwaresolutions_short}} 오퍼링을 사용하여 가상 데이터 센터의 라이프사이클을 관리합니다.

웹 UI 또는 공용 API를 사용하여 다음과 같은 기능이 지원됩니다.
- 가상 데이터 센터 인스턴스 보기
- vCloud 관리 콘솔에 액세스
- 가상 데이터 센터 인스턴스 크기 조정
- 가상 데이터 센터 인스턴스 삭제
- VMware 서비스를 가상 데이터 센터 인스턴스에 추가 및 제거(**향후**)

## 가상 데이터 센터 인스턴스 보기
{: #shared_managing-viewing}

사용자 계정에 대해 프로비저닝된 모든 가상 데이터 센터 인스턴스의 요약을 보려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. 콘솔 배너에서 사용자 계정 아이콘을 클릭한 다음 **계정** 필드를 클릭하여 인스턴스를 확인하려는 사용자 계정을 선택하십시오.  
3. **IBM Cloud VMware Solutions Shared** 테이블에서, 선택된 사용자 계정에서 프로비저닝된 인스턴스의 목록을 보십시오.

| 항목        |설명       |  
|:------------- |:------------- |
|이름 |인스턴스의 이름입니다. |
|유형 |가상 데이터 센터의 유형입니다. |
| 위치 |인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}입니다. |  
|작성 시간 |인스턴스가 작성된 날짜 및 시간입니다. |
|상태 |인스턴스의 상태입니다. |

{: caption="표 1. 가상 데이터 센터 인스턴스 항목" caption-side="top"}

인스턴스에는 다양한 상태가 있습니다.

|상태        |설명       |
|:------------- |:------------- |
|작성 중 |인스턴스가 작성 중입니다. |
|사용할 준비가 됨 |인스턴스를 사용할 준비가 되었습니다. |
|수정 중 |인스턴스가 수정 중입니다. |
|삭제 중 |인스턴스가 삭제 중입니다. |
|삭제됨 |인스턴스가 삭제됩니다. |

{: caption="표 2. 가상 데이터 센터 인스턴스에 대한 상태 설명" caption-side="top"}

## 가상 데이터 센터 세부사항을 보는 프로시저
{: #vc_viewinginstances-procedure-view-vdc-details}

인스턴스의 특성 세부사항을 보려면 다음 작업을 수행하십시오.

1. **IBM Cloud VMware Solutions Shared** 테이블에서 인스턴스 이름을 클릭하십시오.
2. **특성**에서 인스턴스의 세부사항을 보십시오.

|특성        |설명       |
|:------------- |:------------- |
|이름 |인스턴스의 이름입니다. |
|유형 |가상 데이터 센터 유형입니다. |
| 위치 |인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}입니다. |
|ID |인스턴스의 ID입니다. |
|작성 시간 |인스턴스가 작성된 날짜 및 시간이며, 청구가 시작되는 날짜 및 시간입니다. |
|vCPU |언제든지 가상 데이터 센터에서 사용될 수 있는 CPU의 한계 또는 예약된 양입니다. |
| RAM |언제든지 가상 데이터 센터에서 사용될 수 있는 메모리의 한계 또는 예약된 양입니다. |
|공인 IP |모든 가상 데이터 센터는 vApp 및 VM을 인터넷에 연결하는 데 사용될 수 있는 5개의 공인 IP 주소와 함께 제공됩니다. |

{: caption="표 3. 가상 데이터 센터 특성" caption-side="top"}

## vCloud Director 관리 콘솔에 액세스
{: #shared_managing-accessing}

vCloud Director 관리 콘솔을 통해 가상 데이터 센터를 관리합니다.

vCloud Director 관리 콘솔에 대한 첫 번째 액세스는 **admin** 인증 정보를 사용하여 수행됩니다. **위치 비밀번호 재설정** 링크를 사용하여 가상 데이터 센터 세부사항 페이지에서 비밀번호를 생성하십시오. 이 조치는 초기의 복잡한 무작위 비밀번호를 생성하며, 비밀번호는 언제든지 재설정할 수 있습니다.

{{site.data.keyword.vmwaresolutions_short}} 오퍼링은 **admin** 비밀번호를 저장하지 않습니다. 비밀번호가 생성된 후 캡처해야 합니다. 비밀번호를 분실한 경우 새 비밀번호를 생성해야 합니다.

동일한 위치에 있는 모든 가상 데이터 센터의 **admin** 비밀번호는 동일합니다. 하나의 가상 데이터 센터 인스턴스에서 비밀번호를 재설정하면 동일한 위치에 있는 모든 가상 데이터 센터 인스턴스의 vCloud Director 관리 콘솔에 액세스하기 위한 **admin** 비밀번호가 재설정됩니다.

첫 번째 **admin** 비밀번호가 생성된 후 세부사항 페이지의 오른쪽 상단 모서리에서 **vCloud Director 포털** 단추가 사용 가능하게 됩니다. vCloud Director 관리 콘솔에 액세스하려면 **vCloud Director 포털**을 클릭하십시오. 로그인하려면 사용자 이름 **admin** 및 **위치 비밀번호 재설정** 링크에서 얻은 비밀번호를 사용하십시오.

## 가상 데이터 센터 인스턴스 크기 조정
{: #shared_managing-resizing}

가상 데이터 센터 인스턴스가 **사용할 준비가 됨**상태이면 언제든지 가상 데이터 센터에 지정된 리소스의 양을 변경할 수 있습니다. 

가상 데이터 센터 세부사항 페이지에서 가상 데이터 센터 인스턴스에 대한 vCPU 또는 RAM 리소스의 크기를 조정하십시오. 세부사항 페이지에서 **리소스** 옆에 있는 연필 아이콘을 클릭하고 vCPU 또는 RAM 특성의 값을 변경하십시오.

마지막으로 주문하기 전에 구성과 예상 비용을 확인하십시오.

  가상 데이터 센터 리소스를 현재 활성 상태인 리소스 사용량보다 낮은 레벨로 낮출 수 없기 때문에 vCPU 및 RAM 리소스를 낮추는 동안 사용 중인 경우에는 구성 변경에 실패합니다.
{:note}

변경되는 동안 가상 데이터 센터 인스턴스가 **수정 중** 상태가 됩니다. 리소스를 사용할 준비가 되면 상태가 **사용할 준비가 됨**으로 변경됩니다. 

## 가상 데이터 센터 인스턴스 삭제
{: #shared_managing-deleting}

**사용할 준비가 됨** 상태인 경우 가상 데이터 센터 인스턴스를 삭제할 수 있습니다. 가상 데이터 센터 세부사항 페이지 또는 IBM Cloud VMware Solutions Shared 리소스 테이블에서 삭제 오퍼레이션을 수행하십시오.

세부사항 페이지에서 세부사항 페이지의 맨 위 오른쪽에 있는 오버플로우 메뉴 옵션에서 **삭제** 아이콘을 클릭하십시오. 그런 다음 인스턴스를 삭제할 것인지 확인하십시오.

IBM Cloud VMware Solutions Shared 리소스 테이블에서 삭제할 인스턴스를 찾고 **조치** 열에서 **삭제** 아이콘을 클릭하십시오. 그런 다음 인스턴스를 삭제할 것인지 확인하십시오.

## 관련 링크
{: #shared_managing-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared의 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared On-Demand 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Shared 예약 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}

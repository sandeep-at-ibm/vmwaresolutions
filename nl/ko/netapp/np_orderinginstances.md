---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select 인스턴스 주문
{: #np_orderinginstances}

전용 및 고가용성 소프트웨어 정의 스토리지 어플라이언스와 함께 VMware 가상화된 플랫폼을 배치하려면 NetApp ONTAP Select 인스턴스를 주문하십시오.

## 요구사항
{: #np_orderinginstances-req}

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)를 참조하십시오.
*  [NetApp ONTAP Select 인스턴스에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)의 요구사항 및 고려사항을 검토했습니다.

인스턴스 주문 또는 배치 중에 설정되는 값은 수정하지 마십시오. 수정하는 경우 인스턴스를 사용할 수 없게 됩니다. 예를 들어, 공용 네트워킹이 종료되는 경우, 서버 및 가상 서버 인스턴스(VSI)가 Vyatta 뒤로 이동하는 경우, IBM CloudBuilder VSI가 중지하거나 삭제된 경우입니다.
{:important}

## 시스템 설정
{: #np_orderinginstances-sys-settings}

NetApp ONTAP Select 인스턴스를 주문할 때는 다음 기본 설정을 지정해야 합니다.

### 인스턴스 이름
{: #np_orderinginstances-instance-name}

인스턴스 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 인스턴스 이름은 영문자로 시작하고 영숫자로 끝나야 합니다.
* 인스턴스 이름의 최대 길이는 10자입니다.
* 인스턴스 이름은 계정 내에서 고유해야 합니다.

## 네트워크 인터페이스 설정
{: #np_orderinginstances-network-interface-settings}

NetApp ONTAP Select 인스턴스를 주문할 때는 다음 네트워크 인터페이스 설정을 지정해야 합니다.

### 호스트 이름 접두부
{: #np_orderinginstances-host-name-prefix}

호스트 이름 접두부는 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  호스트 이름 접두부는 영숫자 문자로 시작하고 끝나야 합니다.
*  호스트 이름 접두부의 최대 길이는 10자입니다.

### 하위 도메인 레이블
{: #np_orderinginstances-subdomain-label}

하위 도메인 레이블은 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  하위 도메인 레이블은 영문자로 시작하고 영숫자로 끝나야 합니다.
*  하위 도메인 레이블의 최대 길이는 10자입니다.
*  하위 도메인 레이블은 계정 내에서 고유해야 합니다.

### 도메인 이름
{: #np_orderinginstances-domain-name}

루트 도메인 이름은 다음 요구사항을 충족해야 합니다.
* 도메인 이름은 마침표(.)로 구분된 두 개 이상의 문자열로 구성되어야 합니다.
* 첫 번째 문자열은 영문자로 시작하고 영숫자로 끝나야 합니다.
* 마지막 문자열을 제외한 모든 문자열은 영숫자 및 대시(-) 문자만 포함할 수 있습니다.
* 마지막 문자열은 영문자만 포함할 수 있습니다.
* 마지막 문자열의 길이는 2 - 24자 사이여야 합니다.

호스트 및 가상 머신(VM)에 대한 FQDN(Fully Qualified Domain Name)의 최대 길이는 50자입니다. 도메인 이름은 이 최대 길이를 포함할 수 있어야 합니다.
{:note}

## 라이센스 부여 설정
{: #np_orderinginstances-licensing-settings}

네 개의 {{site.data.keyword.baremetal_short}}에 하나씩, 네 개의 NetApp 라이센싱 파일을 업로드해야 합니다. NetApp 영업 팀에 문의하여 고성능 또는 고용량 배치에 적합한 라이센싱을 확보하십시오.

## Bare Metal Server 설정
{: #np_orderinginstances-bare-metal-settings}

### 데이터 센터 위치
{: #np_orderinginstances-dc-location}

인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}를 선택해야 합니다.

### Bare Metal Server 구성
{: #np_orderinginstances-bare-metal-config}

사용자의 요구사항에 따라 Bare Metal Server 구성을 선택하십시오.
* **고성능(중형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 1.9TB SSD 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 59TB
* **고성능(대형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 3.8TB SSD 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 118TB
* **고용량** – 표준 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 64GB RAM / 노드당 34개의 4TB SATA 드라이브 용량 / 4 노드 클러스터의 유효한 용량 – 190TB

3.8TB SSD(Solid-State Disk) 드라이브는 {{site.data.keyword.CloudDataCent_notm}}에서 일반적으로 사용 가능하게 되는 경우 지원됩니다.
{:note}

### Bare Metal Server 수
{: #np_orderinginstances-bare-metal-number}

기본적으로 NetApp ONTAP Select 인스턴스의 ESXi 서버 수는 4입니다. 이를 변경할 수 없습니다. 모든 ESXi 서버는 구성을 공유합니다.

## NetApp ONTAP Select 인스턴스를 주문하는 프로시저
{: #ordering-netapp-ontap-select-instances}

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **NetApp ONTAP Select**를 클릭하십시오.
2. **NetApp ONTAP Select** 페이지에서 **작성**을 클릭하십시오.
3. **NetApp ONTAP** 페이지에서 인스턴스 이름을 입력하십시오.
4. **호스트 이름 접두부**, **하위 도메인 레이블** 및 **도메인 이름**을 입력하여 네트워크 인터페이스 설정을 완료하십시오.
5. **라이센스 파일 추가**를 클릭하고 네 개의 {{site.data.keyword.baremetal_short}}에서 필요로 하는 네 개의 NetApp 라이센스 파일을 업로드하여 라이센싱 설정을 완료하십시오.
6. Bare Metal Server 설정을 완료하십시오.
   1. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.
   2. Bare Metal Server 구성을 선택하십시오.
7. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
    1. 인스턴스의 설정을 검토하십시오.
    2. 인스턴스의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창에서 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
    3. 비용이 청구되는 계정이 올바른지 확인한 후 **아래 나열된 계정에 비용이 청구될 것임을 이해함** 선택란을 선택하십시오.
    4. 주문에 적용되는 이용 약관에 대한 링크를 클릭하십시오. 이러한 이용 약관에 동의하는지 확인한 후 **아래 나열된 서드파티 서비스 계약을 읽었으며 이에 동의함** 선택란을 선택하십시오.
    5. **프로비저닝**을 클릭하십시오.

## 결과
{: #np_orderinginstances-results}

인스턴스의 배치가 자동으로 시작됩니다. 주문이 처리 중이라는 확인을 받은 후 인스턴스 세부사항을 보고 배치의 상태를 확인할 수 있습니다.

인스턴스가 성공적으로 배치된 경우에는 [NetApp ONTAP Select 인스턴스의 기술 스펙](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs)에서 설명된 컴포넌트가 VMware 가상 플랫폼에 설치됩니다.

인스턴스를 사용할 준비가 되면 인스턴스의 상태가 **사용할 준비가 됨**으로 변경되고 이메일로 알림을 받습니다.

## 수행할 작업
{: #np_orderinginstances-next}

주문한 NetApp ONTAP Select 인스턴스를 보고 관리하십시오.

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌, {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에 작성되는 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.
{:important}

**주의:** {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트(인스턴스 주문 시 {{site.data.keyword.cloud_notm}} 계정에 설치된)를 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  컴포넌트 전원 끄기

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

## 관련 링크
{: #np_orderinginstances-related}

* [NetApp ONTAP Select 인스턴스 보기](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [NetApp ONTAP Select 인스턴스 삭제](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [NetApp ONTAP Select 배치에 전용 스토리지 연결](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)

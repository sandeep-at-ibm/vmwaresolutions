---

copyright:

  years:  2016, 2019

lastupdated: "2018-01-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# WebSphere Application Server의 Stock Trader를 컨테이너의 Stock Trader로 변환

Stock Trader 현대화 과정에서 다음 단계는 가상 머신(VM)에서 실행 중인 워크로드를 컨테이너에서 실행 중인 워크로드로 변환하는 것입니다.

계속하기 위해 Todd와 Jane은 Transformation Advisor를 실행하여 Stock Trader 워크로드를 분석하고, 마이그레이션 복잡도를 식별하며, 변경을 권장합니다. 준비가 되면, Transformation Advisor를 사용하여 Stock Trader를 {{site.data.keyword.icpfull_notm}}에서 실행되는 Liberty 컨테이너에 배치합니다.

## IBM Cloud Private 준비

Todd는 먼저 {{site.data.keyword.icpfull_notm}}를 설치해야 합니다. Todd는 VMware on {{site.data.keyword.cloud_notm}} 환경을 사용하므로, {{site.data.keyword.cloud_notm}}의 VMware VM에서 실행되는 완전한 {{site.data.keyword.icpfull_notm}} 인스턴스를 제공하는 {{site.data.keyword.cloud_notm}} Private Hosted 오퍼링을 사용하려고 합니다. 

기본 대시보드는 카탈로그에서 Kubernetes 클러스터, 보안, 스토리지와 배치를 관리하기 위해 포괄적인 사용자 인터페이스를 제공합니다.

### 스토리지 준비

{{site.data.keyword.cloud_notm}} Private Hosted는 GlusterFS로 즉시 사용 가능하도록 구성되고 VM에서 파일 스토리지를 전용 GlusterFS 노드로 제공합니다. GlusterFS의 가치는 동적 프로비저닝을 가능하게 하는 것입니다. Todd가 원할 경우, 추가 VM을 NFS 서버로 설정할 수 있습니다.

Todd는 사용 가능한 NFS 서버를 원했기 때문에 'toddnfs'라는 VM을 식별하여 다음 [단계](https://help.ubuntu.com/community/SettingUpNFSHowTo)를 실행했습니다.

Todd가 다음 명령을 실행하여 새 NFS 서버를 작성합니다.

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

다음으로, Todd는 다음 행을 추가합니다.

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

그런 다음 Todd는 각 VM에서 다음 명령을 실행하여 각 {{site.data.keyword.icpfull_notm}} 작업자 VM에 NFS를 설치합니다.

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd는 다음 명령을 실행하여 설치된 버전을 확인합니다.

`apt-cache policy nfs-common`

새 NFS 볼륨이 필요할 때마다 Todd는 다음 명령을 실행하여 새 NFS 볼륨을 작성합니다.

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### 이미지 보안 준비

{{site.data.keyword.icpfull_notm}} V3.1에서, 이미지를 {{site.data.keyword.icpfull_notm}} 인스턴스로 가져오기 전에 이미지 정책을 제자리에 배치해야 보안이 강화됩니다. 보안을 강화하려면 IBM 이미지가 상주한 위치 *dockerhub/ibmcom* 및 Docker 저장소에 대한 이미지 정책을 추가해야 합니다.

기본적으로 ibmcloud-default-cluster-image-policy가 제공되고 Docker.io/ibmcom/\*의 IBM 이미지를 다루지만 Db2 및 기타 IBM 컨텐츠가 Docker 저장소에 있기 때문에 Docker 저장소 *docker.io/store/ibmcorp/*에 대한 다른 이미지 정책이 필요합니다.

또한 일부 컨텐츠에서는 팟(Pod)에 대한 특정 액세스를 허용하도록 설정된 팟(Pod) 보안 정책이 필요합니다. 예를 들면, Db2는 'default' 이외의 네임스페이스에서 Db2를 실행하려는 클라이언트에 대한 정책이 필요합니다.

자세한 내용은 [IBM Knowledge
Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html)를 참조하십시오.

## Transformation Advisor 및 Microclimate 배치

Todd의 환경에서 {{site.data.keyword.icpfull_notm}}가 실행되면 Microclimate와 함께 Transformation Advisor를 설치합니다. Todd는 [카탈로그](https://www.ibm.com/cloud/private/developer)를 열고 사용 가능한 모든 컨텐츠를 봅니다.

Todd는 Transformation Advisor와 Microclimate를 찾고, helm 설치 차트를 클릭하면 제공되는 readme 파일 지시사항을 통해 이를 설치합니다.

### Transformation Advisor 실행

Transformation Advisor를 실행하기 위해 WebSphere에서 Stock Trader를 실행하는 VM에 데이터 콜렉터를 추가한 Jane이 [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) 사용자 인터페이스를 열어 결과를 확인합니다.

Jane이 Stock Trader를 추가했고 Liberty에서 각 war 파일을 실행하기 위한 권장 사항을 확인하며 대부분의 마이그레이션은 하나의 적당한 마이그레이션으로 간단하게 수행될 것입니다. Jane은 Migration Details를 클릭하고 마이그레이션을 완료하는 데 사용할 수 있는 배치 파일을 Transformation Advisor에서 제공하는지 확인합니다. Jane이 Transformation Advisor에 2진 파일을 업로드하면 Microclimate에서 제공한 API를 사용하여 Liberty 컨테이너를 배치합니다.

결과적으로 Stock Trader 레이아웃 옵션은 다음과 같습니다.
* 단일 Liberty 컨테이너 - Jane이 Liberty 런타임을 배치하고 Stock Trader 앱을 해당 단일 컨테이너에 추가했습니다.
* 다중 Liberty 컨테이너 - Transformation Advisor에서 Stock Trader에 권장하는 대로 각.war 파일에 컨테이너가 하나씩 있습니다.

Todd는 변환 단계 중에 데이터 소스를 변경하지 않았습니다. Transformation Advisor는 WebSphere Application Server Network Deployment 데이터 소스 구성을 가져와서 Liberty 컨테이너의 server.xml에 추가합니다.
{:important}

### 관련 링크

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](../vcs/vcs-hybridity-intro.html)

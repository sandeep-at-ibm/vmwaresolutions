---

copyright:

  years:  2016, 2019

lastupdated: "2018-01-14"

---

# 백업, 재해 복구 및 확장성

## 백업 및 DR

### VMware vCenter Server on IBM Cloud 백업

{{site.data.keyword.vmwaresolutions_full}}의 일부로, Veeam 백업 소프트웨어는 VMware 클러스터 외부에서 {{site.data.keyword.cloud_notm}} Endurance Storage를 사용하는 {{site.data.keyword.cloud_notm}} VSI(Virtual Server Instance)에 선택적으로 배치됩니다. 이 소프트웨어의 목적은 이 솔루션의 관리 컴포넌트를 백업하는 것입니다.

### NSX 백업

모든 NSX 컴포넌트의 적절한 백업은 장애가 발생하는 경우 시스템을 해당 작업 상태로 복원하는 데 매우 중요합니다. NSX 가상 머신(VM)을 백업하는 것만으로는 충분하지 않습니다. 대신 적절한 백업을 위해서는 NSX Manager 내의 NSX 백업 기능을 사용해야 합니다. FTP 또는 SFTP 서버가 NSX 백업 데이터의 저장소에 대해 지정되어야 합니다.
NSX 관리자 백업에는 제어기, 엔티티의 논리적 전환 및 라우팅, 보안, 방화벽 규칙 및 NSX Manager 사용자 인터페이스 또는 API 내에서 구성하는 모든 것을 포함하여 모든 NSX 구성이 포함됩니다. vCenter 데이터베이스와 관련 요소(예: 가상 스위치)는 별도로 백업해야 합니다. NSX 구성은 vCenter 백업과 함께 백업해야 합니다.

### IBM Cloud Private에 대한 백업 및 DR

{{site.data.keyword.icpfull_notm}} 배치에 대한 백업은 장애가 발생하는 경우 시스템을 해당 작업 상태로 복원하는 데 매우 중요합니다. 일반적인 VM 백업 외에도 모든 {{site.data.keyword.icpfull_notm}} 마스터 노드는 etcd를 실행합니다. etcd 문서에서는 복원하는 데 일반 VM 백업을 사용하지 않도록 명확히 명시되어 있습니다.

플랫폼 레벨의 {{site.data.keyword.icpfull_notm}}는 다음 컴포넌트를 백업해야 합니다.
- **Etcd** Kubernetes 리소스 및 Calico 상태 정보를 저장하는 데 사용됩니다.
- **Docker 레지스트리** 이미지 저장소에 컨테이너 이미지 파일을 저장하는 데 사용되는 개인용 이미지 레지스트리입니다.
- **MongoDB** 미터링 서비스, Helm 저장소 서버, Helm API 서버, LDAP 구성, 테넌트(네임스페이스) 및 팀/사용자/사용자 그룹 역할 구성에서 사용하는 데이터베이스입니다.
- **MariaDB** OIDC에서 사용하는 데이터베이스입니다.
- **Elasticsearch** 시스템 및 애플리케이션 로그를 저장합니다.
- **Prometheus** 모니터링에 대한 데이터를 저장합니다.
- **지속적 스토리지** {{site.data.keyword.icpfull_notm}} 또는 Kubernetes 지속적 볼륨과 스토리지 제공자를 사용하는 관리 서비스에 사용됩니다. 스토리지 제공자가 제공하는 백업 또는 복원 기술을 사용할 수 있습니다. 유사한 프로세스를 사용자의 애플리케이션에도 확장할 수 있습니다.

### CAM에 대한 백업 및 DR

CAM 배치에 대한 백업은 장애가 발생하는 경우 시스템을 해당 작업 상태로 복원하는 데 매우 중요합니다. CAM 백업은 고객이 다음 컴포넌트를 백업해야 합니다.
- **Mongo 데이터베이스**는 기본 CAM 데이터베이스입니다.
- **Maria 데이터베이스**는 CAM 블루프린트 디자이너에서 사용되는 데이터베이스입니다.
- **NFS/GlusterFS**에서는 CAM 데이터가 4개의 지속적 볼륨에 상주합니다.

### IBM Cloud Kubernetes Service에 대한 백업 및 DR

etcd 데이터베이스의 백업은 관리 서비스의 일부로 고객에게 제공되며 애플리케이션 데이터는 자체적으로 백업해야 합니다.

## 확장성

### VCS 확장성

초기 호스트를 배치하고 나면 사용자는 {{site.data.keyword.cloud_notm}} for VMware 포털 내에서 컴퓨팅 기능을 확장할 수 있습니다.

환경에서 이 확장은 세 가지 경로 중 하나를 따릅니다.
- 별도의 vCenter Server에서 관리하는 새 사이트의 추가
- 새 클러스터의 추가
- 기존 클러스터에 새 호스트 추가

#### 다중 사이트 배치

VMware on {{site.data.keyword.cloud_notm}}는 IBM Cloud의 전세계 데이터 센터 및 통합 네트워크 백본을 사용하여 다양한 교차 지역의 유스 케이스를 배치하고 처음부터 이러한 인프라를 빌드하는 데 걸리는 시간 내에 작동되도록 할 수 있습니다.

#### 새 클러스터로 확장

사용자는 콘솔에서 새 클러스터를 작성하고, 호스트를 주문하여 컴퓨팅 용량을 확장할 수 있으며, 새 호스트는 새 클러스터에 자동으로 추가됩니다. 이 옵션은 환경에 별도의 클러스터를 작성하며, 사용자에게 애플리케이션 워크로드에서 관리 워크로드를 물리적 및 논리적으로 구분하는 기능, 다른 특성(예: Microsoft SQL 데이터베이스 클러스터)에 따라 워크로드를 구분하는 기능 및 고가용성 토폴로지에 애플리케이션을 배치하는 기능을 제공합니다.

#### 기존 클러스터 확장

사용자는 콘솔 내에서 호스트를 주문하여 기존 클러스터를 확장할 수 있으며 새 호스트는 자동으로 클러스터에 추가됩니다. 예약 요구사항에 따라 클러스터에 대한 HA 예약 정책을 조정해야 할 수 있습니다.

### IBM Cloud Private 확장성

온프레미스 또는 클라우드 위치에서 사용 가능한 컴퓨팅 용량에 따라, 사용자는 처음에 배치된 부트 노드에서 노드 아키텍처를 확장할 수 있습니다.

환경에서 확장은 다음을 따릅니다.
- {{site.data.keyword.icpfull_notm}} 작업자 노드 확장
- {{site.data.keyword.containerlong_notm}} 오퍼링 확장 및 사용

#### IBM Cloud Private 확장

{{site.data.keyword.icpfull_notm}} 작업자의 VM 노드는 컴퓨팅 또는 애플리케이션을 확장하도록 스케일링됩니다.
- 고객은 {{site.data.keyword.icpfull_notm}}가 배치되는 동일한 VXLAN에 새로운 VM을 프로비저닝합니다.
- 고객은 새 VM을 프로비저닝한 후 부트 노드에 로그인하여 새 노드를 클러스터로 가져오는 명령을 실행하여 작업자 노드를 확장할 수 있습니다.
- CAM을 사용하여 VM 프로비저닝을 자동화하고 {{site.data.keyword.icpfull_notm}} 클러스터에 추가하는 명령을 실행하도록 자동화할 수 있습니다.

###  IBM Cloud Kubernetes Service 확장

사용자는 {{site.data.keyword.cloud_notm}} Portal을 통해 {{site.data.keyword.containerlong_notm}} 환경을 프로비저닝하여 컨테이너 환경을 확장하거나 사용할 수 있습니다. 

애플리케이션을 {{site.data.keyword.containerlong_notm}}에 배치하려면 다음을 수행하십시오. 
- {{site.data.keyword.containerlong_notm}} 연결 또는 서비스는 CAM에서 개발되고 {{site.data.keyword.icpfull_notm}} 카탈로그에 공개됩니다.
- 다중 클라우드 관리자의 향후 {{site.data.keyword.containerlong_notm}} 인스턴스 관리 개선사항
- Helm 명령행 인터페이스
- 다중 구역 클러스터를 사용하여 고가용성을 늘리십시오.

### 관련 링크

* [클러스터 노드 추가 또는 제거](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [기존 작업자 풀을 크기 조정하여 작업자 노드 추가](../../../../containers/cs_clusters.html#resize_pool)
* [{{site.data.keyword.cloud_notm}} Private 백업 및 복원 방법](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}} 백업 GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](../vcs/vcs-hybridity-intro.html)

---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM 사용자 ID 및 vCenter Server 인스턴스의 배치 히스토리 메시지
{: #ibm_use}

{{site.data.keyword.cloud}}는 자동화 및 오퍼레이션 로깅을 위해 사용자의 계정에 대한 액세스 권한이 필요합니다. 

## 사용자 ID
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}}는 오퍼레이션(예: 호스트, 클러스터 또는 스토리지를 VMware 인스턴스에 추가)을 수행할 때 {{site.data.keyword.cloud_notm}} 자동화에 사용될 사용자 계정 내에 있는 일련의 사용자를 관리합니다. {{site.data.keyword.cloud_notm}} 자동화 사용자 ID에 대한 다음 절을 검토하십시오. 

IBM 사용자 ID가 삭제되거나 사용 안함으로 설정되는 경우 또는 비밀번호가 변경되는 경우에는 VMware 인스턴스 오퍼레이션이 실패합니다.
{:important}

### vCenter및 Platform Services Controller 사용자 ID
{: #ibm_use-user-ids-vcenter-psc}

V2.5부터 {{site.data.keyword.vmwaresolutions_short}}는 다음 사용자 ID를 사용하여 기본적으로 임베드된 ID 소스를 vCenter에 추가합니다. 

표 1. vCenter및 Platform Services Controller 사용자 ID

| 사용자   |사용자 ID      | 메소드 |설명 |
|:---------|:-------------|:-------|:------------|
|IBM      | root         | SSH    | VMware 구성(예: VMware 고가용성 설정 및 분배 스위치 작성)에 사용됩니다. 기본 및 보조 vCenter Server 인스턴스를 페어링하는 데 사후 배치가 사용됩니다. |
|고객 | customerroot | SSH    | 고객용으로만 작성됩니다. |
|IBM      | automation@``root_domain``<br/>(Active Directory 사용자) | HTTP | 호스트 및 클러스터를 추가하고 제거하며, 추가 서비스로 가상 머신을 배치하고 구성하는 데 사후 배치가 사용됩니다. |
|고객 | Administrator@vsphere.local | HTTP | 고객용으로만 작성됩니다. |

HTTP는 vCenter 설정 및 구성과 VMware 오퍼레이션(예: vCenter의 리소스 관리를 위한 호스트, 클러스터 또는 스토리지 추가)에 사용됩니다.
{:note}

### NSX Manager 사용자 ID
{: #ibm_use-user-ids-nsx-mgr}

NSX Manager 사용자 ID는 서비스에 대한 ESG 규칙을 추가하는 데 사용됩니다. 

표 2. NSX Manager 사용자 ID

| 사용자   |사용자 ID      |설명 |
|:---------|:-------------|:------------|
|IBM      | automation@``root_domain``<br/>(Active Directory 사용자) | NSX VTEP IP 주소를 관리하고, 호스트 및 클러스터 구성을 관리하는 데 호스트 및 클러스터를 추가하고 제거하며, 라이센스 부여, 활성화 또는 사용량 보고를 위해 공용 네트워크 액세스 권한이 필요한 추가 서비스로 ESG 구성을 관리할 때 NSX VTEP IP 주소를 관리하고 호스트 및 클러스터 구성을 관리하는 데 사후 배치가 사용됩니다. |
|고객 |관리자        | 고객용으로만 작성됩니다. |

### ESXi 호스트 사용자 ID
{: #ibm_use-user-ids-esxi}

ESXi 호스트 사용자 ID는 스토리지를 추가하고, 패치하고, vSAN 클러스터를 구성하는 데 사용되며 모든 서버 유효성 검증 코드를 실행합니다. 

표 3. ESXi 호스트 사용자 ID

| 사용자   |사용자 ID      |설명 |
|:---------|:-------------|:------------|
|IBM      | ic4vroot     | 추가 NFS 스토리지를 추가하고 해당 스토리지에 대한 라우트를 구성하는 데 사후 배치가 사용됩니다. |
|고객 | root         | 고객용으로만 작성됩니다. |

### Microsoft Active Directory 사용자 ID
{: #ibm_use-user-ids-ad}

Active Directory 사용자 ID는 DNS 항목을 설정하는 데 사용됩니다. 

표 4. Active Directory 사용자 ID

| 사용자   |사용자 ID       |설명 |
|:---------|:------------- |:------------|
|IBM      | 자동화    | 호스트를 추가하고, 가상 머신을 서비스에 추가하고, Active Directory 및 DNS 항목을 설정하는 데 사용됩니다. |
|고객 | 관리자 | 고객용으로만 작성됩니다. |

## 인스턴스 히스토리 메시지
{: #ibm_use-msgs}

{{site.data.keyword.cloud_notm}}가 VMware 인스턴스에 대해 수행하는 모든 오퍼레이션이 인스턴스 히스토리에 로깅됩니다. 참조로 인스턴스 히스토리를 사용하여 이 오퍼레이션을 검토할 수 있습니다. 인스턴스 히스토리 검토에 대한 자세한 정보는 [vCenter Server 인스턴스에 대한 배치 히스토리를 보는 프로시저](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history)를 참조하십시오. 

다음 절에서는 인스턴스 히스토리에 발행될 수 있는 모든 메시지를 제공합니다. 

### 일반 인스턴스 히스토리 메시지
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}}는 일반 조치에 대한 다음 메시지를 발행합니다. 

* ``Starting to create the instance user and required services...``
* ``The instance user and required services creation is complete.``
* ``Ordering the vCenter Server license...``
* ``Ordering VMware licenses...``
* ``Completed the order for VMware licenses.``
* ``Ordering <quantity> upcharges...``
* ``Starting the <environment> installation and configuration...``
* ``The <environment> installation and configuration is complete.``
* ``Starting VMware components...``
* ``Starting to deploy the instance...``
* ``The <instance_name> instance is ready to use.``
* ``Starting upgrade to <version>...``
* ``The upgrade to <version> is complete.``
* ``VMware component upgrade is complete.``
* ``Starting the <instance_name> instance deletion...``
* ``The <instance_name> instance is successfully deleted.``
* ``The secure wipe of the instance is complete.``
* ``Cancelling the vCenter license...``
* ``Cancelling the instance user and required services...``
* ``Cancelling <environment> upcharges...``
* ``VMware license cancellation in progress...``
* ``VMware license cancellation is complete.``
* ``The SoftLayer order failed or timed out.``

### 클러스터 히스토리 메시지
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}}는 vCenter Server 클러스터에 대한 다음 메시지를 발행합니다. 

* ``Starting the cluster configuration...``
* ``Starting the cluster configuration for <cluster_name>...``
* ``The cluster configuration is complete.``
* ``The <cluster_name> cluster is ready to use.``
* ``Adding the new cluster into vCenter...``
* ``The new cluster is added to vCenter.``
* ``Starting the cluster deletion for <cluster_name>...``
* ``Deleting the <cluster_name> cluster from vCenter...``
* ``The <cluster_name> cluster is deleted from vCenter.``
* ``The <cluster_name> cluster is deleted.``

### 가상 서버 인스턴스 히스토리 메시지
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}}는 VSI(Virtual Server Instance)에 대한 다음 메시지를 발행합니다. 

* ``Ordering a new virtual server instance for the IBM CloudDriver...``
* ``The <ip_address> IBM CloudDriver virtual server instance is provisioned.``
* ``Cancelling the <ip_address> IBM CloudDriver virtual server instance...``
* ``Starting the order for the Microsoft Windows virtual server instance for Microsoft Active Directory/DNS...``
* ``Verifying the Microsoft Windows virtual server instance order for Active Directory/DNS...``
* ``The Microsoft Windows virtual server instance for Active Directory/DNS is ready.``
* ``Virtual server instance cancellation in progress...``
* ``Cancelling associated virtual server instances...``
* ``Virtual server instance cancellation is complete.``

### IBM CloudDriver 히스토리 메시지
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}}는 IBM CloudDriver에 대한 다음 메시지를 발행합니다. 

* ``Preparing the IBM CloudDriver...``
* ``The IBM CloudDriver is ready.``
* ``The <ip_address> IBM CloudDriver is ready to use.``
* ``Checking the IBM CloudDriver status...``
* ``Reusing the existing <ip_address> IBM CloudDriver...``
* ``Reusing the existing IBM CloudDriver (In Provisioning)...``
* ``Releasing the IBM CloudDriver...``
* ``Releasing the <ip_address> IBM CloudDriver...``
* ``Starting the IBM CloudDriver deletion...``
* ``Completed the IBM CloudDriver deletion.``

### ESXi 서버 히스토리 메시지
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}}는 ESXi 서버에 대한 다음 메시지를 발행합니다. 

* ``Starting the order for <quantity> ESXi servers...``
* ``Verifying the ESXi server order...``
* ``The ESXi servers with the <ip_addresses> Private IP address are ready.``
* ``All ESXi servers are reclaimed.``
* ``Adding ESXi servers to the vCenter Server instance...``
* ``The ESXi servers are successfully updated.``
* ``Starting to order ESXi servers for cluster...``
* ``Starting to order <quantity> ESXi servers for the <Cluster Name> cluster...``
* ``The ESXi servers for the cluster are ready.``
* ``ESXi servers with the <ip_addresses> Private IP address are ready for the cluster.``
* ``The ESXi server is ready.``
* ``The ESXi server configuration is complete.``
* ``The ESXi server is successfully added with the property.``
* ``All requests for adding ESXi servers are successfully completed.``
* ``Adding the ESXi server...``
* ``Ordering a Bare Metal Server for the ESXi server...``
* ``New ESXi servers are added to vCenter.``
* ``Starting to add services to the new ESXi servers...``
* ``The selected ESXi servers are successfully cancelled.``
* ``New ESXi servers are provisioned.``
* ``New ESXi servers are verified and ready.``
* ``Starting to order <quantity> new ESXi servers for the <cluster_name> cluster...``
* ``The selected ESXi servers are removed from vCenter Server.``
* ``Starting to remove services to remove ESXi servers...``
* ``Verifying ESXi servers for the <cluster_name> cluster...``
* ``The new cluster ESXi servers successfully passed verification.``
* ``Verifying new ESXi server order...``
* ``The verification of the ESXi servers order failed.``
* ``Splitting batch add ESXi servers request.``
* ``Successfully completed all requests for removing ESXi servers.``
* ``The host is successfully added.``
* ``The host(s) are successfully removed.``
* ``Bare Metal Server cancellation in progress...``
* ``Bare Metal Server cancellation is complete.``
* ``Removing ESXi servers from the vCenter Server instance...``
* ``Removing the ESXi server.``
* ``Removing the <server_id> ESXi server.``
* ``Removing selected ESXi servers from vCenter Server...``
* ``Cancelling the ESXi servers...``
* ``Cancelling the selected ESXi servers...``

### IBM CloudBuilder 히스토리 메시지
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}}는 IBM CloudBuilder에 대한 다음 메시지를 발행합니다. 

* ``Verifying the IBM CloudBuilder Virtual Server Instance order...``
* ``Starting the order for the IBM CloudBuilder Virtual Server Instance...``
* ``The IBM CloudBuilder Virtual Server Instance is ready.``
* ``The IBM CloudBuilder is ready for service.``
* ``Dismissing the IBM CloudBuilder Virtual Server Instance...``

### 스토리지 히스토리 메시지
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}}는 스토리지 설정에 대한 다음 메시지를 발행합니다. 

* ``Ordering the vSAN license...``
* ``Cancelling the vSAN license...``
* ``The VSAN license cancellation is complete.``
* ``Ordering <quantity> NFS storage(s) for the <cluster_name> cluster.``
* ``The new NFS storage is added and ready to use.``
* ``Cancelling Management NFS share storage...``
* ``The selected NFS storage is deleted.``
* ``Starting the order for Endurance Storage...``
* ``Cancelling Endurance Storage...``

### 네트워크 히스토리 메시지
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}}는 네트워크 설정에 대한 다음 메시지를 발행합니다. 

* ``Starting the public VLAN order...``
* ``Successfully completed the VLAN configuration.``
* ``Ordering additional private VLAN...``
* ``Additional private VLAN is provisioned.``
* ``An additional private VLAN Virtual Server Instance is provisioned.``
* ``Trunking additional private VLAN to Bare Metal Servers...``
* ``Successfully trunked the additional private VLAN to Bare Metal Servers.``
* ``Cancelling the additional private VLAN Virtual Server Instance...``
* ``Cancelling VLANs...``
* ``VLAN cancellation in progress...``
* ``VLAN cancellation is complete.`
* ``Ordering a two socket <type> NSX license...``
* ``NSX configuration for the new cluster is complete.``
* ``Cancelling  the two socket NSX license...``
* ``The NSX license has been successfully cancelled.``
* ``Starting the order for subnets...``
* ``The subnet is ready.``
* ``The portable private subnet is ready.``
* ``Granting new subnet access to NFS storage...``
* ``Cancelling subnets...``
* ``Subnet cancellation in progress...``
* ``Cancelling the customer portable private subnet...``
* ``Canceling the customer portable public subnet...``
* ``Cancelling the Endurance Storage private subnet...``
* ``Cancelling the portable public subnet...``
* ``The portable public subnet is ready.``
* ``Starting the portable public subnet order...``
* ``Subnet cancellation is complete.``
* ``Cancelling network storage...``

### 서비스 히스토리 메시지
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}}는 서비스에 대한 다음 메시지를 발행합니다. 

* ``Starting the management services setup...``
* ``Ordering service entries...``
* ``Completed the order for service entries.``
* ``IBM operation services are running.``
* ``Enabling the default services...``
* ``The default services are successfully enabled.``
* ``Service entry cancellation in progress...``
* ``Service entry cancellation is complete.``

### vCenter Server with Hybridity Bundle 히스토리 메시지
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}}는 vCenter Server with Hybridity Bundle 인스턴스에 대한 다음 메시지를 발행합니다. 

* ``Ordering vCenter Server with Hybridity Bundle licenses...``
* ``Starting the vCenter Server with Hybridity Bundle conversion...``
* ``The vCenter Server with Hybridity Bundle conversion is complete.``
* ``Removing the vCenter Server with Hybridity Bundle...``
* ``The vCenter Server with Hybridity Bundle is successfully removed.``
* ``Cancelling the vCenter Server with Hybridity Bundle conversion...``

### Cloud Foundation 히스토리 메시지
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}}는 Cloud Foundation 인스턴스에 대한 다음 메시지를 발행합니다. 

* ``Starting the Cloud Foundation instance order...``
* ``The Cloud Foundation order has been received.``
* ``Processing the Cloud Foundation order...``
* ``Ordering a virtual server to use for the Cloud Foundation configuration...``
* ``Completed the order of the virtual server to use for the Cloud Foundation configuration.``
* ``Verified the order of the virtual server to use for the Cloud Foundation configuration.``
* ``Ordering Bare Metal Servers to use for the Cloud Foundation configuration...``
* ``Completed the order of Bare Metal Servers to use for the Cloud Foundation configuration.``
* ``Configuring Cloud Foundation networking...``
* ``Completed the configuration of Cloud Foundation networking.``
* ``Ordering Cloud Foundation subnets...``
* ``Completed order of the Cloud Foundation subnets``
* ``Configuring the Cloud Foundation instance...``
* ``Customizing and optimizing the Cloud Foundation instance components...``
* ``The Cloud Foundation cleanup in progress...``
* ``The Cloud Foundation cleanup is complete.``
* ``The Cloud Foundation instance is ready to use.``
* ``Customizing and optimizing the Cloud Foundation instance...``
* ``The Cloud Foundation instance configuration is complete.``
* ``Customizing and optimizing Cloud Foundation instance is complete.``
* ``The Cloud Foundation components order is complete.``
* ``The Cloud Foundation instance deletion is complete.``
* ``Deletion of the Cloud Foundation instance is complete.``

### 오류 메시지
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}}는 다음 인스턴스 히스토리 오류 메시지를 발행합니다. 

* ``Error ordering a Virtual Server used for the Cloud Foundation configuration. Open a service ticket for assistance.``
* ``Error: SoftLayer failed to provision a virtual server to use for the Cloud Foundation configuration. Open a service ticket for assistance.``
* ``Error ordering Bare Metal Servers used for the Cloud Foundation configuration. Open a service ticket for assistance.``
* ``Error ordering VLANs to use for the Cloud Foundation configuration. Open a service ticket for assistance.``
* ``Error configuring Cloud Foundation networking. Open a service ticket for assistance.``
* ``Error ordering Cloud Foundation subnets. Open a service ticket for assistance.``
* ``Error creating administration services for the Cloud Foundation instance. Open a service ticket for assistance.``
* ``Error ordering VMware licenses. Open a service ticket for assistance.``
* ``Error ordering subnets. Open a service ticket for assistance.``
* ``Error configuring the Cloud Foundation instance. Open a service ticket for assistance.``
* ``Error customizing and optimizing the Cloud Foundation instance. Open a service ticket for assistance.``
* ``Error: The SoftLayer API key is not valid. Open a service ticket for assistance.``
* ``Error: The SoftLayer data center is not valid. Open a service ticket for assistance.``
* ``Error using a shared image in the provided SoftLayer account. Open a service ticket for assistance.``
* ``Error ordering service entries. Open a service ticket for assistance.``
* ``Error ordering subnets. Open a service ticket for assistance.``
* ``Error ordering licenses. Open a service ticket for assistance.``
* ``Error ordering services. Open a service ticket for assistance.``


## 관련 링크
{: #ibm_use-related}

* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

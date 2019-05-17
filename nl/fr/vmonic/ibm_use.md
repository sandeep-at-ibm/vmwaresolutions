---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# ID utilisateur IBM et messages d'historique de déploiement pour les instances vCenter Server 
{: #ibm_use}

{{site.data.keyword.cloud}} nécessite un accès à votre compte pour l'automatisation et la journalisation des opérations.

## ID utilisateur
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} maintient un ensemble d'utilisateurs dans votre compte à utiliser par l'automatisation {{site.data.keyword.cloud_notm}} lorsque vous effectuez des opérations telles que l'ajout de serveurs, de clusters ou le stockage à votre instance VMware. Passez en revue les sections suivantes relatives aux ID utilisateur utilisés par l'automatisation {{site.data.keyword.cloud_notm}}.

Les opérations des instances VMware échouent si les ID utilisateur IBM sont supprimés, désactivés ou si leurs mots de passe sont modifiés.
{:important}

### ID utilisateur du vCenter et de PSC (Platform Services Controller)
{: #ibm_use-user-ids-vcenter-psc}

A partir de la version 2.5, {{site.data.keyword.vmwaresolutions_short}} utilise les ID utilisateur suivants pour ajouter une source d'identité, intégréé par défaut, dans vCenter.

Tableau 1. ID utilisateur de vCenter et PSC (Platform Services Controller)

| Utilisateur     | ID utilisateur      | Méthode | Description |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Utilisé pour la configuration de VMware, par exemple pour la configuration de la haute disponibilité dans VMware et la création de commutateurs distribués. Utilisé après le déploiement pour coupler les instances principales et secondaires de vCenter Server. |
| Client | customerroot | SSH    | Créé uniquement pour l'utilisation par les clients. |
| IBM      | automation@``root_domain``<br/>(utilisateur Active Directory) | HTTP | Utilisé après le déploiement pour ajouter et supprimer des hôtes et des clusters et pour déployer et configurer des machines virtuelles pour les services complémentaires. |
| Client | Administrator@vsphere.local | HTTP | Créé uniquement pour l'utilisation par les clients. |

HTTP est utilisé pour l'installation et la configuration de vCenter, ainsi que pour les opérations VMware telles que l'ajout d'hôtes, de clusters ou de stockage pour la gestion des ressources de vCenter.
{:note}

### ID utilisateur de NSX Manager 
{: #ibm_use-user-ids-nsx-mgr}

Les ID utilisateur de NSX Manager sont utilisés pour ajouter des règles ESG au service.

Tableau 2. ID utilisateur de NSX Manager

| Utilisateur     | ID utilisateur      | Description |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(utilisateur Active Directory) | Utilisé après le déploiement pour gérer les adresses IP NSX VTEP, gérer la configuration des hôtes et des clusters lors de l'ajout et de la suppression d'hôtes et de clusters, et gérer la configuration ESG pour les services complémentaires qui nécessitent un accès au réseau public pour l'octroi de licence, l'activation ou les rapports d'utilisation. |
| Client | Administrateur        | Créé uniquement pour l'utilisation par les clients. |

### ID utilisateur des hôtes ESXi
{: #ibm_use-user-ids-esxi}

Les ID utilisateur des hôtes ESXi sont utilisés pour ajouter du stockage, pour effectuer des corrections, pour configurer les clusters vSAN et pour exécuter tous les codes de validation de serveur.

Tableau 3. ID utilisateur des hôtes ESXi

| Utilisateur     | ID utilisateur      | Description |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Utilisé après le déploiement pour ajouter un stockage NFS additionnel et configurer des routes pour ce stockage. |
| Client | root         | Créé uniquement pour l'utilisation par les clients. |

### ID utilisateur de Microsoft Active Directory
{: #ibm_use-user-ids-ad}

Les ID utilisateur d'Active Directory sont utilisés pour configurer des entrées DNS.

Table 4. ID utilisateur d'Active Directory

| Utilisateur     | ID utilisateur       | Description |
|:---------|:------------- |:------------|
| IBM      | automation    | Permet d'ajouter un hôte, d'ajouter une machine virtuelle pour le service et pour configurer Active Directory et les entrées DNS. |
| Client | Administrateur | Créé uniquement pour l'utilisation par les clients. |

## Messages d'historique des instances
{: #ibm_use-msgs}

Toutes les opérations qu'{{site.data.keyword.cloud_notm}} effectue pour votre instance VMware sont enregistrées dans l'historique des instances. Vous pouvez utiliser l'historique des instances comme référence pour passer en revue ces opérations. Pour plus d'informations sur la vérification de votre historique des instances, voir [Procédure d'affichage de l'historique de déploiement pour les instances vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

Les sections suivantes fournissent tous les messages possibles qui peuvent être envoyés à votre historique des instances.

### Messages généraux de l'historique des instances
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les actions générales :

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

### Messages d'historique des clusters
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les clusters vCenter Server :

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

### Messages d'historique des instances de serveur virtuel
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les instances de serveur virtuel (VSI) :

* ``Ordering a new virtual server instance for the IBM CloudDriver...``
* ``The <ip_address> IBM CloudDriver virtual server instance is provisioned.``
* ``Cancelling the <ip_address> IBM CloudDriver virtual server instance...``
* ``Starting the order for the Microsoft Windows virtual server instance for Microsoft Active Directory/DNS...``
* ``Verifying the Microsoft Windows virtual server instance order for Active Directory/DNS...``
* ``The Microsoft Windows virtual server instance for Active Directory/DNS is ready.``
* ``Virtual server instance cancellation in progress...``
* ``Cancelling associated virtual server instances...``
* ``Virtual server instance cancellation is complete.``

### Messages d'historique d'IBM CloudDriver
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour IBM CloudDriver :

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

### Messages d'historique du serveur ESXi
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les serveurs ESXi:

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

### Messages d'historique d'IBM CloudBuilder 
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour IBM CloudBuilder :

* ``Verifying the IBM CloudBuilder Virtual Server Instance order...``
* ``Starting the order for the IBM CloudBuilder Virtual Server Instance...``
* ``The IBM CloudBuilder Virtual Server Instance is ready.``
* ``The IBM CloudBuilder is ready for service.``
* ``Dismissing the IBM CloudBuilder Virtual Server Instance...``

### Messages d'historique de stockage
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les paramètres de stockage :

* ``Ordering the vSAN license...``
* ``Cancelling the vSAN license...``
* ``The VSAN license cancellation is complete.``
* ``Ordering <quantity> NFS storage(s) for the <cluster_name> cluster.``
* ``The new NFS storage is added and ready to use.``
* ``Cancelling Management NFS share storage...``
* ``The selected NFS storage is deleted.``
* ``Starting the order for Endurance Storage...``
* ``Cancelling Endurance Storage...``

### Messages d'historique du réseau 
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les paramètres de réseau :

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

### Messages d'historique de service
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les services :

* ``Starting the management services setup...``
* ``Ordering service entries...``
* ``Completed the order for service entries.``
* ``IBM operation services are running.``
* ``Enabling the default services...``
* ``The default services are successfully enabled.``
* ``Service entry cancellation in progress...``
* ``Service entry cancellation is complete.``

### Messages d'historique de vCenter Server with Hybridity Bundle
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les instances vCenter Server with Hybridity Bundle :

* ``Ordering vCenter Server with Hybridity Bundle licenses...``
* ``Starting the vCenter Server with Hybridity Bundle conversion...``
* ``The vCenter Server with Hybridity Bundle conversion is complete.``
* ``Removing the vCenter Server with Hybridity Bundle...``
* ``The vCenter Server with Hybridity Bundle is successfully removed.``
* ``Cancelling the vCenter Server with Hybridity Bundle conversion...``

### Messages d'historique de Cloud Foundation
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} émet les messages suivants pour les instances Cloud Foundation :

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

### Messages d'erreur
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} émet les messages d'erreur d'historique d'instance suivants :

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


## Liens connexes
{: #ibm_use-related}

* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

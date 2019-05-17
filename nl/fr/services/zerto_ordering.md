---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de Zerto on IBM Cloud
{: #zerto_ordering}

Vous pouvez commander le service Zerto on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou en ajoutant le service à votre instance existante.

## Commande de Zerto on IBM Cloud pour une nouvelle instance
{: #zerto_ordering-new}

Vous pouvez commander une nouvelle instance avec Zerto on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **Zerto on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **Zerto on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de Zerto on IBM Cloud pour une instance existante
{: #zerto_ordering-existing}

Vous pouvez ajouter le service Zerto on {{site.data.keyword.cloud_notm}} à une instance existante en utilisant l'une des méthodes suivantes :
* Dans la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **Zerto on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

Si vous ajoutez Zerto for {{site.data.keyword.cloud_notm}} à une instance vCenter Server doté d'un serveur ESXi qui est en mode maintenance, vous devez utiliser la console Zerto Virtual Manager (ZVM) et l'adresse IP préremplie de Zerto Virtual Replication Appliance (VRA) pour déployer manuellement la machine virtuelle VRA.
{:note}

## Commande de Zerto on IBM Cloud pour des instances uniquement privées
{: #zerto_ordering-private-only}

Si vous souhaitez ajouter Zerto on {{site.data.keyword.cloud_notm}} à une instance uniquement privée, tenez compte de ceci :
* Vous êtes responsable de la configuration de votre propre serveur proxy pour vous connecter à Internet. Pour plus d'informations, voir [Connectivité au réseau public](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Vous devez également configurer la fonction Call Home pour Zerto. Pour plus d'informations sur la fonction Call Home de Zerto, voir [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Liens connexes
{: #zerto_ordering-related}

* [Présentation de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Demande de services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

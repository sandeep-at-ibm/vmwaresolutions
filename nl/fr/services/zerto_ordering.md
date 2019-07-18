---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de Zerto on IBM Cloud
{: #zerto_ordering}

Vous pouvez commander le service Zerto on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou en ajoutant le service à votre instance existante.

## Facturation pour la réplication Zerto
{: #zerto_ordering-billing}

Les machines virtuelles répliquées à l'aide de Zerto sont mesurées par Zerto et {{site.data.keyword.cloud_notm}}. Votre facture pour cette utilisation est facturée via un compte facturable {{site.data.keyword.cloud_notm}} au lieu d'un compte d'infrastructure {{site.data.keyword.cloud_notm}}.

Avant de commander Zerto sur {{site.data.keyword.cloud_notm}}, assurez-vous que votre compte {{site.data.keyword.cloud_notm}} est un compte facturable et qu'il est lié au même compte d'infrastructure {{site.data.keyword.cloud_notm}} sur lequel votre instance est déployée.

Si vous disposez d'une installation Zerto sur {{site.data.keyword.cloud_notm}} à partir de la version 3.0 ou antérieure, vos coûts de réplication de VM sont toujours facturés à l'aide de la facturation d'infrastructure {{site.data.keyword.cloud_notm}}. Si vos paramètres de compte et de facturation respectent les exigences répertoriées précédemment, vous pouvez convertir votre méthode de facturation Zerto en facturable.

Sur la console {{site.data.keyword.vmwaresolutions_short}}, vous êtes invité à convertir le plan d'infrastructure {{site.data.keyword.cloud_notm}} en plan facturable et à mettre à niveau votre compte {{site.data.keyword.cloud_notm}} en compte facturable, si nécessaire.

* Pour plus d'informations sur les comptes gratuits et facturables, voir [Types de compte](/docs/account?topic=account-accounts).
* Pour plus d'informations sur la mise à niveau vers un compte facturable, voir  [Mise à niveau de votre compte](/docs/account?topic=account-upgrading-account).
* Pour plus d'informations sur la liaison de vos comptes d'infrastructure {{site.data.keyword.cloud_notm}} et {{site.data.keyword.cloud_notm}}, voir [Passage à l'IBMid et liaison des comptes](/docs/account?topic=account-unifyingaccounts).

## Commande de Zerto on IBM Cloud pour une nouvelle instance
{: #zerto_ordering-new}

Vous pouvez commander une nouvelle instance avec Zerto on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **Zerto on IBM Cloud** dans la section **Services**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Zerto on IBM Cloud** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de Zerto on IBM Cloud pour une instance existante
{: #zerto_ordering-existing}

Vous pouvez ajouter le service Zerto on {{site.data.keyword.cloud_notm}} à une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance à laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Zerto on IBM Cloud** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

Si vous ajoutez Zerto on {{site.data.keyword.cloud_notm}} à une instance vCenter Server doté d'un serveur ESXi qui est en mode maintenance, vous devez utiliser la console Zerto Virtual Manager (ZVM) et l'adresse IP préremplie de Zerto Virtual Replication Appliance (VRA) pour déployer manuellement la machine virtuelle VRA.
{:note}

## Commande de Zerto on IBM Cloud pour des instances uniquement privées
{: #zerto_ordering-private-only}

Si vous souhaitez ajouter Zerto on {{site.data.keyword.cloud_notm}} à une instance uniquement privée, tenez compte de ceci :
* Vous êtes responsable de la configuration de votre propre serveur proxy pour vous connecter à Internet. Pour plus d'informations, voir [Connectivité au réseau public](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Vous devez également configurer la fonction Call Home pour Zerto. Pour plus d'informations sur la fonction Call Home de Zerto, voir [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Liens connexes
{: #zerto_ordering-related}

* [Présentation de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Site Web zerto.com](https://www.zerto.com){:external}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:external}

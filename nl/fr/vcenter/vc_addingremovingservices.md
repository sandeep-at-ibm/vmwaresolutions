---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-01"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande, affichage et retrait de services pour des instances vCenter Server
{: #vc_addingremovingservices}

Vous pouvez commander des services pour vos instances VMware vCenter Server, telle une solution de reprise après incident. Lorsque vous n'avez plus besoin de ces services, vous pouvez les supprimer de vos instances.

Un engagement de 12 mois est demandé lorsque vous commandez le service VMware HCX on {{site.data.keyword.cloud_notm}}. Vous ne pouvez pas supprimer le service tant que votre période de 12 mois n'a pas expiré. La date d'expiration de l'engagement de 12 mois est disponible sur la page des détails relatifs à HCX {{site.data.keyword.cloud_notm}}. Pour plus d'informations sur l'affichage des détails du service, voir [Commande, affichage et suppression de services pour les instances vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

## Services disponibles pour les instances vCenter Server
{: #vc_addingremovingservices-available-services}

Le tableau suivant présente les services disponibles sur les instances vCenter Server, ainsi que les versions installées de ces services :

| Nom de service | Version de service en cours | Version d'instance |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2.1 | A partir de V2.9 |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | A partir de V1.9 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | Série 300 | A partir de V2.0 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | A partir de V2.0 |
| [HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations) | 3.5.1 | V2.1 et versions ultérieures |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | 5.5.1 | A partir de V2.3 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)  | 4.3.2 | A partir de V2.3 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.3.2 | A partir de V2.5 |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1.2 | A partir de V2.5 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | 10.1.3 | A partir de V2.2 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  | Non applicable  |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | A partir de V1.8 |
| [VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vrops_overview) | 9.7 | V3.2 et versions ultérieures |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6.5 update 3 | A partir de V1.2 |
{: caption="Tableau 1. Services disponibles pour les instances vCenter Server" caption-side="top"}

## Procédure d'ajout de services à des instances vCenter Server
{: #vc_addingremovingservices-adding-procedure}

Pour ajouter un service à votre instance vCenter Server, cliquez sur le lien de service approprié dans le tableau précédent pour passer en revue les remarques relatives au service et vérifiez les composants qui sont déployés. Suivez ensuite les instructions de la rubrique sur la commande de service afin d'ajouter le service à votre instance.

### Que se passe-t-il après l'installation d'un service ?
{: #vc_addingremovingservices-adding-results}

Lorsque l'installation du service est terminée, vous êtes prévenu par un courrier électronique, et le service s'affiche sur la page **Services** de l'instance avec le statut **Installé**.

## Procédure d'affichage de services pour des instances vCenter Server
{: #vc_addingremovingservices-viewing-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez afficher les services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche.
4. Sur la page **Services**, cliquez sur un service pour passer en revue les informations le concernant, par exemple, le statut du service et d'autres détails.
5. Selon le service visualisé, vous pouvez accéder aux consoles de service à l'aide des données d'identification qui sont fournies sur la page des détails de service et vous pouvez gérer le service à partir de là.

La date d'expiration de l'engagement de 12 mois pour VMware HCX on {{site.data.keyword.cloud_notm}} est disponible sur la page des détails relatifs à HCX on {{site.data.keyword.cloud_notm}}.
{:note}

## Procédure de retrait de services pour des instances vCenter Server
{: #vc_addingremovingservices-removing-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez retirer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche.
4. Sur la page **Services**, localisez l'instance de service que vous souhaitez retirer et cliquez sur l'icône **Supprimer**.
5. Dans la fenêtre **Supprimer un service**, passez en revue, le cas échéant, les remarques ou avertissements. Sélectionnez **Je comprends** et cliquez sur **Supprimer**.

### Que se passe-t-il après le retrait d'un service ?
{: #vc_addingremovingservices-removing-results}

Une fois votre demande de retrait du service acceptée, le service prend le statut **Retrait en cours**.

Lorsque le retrait du service est terminé, vous êtes prévenu par un courrier électronique, et le service est retiré de la page **Services** de l'instance.

Les services retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
{:note}

## Liens connexes
{: #vc_addingremovingservices-related}

* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notes sur l'édition pour la version V3.2
{: #relnotes_v32}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Disponibilité de VMware HCX for IBM Cloud
{: #relnotes_v32-HCX}

A compter de l'édition 3.2, vous avez la possibilité de commander le service VMware HCX on {{site.data.keyword.cloud_notm}} avec des instances VMware vCenter Server. 
Auparavant, vous ne pouviez commander le service HCX on {{site.data.keyword.cloud_notm}} que via l'instance VMware vCenter Server with Hybridity Bundle. L'instance vCenter Server with Hybridity Bundle n'est plus disponible.

Un engagement de 12 mois est demandé lorsque vous commandez le service HCX on {{site.data.keyword.cloud_notm}}. 
Une fois l'engagement de 12 mois expiré, vous pouvez installer et désinstaller le service HCX on {{site.data.keyword.cloud_notm}} et ajouter et supprimer des hôtes et des clusters sans restrictions. 
Votre compte est ensuite facturé sur une base mensuelle et vous pouvez annuler à tout moment.

Pour plus d'informations, voir [Présentation de VMware HCX on IBM Cloud](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations).

## Prise en charge de VMware vSphere 6.7 Update 2
{: #relnotes_v32-vsphere-v67}

Vous avez désormais la possibilité de commander VMware vSphere version 6.7 Update 2 avec vos instances VMware vCenter Server, VMware vCenter Server with NSX-T et VMware vSphere on IBM Cloud. vSphere Enterprise Plus 6.7u2 remplace l'option de commande de vSphere Enterprise Plus 6.7u1 par de nouvelles instances. En outre, les instances Single-node Trial for Migration and App Modernization et Single-node Trial for Data Protection and Disaster Recovery sont désormais commandées avec vSphere Enterprise Plus 6.7u2.

vSphere Enterprise Plus 6.7u2 est disponible pour Skylake, Cascade Lake et Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Si vous disposez d'une instance existante avec vSphere Enterprise Plus 6.7u1, vous avez la possibilité d'ajouter de nouveaux hôtes avec vSphere Enterprise Plus 6.7u1 ou vSphere Enterprise Plus 6.7u2. 
Toutefois, l'ajout d'un nouvel hôte 6.7u1 n'est pas sécurisé. Il est recommandé de mettre à jour vos hôtes vers la dernière version du serveur ESXi dès que possible.{:note}

## Prise en charge de Cascade Lake
{: #relnotes_v32-cascade}

A compter de la version 3.2, les nouveaux modèles d'unité
centrale {{site.data.keyword.baremetal_short_sing}} suivants sont disponibles pour le déploiement avec des instances et des clusters avec VMware vSphere 6.7 Update 2. Ceci s'applique à vCenter Server, vCenter Server with NSX-T et VMware vSphere.

* Processeur Dual Intel Xeon Gold 4210 / 20 coeurs au total, 2,3 GHz
* Processeur Dual Intel Xeon Gold 5218 / 32 coeurs au total, 2,3 GHz
* Processeur Dual Intel Xeon Gold 6248 / 40 coeurs au total, 2,5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} est disponible dans la région multi-zone (MZR, Multi-Zone Region) {{site.data.keyword.CloudDataCents_notm}}. Pour
plus d'informations, voir [Présentation des régions multi-zone](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Pour plus d'informations sur les paramètres {{site.data.keyword.baremetal_short_sing}}, voir :

* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [Commande d'instances vCenter Server with NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v32-vcs}

Cette version applique les mises à niveau et améliorations suivantes pour les instances, clusters et hôtes récemment déployés :

* VMware NSX for vSphere 6.4.5 (build 13282012)
* vSphere ESXi 6.7 EP 10 (build 6.7.0-13981272)
* vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Update 2b (6.7.0.-13843469)

Pour plus d'informations, voir [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Dénomination du cluster initial
{: #relnotes_v32-vcs-initial-cluster}

Vous pouvez maintenant spécifier le nom du cluster initial à créer au moment où vous commandez votre instance. Pour plus d'informations, voir :

* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Commande d'instances vCenter Server with NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Mises à jour des instances VMware vSphere
{: #relnotes_v32-vss}

Aucun VLAN public n'est désormais requis lorsque vous commandez un nouveau cluster vSphere uniquement avec un réseau privé.

Pour plus d'informations, voir la section *Paramètres de l'interface réseau* dans [Commande de nouveaux clusters vSphere
](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings).

## Mises à jour apportées aux services complémentaires
{: #relnotes_v32-services}

Cette édition installe les versions de service suivantes sur les instances nouvellement déployées :

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

Le service vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware vCenter Server déployées ou mises à niveau vers la version 3.2 ou des éditions ultérieures.

Ce service fournit VMware vRealize Log Insight (vRLI) intégré à vRealize Operations Manager (vROps) pour vous aider à surveiller et gérer de manière proactive la santé et les performances de votre environnement virtualisé, et à effectuer une analyse des causes profondes d'un problème en filtrant et en recherchant dans les journaux.

Vous pouvez commander des instances vCenter Server avec le service vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} inclus ou ajouter ultérieurement ce service à vos instances existantes à partir de l'onglet Services de la page des détails de l'instance.

Vous pouvez également apporter à votre entreprise des licences vRealize Operations and vRealize Log Insight sur le cloud (par UC ou interconnexion de systèmes ouverts) ou louer des licences depuis IBM Cloud.

Pour plus d'informations, voir [Présentation de VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview).

## Documentation nouvelle et mise à jour
{: #relnotes_v32-updated-doc}

* La documentation d'Activity Tracker est mise à jour. Pour plus d'informations, voir [Evénements Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v32-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Les exigences relatives au nom d'instance ont été modifiées. Pour plus d'informations, voir la rubrique appropriée au type d'instance que vous commandez.
* Le format du serveur ESXi qualifié complet a été modifié. Pour plus d'informations, voir la rubrique appropriée au type d'instance que vous commandez.
* Des zéros non significatifs ont été ajoutés aux noms d'hôte et de cluster afin de faciliter le tri.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

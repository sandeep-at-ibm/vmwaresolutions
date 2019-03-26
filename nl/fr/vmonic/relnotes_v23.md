---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 2.3
{: #relnotes_v23}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown
{: #relnotes_v23-spectre}

{{site.data.keyword.vmwaresolutions_short}} a publié des modules de correction depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

Cette édition introduit l'offre VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. vCenter Server with Hybridity Bundle est un cloud privé hébergé qui vous permet de déployer rapidement et facilement votre infrastructure locale dans le cloud. L'environnement VMware est basé sur des licences SDDC (Software Defined Data Center) VMware fournies par IBM et inclut le service VMware HCX on {{site.data.keyword.cloud_notm}} qui permet de connecter très facilement et de manière sécurisée un environnement vSphere 5.0+ local à des sites {{site.data.keyword.cloud_notm}} pour obtenir une hybridité d'infrastructure transparente et une véritable mobilité d'application.

Le service HCX on {{site.data.keyword.cloud_notm}} est disponible uniquement via l'instance vCenter Server with Hybridity Bundle. Vous pouvez mettre à niveau votre instance vCenter Server existante vers une instance vCenter Server with Hybridity Bundle après avoir appliqué la mise à jour logicielle vCenter Server V2.3 de base. Pour plus d'informations, voir [Application de mises à jour à des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

Pour plus d'informations sur vCenter Server with Hybridity Bundle, voir les rubriques suivantes :

* [Présentation de vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## Suppression du support de cluster pour les instances vCenter Server et Cloud Foundation
{: #relnotes_v23-delete-cluster}

Vous pouvez désormais supprimer des clusters sur une instance sans avoir à supprimer celle-ci. Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 pour pouvoir supprimer les clusters que vous lui avez ajoutés.

Pour plus d'informations, voir [Ajout, affichage et suppression de clusters pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances).

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v23-vcs}

Cette édition applique les mises à niveau et améliorations suivantes :
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 avec le niveau de module de correction ESXi650-201803001 appliqué)
*	VMware vCenter Server 6.5 Update 1g

A compter de la version 2.3, les nouveaux modèles d'UC suivants sont disponibles pour déploiement lorsque vous choisissez la configuration de serveur bare metal **Personnalisée** :
* Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz
* Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz

Pour plus d'informations, voir les rubriques suivantes :

* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## Mises à jour des instances VMware Cloud Foundation
{: #relnotes_v23-vcf}

Cette édition applique les mises à niveau et améliorations suivantes :
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 avec le niveau de module de correction ESXi650-201803001 appliqué)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Mises à jour apportées aux services complémentaires
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

Le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. Le service applique et contrôle la conformité par rapport aux normes de sécurité standard et fournit un contrôle d'accès à base de rôles. Combiné à HyTrust DataControl, ce service garantit que les machines virtuelles et les données de charge de travail ne quittent pas une région, un cluster ou un serveur ESXi donnés au sein du centre de données {{site.data.keyword.cloud_notm}}.

Vous pouvez commander des instances avec le service déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes.

Pour plus d'informations, voir les rubriques suivantes :
* [Composants et remarques pour HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Gestion de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

Le service HyTrust DataControl on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. Le service offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service peut fournir un chiffrement au niveau du système d'exploitation et au niveau des données, ce qui signifie que n'importe quel répertoire, dossier ou fichier d'une charge de travail peut être chiffré et déchiffré.

Vous pouvez commander des instances avec le service déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes.

Pour plus d'informations, voir les rubriques suivantes :
* [Composants et remarques pour HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Gestion de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

L'édition en cours installe IBM Spectrum Protect&trade; Plus V10.1.1 comme service de sauvegarde par défaut sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.1, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentation nouvelle et mise à jour
{: #relnotes_v23-new-docs}

Une nouvelle fiche de recette developerWorks est disponible avec des instructions détaillées sur la manière d'ajouter du stockage à IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} après le déploiement. Pour plus d'informations, voir [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v23-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :
* **Cohérence** : l'impression générale de l'interface utilisateur est désormais cohérente avec celle d'autres services sur {{site.data.keyword.cloud_notm}}.
* **Facilité d'accès** : vous pouvez désormais accéder aux offres VMware directement à partir du **catalogue** {{site.data.keyword.cloud_notm}}.
* **Processus de commande rationalisé et simplifié** : vous pouvez désormais commander une instance VMware et déployer ses services complémentaires dans une seule et même interface. En outre, le coût estimé est calculé et présenté instantanément dans la même interface de manière à vous permettre d'ajuster votre configuration en fonction de votre plan des coûts.
* Le mode BYOL n'est pas disponible pour les partenaires commerciaux lors de la commande d'instances ou de l'ajout de clusters.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

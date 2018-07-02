---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Notes sur l'édition pour la version 2.3

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown

{{site.data.keyword.vmwaresolutions_short}} a publié des correctifs depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Pour plus d'informations, voir [Résolution des vulnérabilités Spectre et Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

Cette édition introduit l'offre VMware vCenter Server on IBM Cloud with Hybridity Bundle. vCenter Server with Hybridity Bundle est un cloud privé hébergé qui vous permet de déployer rapidement et facilement votre infrastructure locale dans le cloud. L'environnement VMware est basé sur des licences SDDC (Software Defined Data Center) VMware fournies par IBM et inclut le service VMware HCX on {{site.data.keyword.cloud_notm}} qui permet de connecter très facilement et de manière sécurisée un environnement vSphere 5.0+ local à des sites IBM Cloud pour obtenir une hybridité d'infrastructure transparente et une véritable mobilité d'application. 

Le service HCX on {{site.data.keyword.cloud_notm}} est disponible uniquement via l'instance vCenter Server with Hybridity Bundle. Vous pouvez mettre à niveau votre instance vCenter Server existante vers une instance vCenter Server with Hybridity Bundle après avoir appliqué la mise à jour logicielle vCenter Server V2.3 de base. Pour plus d'informations, voir [Application de mises à jour à des instances vCenter Server](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html).

Pour plus d'informations sur l'instance vCenter Server with Hybridity Bundle, voir :

* [Présentation de vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html)
* [Commande d'instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_orderinginstance.html)

## Suppression du support de cluster pour les instances vCenter Server et Cloud Foundation

Vous pouvez désormais supprimer des clusters sur une instance sans avoir à supprimer celle-ci. Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 pour pouvoir supprimer les clusters que vous lui avez ajoutés.

Pour plus d'informations, voir :

* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Ajout, affichage et suppression de clusters pour des instances Cloud Foundation](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Mises à jour des instances VMware vCenter Server

Cette édition applique les mises à niveau et améliorations suivantes :
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 avec le niveau de module de correction ESXi650-201803001 appliqué)
*	VMware vCenter Server 6.5 Update 1g

### Améliorations apportées aux instances et clusters vCenter Server

A compter de l'édition V2.3, les nouveaux modèles d'UC suivants sont disponibles pour déploiement lorsque vous choisissez la configuration de serveur bare metal **Personnalisée** :
* Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz
* Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz

Pour plus d'informations, voir :

* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Mises à jour des instances VMware Cloud Foundation

Cette édition applique les mises à niveau et améliorations suivantes :
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 avec le niveau de module de correction ESXi650-201803001 appliqué)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Mises à jour apportées aux instances VMware Federal

### Configuration DNS pour les instances VMware Federal

Vous avez maintenant la possibilité de sélectionner le déploiement d'une seule instance de serveur virtuel Microsoft Windows pour Microsoft Active Directory (AD) ou de deux machines virtuelles à haute disponibilité Microsoft Windows dans le cluster de gestion. Pour l'édition V2.2, l'unique instance de serveur virtuel Microsoft Windows pour Microsoft AD a été automatiquement déployée par défaut. La nouvelle option de sélection de deux machines virtuelles Microsoft Windows améliore la confidentialité et offre une possibilité de sauvegarde et de restauration des machines virtuelles à l'aide du service Veeam.

**Remarque :** vous devez fournir deux licences Microsoft Windows Server 2012 R2 si vous configurez votre instance de manière à utiliser deux machines virtuelles Microsoft Windows. Utilisez la licence d'édition Microsoft Windows Server 2012 R2 Standard et/ou la licence d'édition Microsoft Windows Server 2012 R2 Datacenter. Vous disposez de 30 jours pour activer les machines virtuelles.

Pour plus d'informations, voir la section *Paramètres d'interface réseau* dans la rubrique [Commande d'instances VMware Federal](../vcenter/vc_fed_orderinginstance.html#network-interface-settings).

### Ajout et suppression du support de cluster pour les instances VMware Federal

Vous pouvez désormais utiliser des clusters pour gérer des serveurs ESXi dans les instances VMware Federal déployées dans la version 2.3 et des éditions ultérieures de manière à bénéficier d'une meilleure gestion des ressources et de la haute disponibilité. Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**. Vous pouvez afficher les détails du cluster sur la page de présentation d'une instance ou ajouter jusqu'à 10 clusters à une instance. Lorsque vous augmentez ou réduisez la capacité d'une instance, vous pouvez sélectionner le cluster dans lequel ajouter ou retirer des serveurs ESXi.

Vous avez également la possibilité de supprimer un ou plusieurs clusters de l'instance sans avoir à supprimer celle-ci.

Pour plus d'informations, voir [Ajout, affichage et suppression de clusters pour des instances VMware Federal](../vcenter/fed_addviewdeleteclusters.html).

## Mises à jour apportées aux services complémentaires

### HyTrust CloudControl on IBM Cloud

Le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. Le service applique et contrôle la conformité par rapport aux normes de sécurité standard et fournit un contrôle d'accès à base de rôles. Combiné à HyTrust DataControl, ce service garantit que les machines virtuelles et les données de charge de travail ne quittent pas une région, un cluster ou un serveur ESXi donnés au sein du centre de données {{site.data.keyword.cloud_notm}}.

Vous pouvez commander des instances avec le service déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes. 

Pour plus d'informations, voir :
* [Composants et remarques pour HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)
* [Gestion de HyTrust CloudControl on IBM Cloud](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

Le service HyTrust DataControl on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. Le service offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service peut fournir un chiffrement au niveau du système d'exploitation et au niveau des données, ce qui signifie que n'importe quel répertoire, dossier ou fichier d'une charge de travail peut être chiffré et déchiffré.

Vous pouvez commander des instances avec le service déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes. 

Pour plus d'informations, voir :
* [Composants et remarques pour HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)
* [Gestion de HyTrust DataControl on IBM Cloud](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

L'édition en cours installe IBM Spectrum Protect&trade; Plus V10.1.1 comme service de sauvegarde par défaut sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.1, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentation nouvelle et mise à jour

Une nouvelle fiche de recette developerWorks est disponible avec des instructions détaillées sur la manière d'ajouter du stockage à IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} après le déploiement. Pour plus d'informations, voir [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Améliorations et mises à jour apportées à l'interface utilisateur

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :
* **Cohérence** : l'impression générale de l'interface utilisateur est désormais cohérente avec celle d'autres services sur IBM Cloud.
* **Facilité d'accès** : vous pouvez désormais accéder aux offres VMware directement à partir du **catalogue** IBM Cloud.
* **Processus de commande rationalisé et simplifié** : vous pouvez désormais commander une instance VMware et déployer ses services complémentaires dans une seule et même interface. En outre, le coût estimé est calculé et présenté instantanément dans la même interface de manière à vous permettre d'ajuster votre configuration en fonction de votre plan des coûts.
* Le mode BYOL n'est pas disponible pour les partenaires commerciaux lors de la commande d'instances ou de l'ajout de clusters.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

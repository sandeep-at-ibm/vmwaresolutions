---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 1.7
{: #relnotes_v17}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Mises à jour des instances VMware Cloud Foundation
{: #relnotes_v17-vcf}

Cette mise à jour applique les mises à niveau et améliorations suivantes :
* Gestionnaire VMware SDDC 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Améliorations de la stabilité du composant IBM CloudDriver
* Le mode EVC (basé sur le processeur Intel “Haswell” 2690-V3) est activé sur les déploiements VMware pré-existants qui se trouvent sur des serveurs V3 au moment de la mise à niveau.

  Le mode EVC n'est pas activé pour les déploiements nouveaux ou existants sur des serveurs V4.
  {:note}

* Les déploiements VMware Cloud Foundation effectués avant le 22 mai et qui utilisent donc des serveurs V3 commanderont désormais des serveurs V4 lors de l'ajout d'un nouveau noeud à l'instance. Ces serveurs disposent de 256 Go de mémoire. Si vous avez besoin de 512 Go de mémoire, une fois les serveurs ajoutés, ouvrez un ticket de demande de service pour solliciter une mise à niveau à 512 Go de mémoire. Pour savoir comment contacter le support IBM, voir [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

### Améliorations du processus de mise à jour
{: #relnotes_v17-update-process}

Selon la complexité de votre déploiement d'instance Cloud Foundation et si vous disposez d'une configuration multisite, le processus de mise à jour peut nécessiter d'effectuer une série d'opérations en respectant la procédure affichée dans l'onglet **Mise à jour et module de correction** sur la console.

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v17-vcs}

### Prise en charge des clusters
{: #relnotes_v17-cluster}

A compter de la version 1.7, vous pouvez utiliser des clusters pour gérer des serveurs ESXi dans des instances vCenter Server pour bénéficier d'une meilleure gestion des ressources et de la haute disponibilité. Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**. Vous pouvez afficher les détails du cluster et ajouter jusqu'à cinq clusters à une instance à partir du nouvel onglet **Infrastructure** de la page des détails de l'instance. Lorsque vous augmentez ou réduisez la capacité d'une instance, vous pouvez sélectionner le cluster dans lequel ajouter ou retirer des serveurs ESXi. Pour plus d'informations, voir [Ajout et affichage de clusters pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances).

### Améliorations au niveau du déploiement de la reprise après incident Zerto
{: #relnotes_v17-zerto}

Le déploiement de la reprise après incident Zerto est désormais automatisé et non géré via un ticket de demande de service. Tous les composants Zerto, tels qu'un sous-réseau portable privé, une instance de service virtuel Windows et les frais de licence Zerto sont répertoriés dans le coût estimé, de sorte que vous pouvez les vérifier avant de commander. Pour plus d'informations, voir [Processus de déploiement de la reprise après incident Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

### Possibilités de mise à niveau de la licence NSX
{: #relnotes_v17-nsx}

Vous pouvez mettre à niveau votre édition de licence NSX depuis la page **Récapitulatif** de votre instance vCenter Server. La mise à niveau de la licence remplace toutes les licences NSX SoftLayer existantes de votre compte par la nouvelle licence. Pour plus d'informations, voir [Affichage d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances).

## Améliorations de la convivialité
{: #relnotes_v17-ui}

Des améliorations ont été apportées à l'interface utilisateur, à savoir :
* L'onglet **Propriétés** de la page des détails de l'instance Cloud Foundation a été renommé **Récapitulatif**. Vous pouvez désormais afficher sur cet onglet les détails de l'instance, les informations d'accès des composants associés à l'instance et l'historique de déploiement de l'instance.
* Un onglet **Infrastructure** a été ajouté sur la page des détails de l'instance Cloud Foundation. Sur cet onglet, vous pouvez afficher, ajouter ou supprimer des serveurs ESXi.
* La documentation relative à {{site.data.keyword.vmwaresolutions_short}} se présente sous un nouveau format et elle est désormais totalement intégrée au catalogue Bluemix, avec l'ensemble de la documentation Bluemix. Vous pouvez accéder à la documentation de l'une des manières suivantes :
  * Depuis {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Docs** à gauche de la bannière.
  * Depuis le catalogue de la documentation Bluemix, faites défiler vers le bas jusqu'à la section **Compute & Services**, puis cliquez sur **{{site.data.keyword.vmwaresolutions_short}}**.

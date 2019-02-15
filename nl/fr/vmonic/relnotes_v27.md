---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notes sur l'édition pour la version 2.7

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Prise en charge de serveur 6140 SAP certifié

A compter de la version 2.7, les nouveaux modèles d'UC de serveur {{site.data.keyword.baremetal_short_sing}} {{site.data.keyword.cloud_notm}} sont disponibles pour déploiement pour les instances et les clusters VMware vCenter Server on {{site.data.keyword.cloud_notm}} et VMware vSphere on {{site.data.keyword.cloud_notm}} :
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/192 Go de mémoire RAM
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,2 GHz/384 Go de mémoire RAM
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/768 Go de mémoire RAM

Pour plus d'informations, voir la section *Paramètres de serveur {{site.data.keyword.baremetal_short_sing}}* dans :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Mises à jour apportées aux services complémentaires

### IBM Cloud Private Hosted

Le service {{site.data.keyword.cloud_notm}} Private Hosted est désormais disponible pour les instances VMware vCenter Server with Hybridity Bundle, en plus des instances VMware vCenter Server déployées dans (ou mises à niveau vers) la version 2.5 et des éditions ultérieures. Vous pouvez désormais commander une instance vCenter Server ou une instance vCenter Server with Hybridity Bundle avec le service inclus. Ou vous pouvez ajouter le service à une instance vCenter Server ou vCenter Server with Hybridity Bundle existante après le déploiement initial.

Pour plus d'informations, voir les rubriques suivantes :
* [Présentation d'{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services/icp_overview.html)
* [Commande d'{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services/icp_ordering.html)

### Mission Critical VMware on IBM Cloud

Le service Mission Critical VMware on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances qui sont déployées dans, ou mises à niveau vers, la version 2.7 ou des éditions ultérieures.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} fournit une architecture de cloud multi-zone qui permet aux entreprises d'empêcher les temps d'indisponibilité pour les applications en cloud et qui permet d'automatiser les basculements dans une région de cloud. Grâce à cette architecture de cloud, vous pouvez atteindre un taux de réussite de disponibilité et de basculement plus élevé que celui obtenu par la plupart des clients VMware avec des environnements sur site ou des plateformes cloud concurrentes.

Pour plus d'informations, voir [Présentation de Mission Critical VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/mcv_overview.html).

### F5 on IBM Cloud

Désormais, lorsque vous commandez le service F5 on {{site.data.keyword.cloud_notm}}, vous pouvez indiquer si F5 doit appliquer la licence sur un réseau public ou un réseau privé avec un serveur proxy. Pour plus d'informations, voir [Commande de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_ordering.html).

### FortiGate Virtual Appliance on IBM Cloud

Au cours du troisième trimestre 2018, Fortinet a modifié ses offres groupées d'abonnement. Pour plus d'informations, voir [Commande de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_ordering.html).

Pour le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} qui est déployé dans les instances Cloud Foundation et vCenter Server versions 2.7 et ultérieures, FortiOS 6.0.3 est mis à disposition.

Lorsque vous commandez le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, vous pouvez indiquer si FortiGuard doit appliquer les mises à jour de licence et de sécurité sur un réseau public ou un réseau privé avec un serveur proxy. Pour plus d'informations, voir [Commande de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_ordering.html).

### Mises à jour du composant de service Zerto on IBM Cloud

Pour le service Zerto on {{site.data.keyword.cloud_notm}} qui est déployé dans les instances Cloud Foundation et vCenter Server versions 2.7 et ultérieures, Zerto Virtual Replication 6.0 update 3 est mis à disposition. Pour plus d'informations, voir [Présentation de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/addingzertodr.html).

### Intégration de KMIP for VMware on IBM Cloud à IBM Cloud Activity Tracker

En plus des événements d'instance VMware, les événements pour KMIP for VMware on {{site.data.keyword.cloud_notm}}, tels que la création de clé, la suppression de clé et l'accès aux clés, sont désormais intégrés à votre instance {{site.data.keyword.cloud_notm}} Activity Tracker. Pour plus d'informations sur KMIP for WMware on {{site.data.keyword.cloud_notm}}, voir [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### KMIP for VMware on IBM Cloud - Obsolète

(Mise à jour du 14 décembre 2018) La version actuelle de KMIP for VMware on {{site.data.keyword.cloud_notm}} va devenir obsolète. Pour plus d'informations, voir [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).
{:deprecated}

## Documentation nouvelle et mise à jour

### Documentation d'architecture de référence

Les documents techniques suivants sont désormais disponibles dans la section *Référence* de la documentation utilisateur :

* [Architecture de la solution NSX Edge Services Gateway](/docs/services/vmwaresolutions/archiref/nsx/nsx_overview.html)
* [Guide VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum/vum-intro.html)
* [Guide de mise en réseau de vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt/vcsnsxt-intro.html)
* [Guide vCenter Server et {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html)
* [Guide de maintenance de vCenter Server et IBM Kubernetes](/docs/services/vmwaresolutions/archiref/vcsiks/vcsiks-intro.html)
* [Guide Concept Car pour VMware et Skate Advisor](/docs/services/vmwaresolutions/archiref/vcscar/vcscar-intro.html)
* [VMware - Le parcours de modernisation de Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent/vcscontent-modjourney.html)

## Améliorations et mises à jour apportées à l'interface utilisateur

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* L'onglet **Personnalisé** sur lequel vous spécifiez le modèle d'UC et la mémoire RAM pour les paramètres de serveur {{site.data.keyword.baremetal_short_sing}} lorsque vous commandez des instances a été scindé en deux onglets, **Skylake** et **Broadwell**, en fonction du type de serveur, afin de vous aider à choisir un serveur.
* Les options **Préconfiguré** pour la configuration de serveur bare metal ne sont plus disponibles.
* La colonne **Type** est désormais incluse dans le tableau **Instances vCenter Server** sur la page **Instances déployées** pour identifier les instances vCenter Server, vCenter Server with Hybridity Bundle et les instances d'unité de test limitée vCenter.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

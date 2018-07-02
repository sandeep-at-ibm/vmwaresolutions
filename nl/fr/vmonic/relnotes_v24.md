---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# Notes sur l'édition pour la version 2.4

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown

{{site.data.keyword.vmwaresolutions_short}} a publié des correctifs depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Pour plus d'informations, voir [Résolution des vulnérabilités Spectre et Meltdown](../vmonic/trbl_fix_spectre.html).

## Support de langue nationale

A compter de l'édition V2.4, le support de langue nationale est disponible pour IBM Cloud for VMware Solutions.
Toutes les fonctions de la console, y compris la documentation utilisateur, sont disponibles dans plusieurs langues. 

Les langues suivantes sont prises en charge, en plus de l'anglais :
* Allemand
* Espagnol
* Français
* Italien
* Japonais
* Coréen
* Portugais (Brésil)
* Chinois simplifié
* Chinois traditionnel

**Remarque** : les documents sur l'architecture de référence ne sont disponibles qu'en anglais. 

## Prise en charge d'UC Skylake Xeon

A compter de l'édition V2.4, les nouveaux modèles d'UC de serveur bare metal suivants sont disponibles pour déploiement pour les instances et les clusters VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}} et VMware Federal on {{site.data.keyword.cloud_notm}} :

* Processeur Dual Intel Skylake Xeon Silver 4110/16 coeurs au total, 2,1 GHz
* Processeur Dual Intel Skylake Xeon Gold 5120/28 coeurs au total, 2,2 GHz
* Processeur Dual Intel Skylake Xeon Gold 6140/36 coeurs au total, 2,3 GHz

Pour plus d'informations, voir la section *Paramètres de serveur bare metal* dans :

* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Commande de nouveaux clusters vSphere](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [Commande d'instances VMware Federal](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Mises à jour des instances VMware vCenter Server

### Amélioration apportées aux performances du système NFS

Le niveau de performance de 10 IOPS/Go, conçu pour les types de charge de travail les plus exigeants, n'est plus limité à un {{site.data.keyword.CloudDataCent_notm}} spécifique; il est désormais disponible pour tous les centres de données. Pour plus d'informations, voir la section *Stockage* dans [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html#vcenter-server-technical-specifications).

## Mises à jour apportées aux instances VMware Federal

### Nouvelle option IBM Cloud Data Center

Vous pouvez désormais déployer des instances VMware Federal sur l'{{site.data.keyword.CloudDataCent_notm}} DAL08 - Dallas, TX. Pour plus d'informations, voir la section *Disponibilité d'IBM Cloud Data Center* dans [Exigences et planification pour les instances VMware Federal](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Mises à jour apportées aux services complémentaires

### IBM Spectrum Protect Plus on IBM Cloud

L'édition en cours installe IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 comme service de sauvegarde par défaut sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.1 Patch 1, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

Une nouvelle option est désormais disponible pour vous permettre de choisir entre un réseau public et un réseau privé pour les interconnexions HCX lorsque vous commandez ce service. Pour plus d'informations, voir [Commande de VMware HCX on IBM Cloud](../services/hcx_ordering.html).

## Documentation nouvelle et mise à jour

### Documentation d'architecture de référence

La documentation sur l'architecture {{site.data.keyword.vmwaresolutions_short}} est désormais disponible dans la section *Référence* de la documentation utilisateur. La documentation sur l'architecture de référence est disponible en anglais uniquement. Pour plus d'informations, voir [Présentation de Solution ](../archiref/solution/solution_overview.html).

### Documentation sur les services

Les informations sur les services ont été restructurées et la navigation a été améliorée afin de trouver facilement les informations appropriées lors de la commande de services. 

Pour plus d'informations, voir :

* [Commande de F5 on IBM Cloud](../services/f5_ordering.html)
* [Commande de FortiGate Security Appliance on IBM Cloud](../services/fortigate_physical_ordering.html)
* [Commande de FortiGate Virtual Appliance on IBM Cloud](../services/fortigate_vm_ordering.html)
* [Commande de Hytrust CloudControl on IBM Cloud](../services/htcc_ordering.html)
* [Commande de Hytrust DataControl on IBM Cloud](../services/htdc_ordering.html)
* [Commande d'IBM Spectrum Protect Plus on IBM Cloud](../services/spp_ordering.html)
* [Commande de KMIP for VMware on IBM Cloud](../services/kmip_ordering.html)
* [Commande de Veeam on IBM Cloud](../services/veeam_ordering.html)
* [Commande de Zerto on IBM Cloud](../services/zerto_ordering.html)

## Améliorations et mises à jour apportées à l'interface utilisateur

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Les panneaux d'ajout de cluster et d'ajout de service utilisent désormais un format de page, avec une présentation mieux organisée, ce qui vous permet d'exécuter des tâches avec plus d'efficience. 
* La fonctionnalité de la page **Instances déployées** a été améliorée grâce à l'ajout de fonctions de recherche, de pagination et de tri. Ces améliorations vous permettent de localiser très rapidement vos instances. 
* La page des détails d'instance utilise désormais un menu de navigation situé sur la gauche, qui vous permet d'accéder facilement et rapidement aux informations sur l'instance. 
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

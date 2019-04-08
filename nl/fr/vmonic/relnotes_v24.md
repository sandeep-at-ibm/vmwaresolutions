---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 2.4
{: #relnotes_v24}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} a publié des modules de correction depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Support de langue nationale
{: #relnotes_v24-nls}

A compter de la version 2.4, le support de langue nationale est disponible pour {{site.data.keyword.vmwaresolutions_short}}.
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

## Prise en charge d'UC Skylake Xeon
{: #relnotes_v24-skylake}

A compter de la version 2.4, les nouveaux modèles d'UC de serveur bare metal suivants sont disponibles pour le déploiement pour les instances et les clusters VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} et VMware vSphere on {{site.data.keyword.cloud_notm}} :

* Processeur Dual Intel Skylake Xeon Silver 4110/16 coeurs au total, 2,1 GHz
* Processeur Dual Intel Skylake Xeon Gold 5120/28 coeurs au total, 2,2 GHz
* Processeur Dual Intel Skylake Xeon Gold 6140/36 coeurs au total, 2,3 GHz

Pour plus d'informations, voir la section *Paramètres de serveur bare metal* dans la rubrique [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings).

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v24-vcs}

### Amélioration apportées aux performances du système NFS
{: #relnotes_v24-nfs}

Le niveau de performance de 10 IOPS/Go, conçu pour les types de charge de travail les plus exigeants, n'est plus limité à un {{site.data.keyword.CloudDataCent_notm}} spécifique; il est désormais disponible pour tous les centres de données. Pour plus d'informations, voir la section *Stockage* dans [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances).

## Mises à jour apportées aux services complémentaires
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

L'édition en cours installe IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.1 Patch 1, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

Une nouvelle option est désormais disponible pour vous permettre de choisir entre un réseau public et un réseau privé pour les interconnexions HCX lorsque vous commandez ce service. Pour plus d'informations, voir [Commande de VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## Documentation nouvelle et mise à jour
{: #relnotes_v24-new-docs}

### Documentation d'architecture de référence
{: #relnotes_v24-ref-archi}

La documentation sur l'architecture {{site.data.keyword.vmwaresolutions_short}} est désormais disponible dans la section *Référence* de la documentation utilisateur. Pour plus d'informations, voir [Présentation de Solution](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Documentation sur les services
{: #relnotes_v24-docs-services}

Les informations sur les services ont été restructurées et la navigation a été améliorée afin de trouver facilement les informations appropriées lors de la commande de services.

Pour plus d'informations, voir les rubriques suivantes :

* [Commande de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Commande de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Commande de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Commande de Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Commande de Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Commande d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Commande de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Commande de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v24-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Les panneaux d'ajout de cluster et d'ajout de service utilisent désormais un format de page, avec une présentation mieux organisée, ce qui vous permet d'exécuter des tâches avec plus d'efficience.
* La fonctionnalité de la page **Ressources** a été améliorée grâce à l'ajout de fonctions de recherche, de pagination et de tri. Ces améliorations vous permettent de localiser rapidement vos instances.
* La page des détails d'instance utilise désormais un menu de navigation situé sur la gauche, qui vous permet d'accéder facilement et rapidement aux informations sur l'instance.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

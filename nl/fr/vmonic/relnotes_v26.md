---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-01"

subcollection: vmware-solutions


---

# Notes sur l'édition pour la version 2.6
{: #relnotes_v26}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown
{: #relnotes_v26-spectre}

{{site.data.keyword.vmwaresolutions_short}} a publié des modules de correction depuis VMware afin de remédier à des vulnérabilités liées à Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Option Hautes performances avec Intel Optane
{: #relnotes_v26-optane}

Cette édition fournit une option vous permettant d'ajouter un cache hautes performances pour le stockage vSAN lorsque vous commandez une nouvelle instance ou que vous ajoutez un nouveau cluster vSAN après le déploiement initial.

Cette option vous permet d'augmenter le nombre de disques de capacité de stockage et de le faire passer de huit à dix au maximum.

L'option Hautes performances avec Intel Optane est disponible uniquement pour les configurations personnalisées avec des processeurs Dual Intel Xeon Gold 5120 et Dual Intel Xeon Gold 6140.

Pour plus d'informations, voir la rubrique de commande appropriée pour votre type d'instance ou de cluster.

## Activation d'un réseau public ou privé
{: #relnotes_v26-pub-private-network}

Vous pouvez désormais déployer des instances vCenter Server et vCenter Server with Hybridity Bundle, ainsi que des clusters VMware vSphere, avec des cartes d'interface réseau publiques et privées activées ou uniquement des cartes d'interface réseau privées activées. Cette option est également disponible lorsque vous ajoutez un nouveau cluster à vos instances vCenter Server et vCenter Server with Hybridity Bundle.

Certains services complémentaires nécessitent des cartes d'interface réseau publiques et ne sont pas disponibles si vous sélectionnez l'option d'activation de réseau privé uniquement :

Pour plus d'informations, voir la section _Paramètres d'interface réseau_ dans les rubriques suivantes :

* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#network-interface-settings)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#network-interface-settings)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#network-interface-settings)

## Suppression de serveurs ESXi
{: #relnotes_v26-delete-esxi}

Vous pouvez désormais supprimer un serveur ESXi de votre instance vCenter Server, vCenter Server with Hybridity Bundle ou Cloud Foundation si vous respectez la configuration minimale requise pour votre instance.

Pour plus d'informations sur la configuration requise pour les serveurs ESXi, voir les rubriques suivantes :

* [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v26-vcs}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Mises à jour de VMware vCenter Server with Hybridity Bundle
{: #relnotes_v26-vcs-hybrid}

### Retrait de la licence Hybridity Bundle d'une instance vCenter Server
{: #relnotes_v26-remove-bundle}

Vous pouvez désormais retirer la licence Hybridity Bundle de votre instance vCenter Server. Pour ce faire, vous devez remplacer les clés de licence locative VMware NSX et VMware vSAN par des clés BYOL (Bring Your Own License) et ouvrir un ticket de demande de service pour annuler les frais liés aux licences locatives.

Pour plus d'informations, voir [Retrait de la licence Hybridity Bundle d'une instance vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletingbundle).

### Disponibilité de vCenter Server with Hybridity Bundle
{: #relnotes_v26-bundle-available}

Les partenaires commerciaux peuvent désormais commander une instance vCenter Server with Hybridity Bundle. Les partenaires commerciaux ne peuvent pas mettre à niveau une instance vCenter Server existante vers une instance vCenter Server with Hybridity Bundle et ne peuvent pas retirer la licence Hybridity Bundle d'une instance vCenter Server with Hybridity Bundle.

Pour plus d'informations, voir les rubriques suivantes :

* [Présentation de vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## Mises à jour des instances VMware Cloud Foundation
{: #relnotes_v26-vcf}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Mises à jour apportées aux services complémentaires
{: #relnotes_v26-services}

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v26-htkc}

Le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.5 et des éditions ultérieures. Le service simplifie la gestion des charges de travail chiffrées en automatisant et en simplifiant le cycle de vie des clés de chiffrement. Le service peut facilement gérer les clés de chiffrement à l'échelle à l'aide du chiffrement compatible avec FIPS 140-2. En utilisant ce service, vous pouvez gérer les clés de chiffrement pour toutes vos machines virtuelles et tous vos magasins de données chiffrés et les faire évoluer pour prendre en charge des milliers de charges de travail chiffrées dans des déploiements de grande taille.

Vous pouvez commander des instances avec le service déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes.

Pour plus d'informations, voir les rubriques suivantes :
* [Composants et remarques pour HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Gestion de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v26-htcc}

L'édition en cours installe HyTrust CloudControl 5.4 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans HyTrust CloudControl 5.4, voir l'[ensemble de la documentation en ligne pour HyTrust CloudControl v 5.4](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html).

### HyTrust DataControl on IBM Cloud
{: #relnotes_v26-htdc}

L'édition en cours installe HyTrust DataControl 4.2 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans HyTrust DataControl 4.2, voir [What's New in HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm).

### Prise en charge de Veeam on IBM Cloud pour vSphere ESXi V6.5 update 2c
{: #relnotes_v26-veeam}

A compter de la version 2.6, de nouvelles instances et de nouveaux hôtes sont mis à disposition à l'aide de vSphere ESXi V6.5 Update 2c. Si vous utilisez Veeam Backup and Replication, Veeam vous recommande de mettre à jour votre instance Veeam on {{site.data.keyword.cloud_notm}} vers V9.5u3a ou une édition ultérieure afin de garantir une compatibilité optimale avec vSphere ESXi 6.5 Update 2c.

Il est recommandé de mettre à jour également les instances Cloud Foundation existantes dotées de Veeam on {{site.data.keyword.cloud_notm}} vers V9.5u3a ou une édition ultérieure.

Pour plus d'informations sur Veeam on {{site.data.keyword.cloud_notm}}, voir [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations).

### VMware HCX on IBM Cloud
{: #relnotes_v26-hcx}

L'édition en cours installe VMware HCX 3.5.1 sur toutes les instances nouvellement déployées. Pour en savoir plus sur les nouvelles fonctions disponibles dans HCX 3.5.1, consultez la [documentation sur VMware HCX](https://docs.vmware.com/en/VMware-HCX/index.html).

### Prise en charge de Zerto on IBM Cloud pour vSphere ESXi V6.5 update 2c
{: #relnotes_v26-zerto}

Si vous mettez à jour des hôtes existants vers vSphere ESXi V6.5 update 2 et que vous avez déjà installé Zerto on {{site.data.keyword.cloud_notm}}, la console de réplication virtuelle de Zerto
peut afficher le message d'avertissement `Unsupported ESX Version` sous le statut des dispositifs VRA (Virtual Replication Appliance) de Zerto.

Pour en savoir plus sur comment résoudre ce message d'avertissement, voir :

* [Zerto Virtual Replication Interoperability Matrix](http://s3.amazonaws.com/zertodownload_docs/6.0_Latest/Zerto%20Virtual%20Replication%20Operability%20Matrix.pdf)
* [Updating a ZVM to Support Zerto-Approved Host Releases Prior to a Full ZVR Update](https://www.zerto.com/myzerto/knowledge-base/updating-a-zvm-to-support-zerto-approved-host-releases-prior-to-a-full-zvr-update/)

## Documentation nouvelle et mise à jour
{: #relnotes_v26-new-docs}

### Documentation d'architecture de référence
{: #relnotes_v26-ref-archi}

Le document sur l'architecture {{site.data.keyword.vmwaresolutions_short}} a été mis à jour avec des remarques importantes destinées à vous permettre de bien comprendre quelles sont vos responsabilités en termes de gestion et d'exécution de votre instance VMware.

Pour plus d'informations, voir [Remarques relatives au post-déploiement pour votre instance VMware](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_considerations).

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v26-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

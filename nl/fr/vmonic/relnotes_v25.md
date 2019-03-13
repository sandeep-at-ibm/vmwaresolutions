---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 2.5
{: #relnotes_v25}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown

{{site.data.keyword.vmwaresolutions_short}} a publié des modules de correction depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Pour plus d'informations, voir [Résolution des vulnérabilités Spectre et Meltdown](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_fix_spectre).

## Mise à jour du composant NSX

Cette édition installe VMware NSX for vSphere 6.4.1 pour les nouveaux déploiements de VMware vCenter Server on {{site.data.keyword.cloud_notm}}, VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle et NetApp ONTAP Select.

## Retrait de la configuration de sauvegarde par défaut

{{site.data.keyword.vmwaresolutions_short}} offre deux services de modules complémentaires intégrés pour la sauvegarde : IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} et Veeam on {{site.data.keyword.cloud_notm}}. Ces services vous permettent de planifier et de fournir la reprise de votre infrastructure de gestion et votre charge de travail. De plus, IBM Resiliency Services fournit des services gérés pour les sauvegardes Veeam.

A partir de la version 2.5, les services IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} et Veeam on {{site.data.keyword.cloud_notm}}, lorsqu'ils sont déployés, ne préconfigurent plus la sauvegarde de machines virtuelles. Ce changement vous permet d'assurer la configuration appropriée de tous les aspects de vos tâches de sauvegarde, y compris la planification, la durée de conservation, l'utilisation du dédoublonnage, la surveillance et les alertes et la gestion de clés de chiffrement. De plus, la machine virtuelle IBM CloudDriver n'est plus configurée en tant que serveur de fichiers permanent pour les sauvegardes NSX.

Vous êtes chargé de configurer, gérer et surveiller tous les composants logiciels, y compris la sauvegarde et la disponibilité de l'infrastructure de gestion et des charges de travail. Pour plus d'informations, voir [Sauvegarde des composants](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#backing-up-components).

Ce changement n'affecte pas les instances déployées antérieures à la version 2.5 sur lesquelles le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}} est déjà installé.
{:note}

## Résilience IBM CloudDriver

Pour les instances déployées dans ou mises à niveau vers la version 2.5 ou des éditions ultérieures, le composant IBM CloudDriver n'est plus configuré en tant que machine virtuelle dans le cluster vSphere. Au lieu de cela, il est déployé en tant qu'instance de serveur virtuel d'infrastructure {{site.data.keyword.cloud_notm}} en fonction des besoins avec le dernier code {{site.data.keyword.cloud_notm}} pour VMware pour les opérations, telles que le déploiement de noeuds, de clusters ou de services supplémentaires. De plus, le composant IBM CloudDriver est modifié pour communiquer avec le plan de gestion {{site.data.keyword.cloud_notm}} à l'aide du réseau privé {{site.data.keyword.cloud_notm}}. Par conséquent, le pare-feu ESG (Edge Services Gateway) NSX de gestion et les règles NAT autorisant IBM CloudDriver à établir des communications sortantes avec le réseau public sont retirés.

Certains services de modules complémentaires, tels que F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} et Zerto on {{site.data.keyword.cloud_notm}} nécessitent toujours un accès au réseau public, par conséquent, le pare-feu ESG NSX de gestion reste déployé dans toutes les instances.

## Gestion des accès et des utilisateurs activée par IAM

A partir de la version 2.5, {{site.data.keyword.vmwaresolutions_short}} est intégré à IAM (IBM Identity and Access Management) afin de fournir une approche unifiée de gestion des comptes utilisateur et des accès utilisateur dans votre compte {{site.data.keyword.cloud_notm}}. A cause de cela :
* Vous pouvez désormais ajouter plusieurs utilisateurs à votre compte {{site.data.keyword.cloud_notm}} à des fins de collaboration, et vous pouvez gérer leur accès aux services et aux ressources mis à disposition dans votre compte en affectant à ces utilisateurs différents rôles d'accès à une plateforme.  
* Les instances qui sont déployées dans la version 2.5 et dans des éditions ultérieures sont liées automatiquement au compte utilisateur qui est utilisé lors de la commande de l'instance.
* Quant aux instances déployées dans la version 2.4 et dans des éditions antérieures, vous pouvez les faire migrer vers un compte {{site.data.keyword.cloud_notm}} spécifié, puis les gérer également à l'aide d'IAM.

Pour plus d'informations, voir les rubriques suivantes :
* [Invitation des utilisateurs à accéder à des services et des ressources](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Gestion des accès utilisateur à l'aide d'IAM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)

## Modifications apportées aux comptes d'utilisateur et aux groupes pour les instances VMware vCenter Server et VMware Cloud Foundation

Le groupe d'utilisateurs **ic4v-vCenter** a été créé sur le serveur Microsoft Active Directory et ajouté aux droits globaux des groupes d'utilisateurs vCenter Server pour NSX Manager. Le groupe contient le compte utilisateur **automation** pour les instances vCenter Server et des comptes utilisateur spécifiques du service pour les instances vCenter Server et Cloud Foundation.

N'éditez pas les droits globaux du groupe **ic4v-vCenter** sur la page **Utilisateurs et groupes** du client Web VMware vSphere. Cela pourrait avoir une incidence sur les opérations de gestion.

Pour les instances Cloud Foundation, utilisez l'ID utilisateur d'hôte **customerroot** à la place de l'ID utilisateur d'hôte **root**.

Pour les instances vCenter Server, continuez à utiliser l'ID utilisateur hôte **root**. L'ID utilisateur hôte **ic4vroot** a été créé pour une utilisation IBM seulement.

Pour plus d'informations sur les comptes utilisateur, voir les rubriques suivantes :

* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)
* [Remarques relatives à la modification des artefacts Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cf_chg_impact)

## Mises à jour apportées aux services complémentaires

### IBM Cloud Private Hosted (mis à jour le 30 août 2018)

Le service {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances vCenter Server déployées dans (ou mises à niveau vers) la version 2.5 ou des éditions ultérieures.

Le service {{site.data.keyword.cloud_notm}} Private Hosted fournit la puissance des microservices et des conteneurs à votre environnement VMware sur {{site.data.keyword.cloud_notm}}. Grâce à ce service, vous pouvez déployer le même modèle opérationnel et les mêmes outils VMware et {{site.data.keyword.cloud_notm}} locaux dans {{site.data.keyword.cloud_notm}}.

Vous pouvez demander ce service après avoir commandé votre instance vCenter Server.

### IBM Spectrum Protect Plus on IBM Cloud

A partir de la version 2.5, le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} est déployé sous forme de deux machines virtuelles distinctes, l'une d'elles exécutant le serveur IBM Spectrum Protect Plus et l'autre exécutant le serveur vSnap et le proxy VADP.

Vous pouvez désormais commander jusqu'à 10 magasins de données de sauvegarde et bénéficier ainsi d'un stockage de sauvegarde pouvant atteindre 120 To. Les machines virtuelles vSnap et VADP sont dimensionnées en fonction de la taille du stockage de sauvegarde que vous avez sélectionnée et conformément aux informations décrites dans le wiki [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### KMIP for VMware on IBM Cloud

Un nouveau noeud final est désormais disponible en Allemagne pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir [Configuration du service KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_ordering.html#kmip-for-vmware-on-ibm-cloud-service-configuration).

## Documentation nouvelle et mise à jour

### Documentation sur le stockage connecté

La documentation technique sur le stockage connecté pour vCenter Server on IBM Cloud est désormais disponible dans la section *Référence* de la documentation utilisateur. Pour plus d'informations, voir [Stockage connecté pour vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-benefits).

### Spécifications techniques

Les spécifications techniques pour tous les types d'instance et tous les types de service sont désormais disponibles dans la documentation utilisateur et liées à partir de l'interface utilisateur. Pour plus d'informations, voir la rubrique de présentation appropriée pour votre instance et votre service.

### Documentation sur les services

Les informations sur les services ont été améliorées afin d'identifier facilement le support du service en fonction du numéro d'édition dans lequel il est disponible.

Pour plus d'informations, voir les rubriques suivantes :

* [Services disponibles pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)
* [Services disponibles pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Services disponibles pour les instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices#available-services-for-cloud-foundation-instances)

## Améliorations et mises à jour apportées à l'interface utilisateur

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Si votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) est lié à votre compte {{site.data.keyword.cloud_notm}}, vous pouvez désormais cliquer sur le nouveau bouton **Extraire** sur la page **Paramètres** afin d'obtenir automatiquement le nom d'utilisateur et la clé d'API pour votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer).
* Un nouvel onglet **Historique de déploiement** a été ajouté dans le panneau de navigation de gauche de la page des détails d'instance pour vous permettre de vérifier l'historique de déploiement d'une instance.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

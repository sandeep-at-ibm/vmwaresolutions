---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 2.2
{: #relnotes_v22}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown

{{site.data.keyword.vmwaresolutions_short}} a publié des modules de correction depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Pour plus d'informations, voir [Résolution des vulnérabilités Spectre et Meltdown](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_fix_spectre).

## Mise à niveau de la machine virtuelle IBM CloudDriver

Lors de la procédure de mise à niveau vers la version 2.2, la machine virtuelle IBM CloudDriver est redéployée avec l'édition CentOS Linux 7.4.1708. De plus, toutes les nouvelles instances mises à disposition incluent l'édition CentOS Linux 7.4.1708 sur IBM CloudDriver.

**Important :**

* Si vous utilisez une solution de sauvegarde qui référence la machine virtuelle IBM CloudDriver, après mise à niveau vers la version 2.2, vérifiez que la solution de sauvegarde référence la nouvelle machine virtuelle IBM CloudDriver.
* Avant d'effectuer une mise à niveau vers la version 2.2, vérifiez que vous avez remplacé l'instance de serveur virtuel Veeam existante par le service Veeam on {{site.data.keyword.cloud_notm}}. L'instance de serveur virtuel Veeam existante n'est plus prise en charge en version 2.2 et dans les versions ultérieures, de sorte que les sauvegardes de composant de gestion associées à l'instance de serveur virtuel Veeam existante ne sont pas disponible pour une restauration.

Pour plus d'informations sur l'utilisation du service Veeam sur {{site.data.keyword.cloud_notm}}, voir les rubriques suivantes :
* [Composants et remarques pour Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Paramètres de configuration avancée sur les serveurs ESXi

Pour la version 2.2 ou des éditions ultérieures, les nouvelles instances sont commandées avec un nouveau jeu de paramètres de configuration avancée pour les serveurs ESXi.
Pour les instances mises au niveau depuis une édition antérieure vers la version 2.2 ou des éditions ultérieures, certains paramètres nécessitent un réamorçage des serveurs ESXi. Par conséquent, seul un sous-ensemble des paramètres de configuration est appliqué automatiquement.

Il est recommandé de modifier les paramètres de configuration restants avec les nouvelles valeurs afin de garantir la cohérence entre toutes les instances et permettre la prise en charge de l'extension de stockage. IBM prévoit de n'effectuer ses tests qu'avec ces nouvelles valeurs pour toutes les éditions ultérieures des solutions {{site.data.keyword.cloud_notm}} pour VMware.

Pour plus d'informations, voir _Paramètres de configuration avancée pour les serveurs ESXi_ dans :
* [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers)
* [Nomenclature de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom#advanced-configuration-settings-for-esxi-servers)

## Prise en charge de 51 serveurs ESXi pour un cluster initial et de 59 serveurs ESXi pour les clusters additionnels

Pour la version 2.2 et éditions ultérieures, vous pouvez désormais augmenter le nombre de serveurs ESXi jusqu'à un maximum de 51 pour un cluster initial et jusqu'à 59 pour les clusters additionnels.

Pour les instances déployées dans la version 2.1 ou des éditions antérieures, vous devez activer la prise en charge vSAN nécessaire pour augmenter la taille du cluster au-delà de 32 éléments. Pour plus d'informations sur la procédure à suivre pour augmenter le nombre de serveurs ESXi, voir _Combien de serveurs ESXi puis-je ajouter à un cluster ?_ dans la [Foire aux questions sur les serveurs ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## Autres options de configuration réseau pour les instances vCenter Server et Cloud Foundation

Pour les commandes d'instance vCenter Server et Cloud Foundation, vous pouvez désormais réutiliser les VLAN publics et privés existants pour votre configuration réseau. Lorsqu'aucun VLAN existant n'est disponible, vous pouvez commander un nouveau VLAN public et deux nouveaux VLAN privés.

Pour prendre connaissance des remarques importantes à connaître avant de sélectionner des VLAN existants, voir les sections *Paramètres d'interface réseau* dans :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)

## Mises à jour des instances VMware vCenter Server

### Mises à jour des paramètres de configuration du composant NSX et du groupe de ports

L'édition actuelle s'applique à la mise à jour du composante VMware NSX pour vSphere 6.3.5. Pour plus d'informations sur les composants, voir [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Pour les instances VMware vCenter Server déployées dans la version 2.2 ou des éditions ultérieures, les paramètres de configuration de NSX et du groupe de ports ont été modifiés. Pour plus d'informations, voir la section *Paramètres de configuration de NSX et du groupe de ports* dans la [nomenclature du logiciel vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings).

### Nouvelle option de configuration pour DNS

Vous pouvez désormais sélectionner le déploiement d'une seule instance de serveur virtuel Microsoft Windows pour Microsoft Active Directory (AD) ou de deux machines virtuelles à haute disponibilité Microsoft Windows dans le cluster de gestion. Pour les éditions antérieures à la version 2.2, l'unique instance de serveur virtuel Microsoft Windows pour Microsoft AD a été automatiquement déployée par défaut. La nouvelle option de sélection de deux machines virtuelles Microsoft Windows améliore la confidentialité et fournit une option permettant de sauvegarder et restaurer les machines virtuelles qui utilisent le service Veeam.

Vous devez fournir 2 licences Microsoft Windows Server 2012 R2 si vous configurez votre instance de manière à utiliser les deux machines virtuelles Microsoft Windows. Utilisez la licence d'édition Microsoft Windows Server 2012 R2 Standard et/ou la licence d'édition Microsoft Windows Server 2012 R2 Datacenter. Vous disposez de 30 jours pour activer les machines virtuelles.
{:note}

Pour plus d'informations, voir la section *Paramètres de configuration du système* dans [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings)​.

### Augmentation du nombre de clusters par instance

Vous pouvez désormais ajouter jusqu'à 10 clusters aux instances VMware vCenter Server déployées dans (ou mises à niveau vers) la version 2.2. et dans des éditions ultérieures. Pour plus d'informations, voir [Ajout et affichage des clusters des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)​.

## Mises à jour des clusters VMware vSphere

### Offres groupées de licence de composant disponibles pour les partenaires commerciaux

Les partenaires commerciaux ont désormais le choix entre quatre offres groupées de licence de composant lorsqu'ils commandent un nouveau cluster vSphere. Les choix possibles sont les suivants : Standard with Management, Advanced, Advanced with Networking ou Advanced with Networking and Management. Vous pouvez également inclure des composants VMware supplémentaires dans votre commande. Le mode BYOL (Bring Your Own License) n'est toutefois pas disponible.

Pour plus d'informations, voir la section *Paramètres d'octroi de licence* dans la rubrique [Commande de nouveaux clusters vSphere ](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Mises à jour des instances NetApp ONTAP Select

L'édition actuelle applique la mise à jour de NetApp ONTAP Select 9.3.

### Augmentation du nombre d'unités SATA pour les serveurs bare metal IBM Cloud à haute disponibilité

Trente quatre unités SATA sont désormais disponibles pour les serveurs {{site.data.keyword.baremetal_short}} NetApp ONTAP Select à haute disponibilité. Pour plus d'informations, voir [Spécifications techniques relatives aux instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#technical-specifications-for-netapp-ontap-select-instances).

## Mises à jour apportées aux services complémentaires

### Option d'augmentation de la bande passante pour F5 on IBM Cloud

Vous pouvez désormais sélectionner une bande passante atteignant 10 Gbps lors de l'installation du service F5 on {{site.data.keyword.cloud_notm}} pour les instances Cloud Foundation et vCenter Server. Pour plus d'informations, voir [Remarques relatives à F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).

### KMIP for VMware on IBM Cloud

Vous pouvez désormais commander une instance Cloud Foundation ou vCenter Server avec le service KMIP for VMware on {{site.data.keyword.cloud_notm}} inclus ou ajouter le service à une instance Cloud Foundation ou vCenter Server existante après le déploiement initial.

Ce service offre une haute disponibilité en 24/7 permettant de gérer les clés de chiffrement qu'utilise VMware dans {{site.data.keyword.cloud_notm}}. Il propose une fonction d'exécution qui permet aux clients de créer, extraire, activer, révoquer et supprimer des clés de chiffrement. Il offre également une fonction de gestion des associations entre les données d'identification du client et ces clés de chiffrement.

Pour plus d'informations, voir [Remarques relatives à KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### IBM Spectrum Protect Plus on IBM Cloud

Le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures.

Ce service fournit une solution évolutive et efficace de protection, de réutilisation et de récupération des données pour les environnements virtuels. Vous pouvez l'implémenter en tant que solution autonome ou vous pouvez l'intégrer à votre environnement IBM Spectrum Protect&trade; Plus pour décharger des copies de stockage à long terme et pour la gouvernance des données.

Le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fournit une protection des données uniquement pour les machines virtuelles de charge de travail.

Pour plus d'informations, voir [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp).

### Services gérés

Des services gérés pour Veeam on {{site.data.keyword.cloud_notm}} et pour Zerto on {{site.data.keyword.cloud_notm}} sont désormais disponibles pour les instances VMware vCenter Server et VMware Cloud Foundation. Demandez ces services gérés si vous ne voulez pas avoir à gérer la complexité de votre propre solution et de votre propre environnement.

Le service Veeam on {{site.data.keyword.cloud_notm}} s'intègre en toute transparence à vos hyperviseurs VMware afin d'aider votre entreprise à obtenir la haute disponibilité requise. Un environnement de sauvegarde totalement gérée peut être déployé à l'aide du logiciel de sauvegarde Veeam et d'IBM Resiliency Backup as a Service.

Le service Zerto on {{site.data.keyword.cloud_notm}} fournit des fonctions de réplication et de reprise après incident, qui peuvent être intégrées aux offres de déploiement de manière à assurer la protection et la récupération des données dans votre environnement virtuel VMware sur {{site.data.keyword.cloud_notm}}. Un environnement de reprise après incident totalement gérée peut être déployé à l'aide du logiciel Zerto DR et des services IBM Resiliency Services.

Vous pouvez demander des services gérés pour vos instances à partir de la page **Initiation**, soit en passant une nouvelle commande d'instance, soit en ajoutant le service à une instance existante.

Pour plus d'informations, voir les rubriques suivantes :
* [Demande de services pour Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Demande de services pour Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## Documentation nouvelle et mise à jour

* La documentation intègre désormais un tableau de comparaison des fonctions prises en charge pour les instances Cloud Foundation et vCenter Server, et pour les clusters VMware vSphere. D'un seul coup d'oeil, vous pouvez voir les différences entre les fonctions que chaque type d'instance fournit. Pour plus d'informations, voir [Graphique de comparaison des offres](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

* La documentation contient désormais la nomenclature des VLAN et des logiciels pour les clusters Cloud Foundation, vCenter Server et VMware vSphere.

  Pour plus d'informations, voir les rubriques suivantes :

  * [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [Nomenclature de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
  * [Nomenclature de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## Améliorations et mises à jour apportées à l'interface utilisateur

Des améliorations ont été apportées à l'interface utilisateur, à savoir :

* Lorsque vous commandez une instance, toutes les options de matériel sont désormais filtrées par emplacement et les options non disponibles s'affichent comme étant désactivées.
* La configuration des serveurs **{{site.data.keyword.baremetal_short}}** est désormais automatiquement renseignée lorsque vous commandez un cluster vSphere basé sur des configurations existantes. Vous pouvez mettre à jour la configuration en fonction de vos besoins.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notes sur l'édition pour la version 2.9
{: #relnotes_v29}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

Cette édition introduit l'offre VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T en tant qu'offre de test de démonstration de faisabilité ou de bac à sable. vCenter Server with NSX-T est un cloud hébergé privé qui vous permet d'expérimenter la plateforme de mise en réseau VMware de génération suivante, NSX-T.

Pour plus d'informations, voir les rubriques suivantes :

* [Présentation de vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [Commande d'instances vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Fin de la prise en charge de VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

Afin de consolider nos offres pour une meilleure expérience client, {{site.data.keyword.cloud_notm}} a décidé de cesser la prise en charge de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} à compter du 13 mai 2019.    
Ainsi, tous les clients seront dirigés vers VMware vCenter Server on {{site.data.keyword.cloud_notm}}, qui offre davantage de souplesse grâce à des options de stockage et d'octroi de licence.   
Une assistance sera fournie aux clients existants qui utilisent VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} afin de les aider à migrer vers VMware vCenter Server on {{site.data.keyword.cloud_notm}} avant la date de fin de la prise en charge fixée au 13 mai 2019. 

Après le 13 mai, les fonctions de gestion pour VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} seront retirées de la console {{site.data.keyword.vmwaresolutions_short}}. Les instances qui n'auront pas été migrées vers VMware vCenter Server on {{site.data.keyword.cloud_notm}} ne seront pas accessibles via la console d'infrastructure IBM Cloud. 

Les clients seront contactés par le support {{site.data.keyword.cloud_notm}} avant le 25 mars 2019 pour commencer la migration à partir de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}. Pour plus d'informations sur les options de migration pour les clients existants, voir la [page wiki {{site.data.keyword.vmwaresolutions_short}}](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}.
 
Les clients peuvent afficher leur instance VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} existante sur la[console {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted).

## Prise en charge de VMware vSphere 6.7 Update 1
{: #relnotes_v29-vsphere}

Vous avez désormais la possibilité de commander VMware vSphere version 6.7 Update 1 avec vos instances VMware vCenter Server, VMware vCenter Server with Hybridity Bundle et VMware vSphere on {{site.data.keyword.cloud_notm}}. 

De plus, les instances Version d'essai à noeud unique pour la migration et la modernisation des applications sont désormais commandées avec vSphere Enterprise Plus 6.7u1.


vSphere Enterprise Plus 6.7u1 est disponible uniquement pour les serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell et Skylake. 

Pour plus d'informations, voir les sections _Paramètres de licence_ dans les rubriques suivantes :

* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Fin de la prise en charge du spanning VLAN
{: #relnotes_v29-vlan}

A compter d'août 2019, le spanning VLAN ne sera plus pris en charge par {{site.data.keyword.vmwaresolutions_short}}. D'ici la fin juillet 2019, vous devez convertir votre compte d'infrastructure {{site.data.keyword.cloud_notm}} en un compte VRF et activer les points finaux de service pour votre compte.


Pour plus d'informations, voir :

* [Aperçu du service Routage et transfert virtuel (VRF) on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Activation de votre compte pour l'utilisation des noeuds finaux de service à l'aide de l'interface CLI IBM Cloud](/docs/services/service-endpoint?topic=services/service-endpoint-cs_cli_install_steps)

## Prise en charge d'API
{: #relnotes_v29-api}

Des API sont désormais disponibles pour le déploiement d'instances, la suppression d'instances et l'ajout ou le retrait de serveurs ESXi et de clusters.

La documentation API REST est également disponible dans la section *Référence* de la documentation utilisateur. Pour plus d'informations, voir [API {{site.data.keyword.vmwaresolutions_short}}](https://console.bluemix.net/apidocs/vmware-solutions).

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v29-vcs}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.7 Update 1 (build 6.7.0-11675023)
* vSphere ESXi 6.5 Update 2 (build 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (build 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (build 11197766)
* NSX-T for vSphere 2.4

Pour plus d'informations sur la sélection de vos composants VMware, voir [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Améliorations apportées au serveur ESXi
{: #relnotes_v29-vcs-esxi}

* Le protocole SSH (Secure Shell) est désormais désactivé pour les serveurs ESXi avant la distribution d'instance. 
* A compter de l''édition V2.9, les opérations de serveur ESXi suivantes seront disponibles :

   * Ajout de nouveaux serveurs ESXi à un cluster existant tandis que ces serveurs sont en mode maintenance. Les machines virtuelles ne sont pas migrées vers les nouveaux serveurs tant que le mode maintenance n'est pas désactivé. 
   * Ajout ou retrait simultané de serveurs ESXi sur plusieurs clusters dans votre instance. 

Pour plus d'informations, voir [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

### Taille du stockage NFS (Network File System)
{: #relnotes_v29-vcs-nfs}

Pour les commandes d'instance vCenter Server, vous pouvez désormais ajouter jusqu'à 24 To de stockage NFS pour les niveaux de performance 0,25, 2, et 4 IOPS/Go.

Le niveau de performance 10 IOPS/Go est toujours limité à une capacité maximale de 4 To par partage de fichiers. {:note}

## Mises à jour apportées aux services complémentaires
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

Le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware vCenter Server qui sont déployées dans, ou mises à niveau vers, la version 2.9 ou des éditions ultérieures. Ce service peut vous aider à gérer la cybersécurité et le risque de conformité à l'aide de contrôles de surveillance proactive et de défense automatisée destinés à assurer une protection contre les menaces et à permettre la conformité aux réglementations de l'industrie et du gouvernement. 

Vous pouvez commander des instances vCenter Server avec le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances vCenter Server existantes à partir de l'onglet **Services** de la page des détails d'instance.

Vous pouvez également commander une licence Caveonix RiskForesight autonome sans l'associer à une instance VMware pour l'octroi de licence et l'activation de vos charges de travail locales. 

Pour plus d'informations, voir :
* [Remarques relatives à Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Commande de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Remarques relatives aux licences Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Commande de licences Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

Dans l'édition en cours, F5-BigIP VE V14.1.0.2 est installé sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de F5-BigIP VE V14.1.0.2, voir [Release Note: BIG-IP 14.1.0 New and Installation](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

Dans l'édition en cours,  HyTrust CloudControl 5.4.2 est installé sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de HyTrust CloudControl 5.4.2, voir [HyTrust CloudControl Release Notes Version 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Deux nouveaux noeuds finaux sont désormais disponibles à Sydney pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Configuration du service KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config).

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

Dans l'édition en cours, Veeam Backup and Replication 9.5 Update 4 est installé sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de Veeam 9.5u4, voir [Release information for Veeam Backup and Replication 9.5 Update 4](https://www.veeam.com/kb2878){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

Dans l'édition en cours, Zerto Virtual Replication 6.5 update 3 est installé sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonction de Zerto Virtual Replication 6.5 update 3, voir [Release notes for Zerto Virtual Replication V6.5 Update 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}.

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v29-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Sur la page **Infrastructure**, un nouveau tableau **Interface réseau** contient des détails de réseau VLAN, de sous-réseau et d'adresse IP pour votre cluster. 
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

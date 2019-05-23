---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notes sur l'édition pour la version 3.0
{: #relnotes_v30}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composants, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir une liste des problèmes corrigés dans les différentes versions, des problèmes connus avec le produit ainsi que des conseils pour utiliser {{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Fin de la prise en charge de VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

Afin de consolider nos offres pour garantir une meilleure expérience client, la plateforme {{site.data.keyword.vmwaresolutions_short}} cessera la commercialisation de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} à compter du 13 mai 2019.

Tous les clients seront désormais dirigés vers VMware vCenter Server on {{site.data.keyword.cloud_notm}}, notre solution phare de centre de données VMware défini par logiciel sur les serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Les clients existants qui utilisent VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} bénéficieront d'une assistance pour la conversion vers VMware vCenter Server on {{site.data.keyword.cloud_notm}} dès le 13 mai 2019, date de la fin de prise en charge.

Après le 13 mai, les capacités de gestion de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} seront gelées dans la console {{site.data.keyword.vmwaresolutions_short}} jusqu'à leur conversion à VMware vCenter Server on {{site.data.keyword.cloud_notm}}. Les clients qui ne souhaitent pas faire migrer leur instance VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} vers VMware vCenter Server on {{site.data.keyword.cloud_notm}} peuvent accéder à leurs instances depuis la console d'infrastructure {{site.data.keyword.cloud_notm}}.

## Suppression de la prise en charge des serveurs Broadwell à 2 unités centrales
{: #relnotes_v30-broadwell}

Depuis la version V3.0, les serveurs Broadwell à 2 unités centrales ne peuvent plus être déployés pour les nouvelles instances et les nouveaux clusters de vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server with NSX-T et vSphere on {{site.data.keyword.cloud_notm}}. Vous pouvez continuer d'ajouter des serveurs aux clusters existants.

## Améliorations du fonctionnement du système de fichiers réseau
{: #relnotes_v30-nfs}

A compter de l'édition V3.0, vous pouvez ajouter ou retirer simultanément le stockage NFS et des serveurs ESXi sur des clusters qui sont à l'état **Prêt à l'emploi**. Par exemple, vous pouvez ajouter ou retirer un serveur ESXi dans un cluster et ajouter ou retirer le stockage NFS dans un autre cluster. Cela s'applique à toutes les instances de vCenter Server et de vCenter Server with NSX-T.

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v30-vcs}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.7, mise à jour 1 (build 6.7.0-13004448)
* vSphere ESXi 6.5, mise à jour 2 (build 6.5.0-13004031)
* vCenter Server Appliance 6.7, mise à jour 1b (build 6.7.0-11727113)
* Platform Services Controller 6.7, mise à jour 1b (build 6.7.0-11727113) 

Pour plus d'informations, voir [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Le logiciel Windows commandé pour les services Microsoft Active Directory (AD) et DNS (Domain Name System) est mis à niveau vers Windows Server 2016 pour les deux options de configuration suivantes : les instances de serveur virtuel (VSI) et les deux machines virtuelles Windows à haute disponibilité. Pour en savoir plus sur la sélection de vos composants, voir [Nomenclature logicielle pour les instances vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### Amélioration du stockage vSAN
{: #relnotes_v30-vcs-vsan}

* Lorsque vous utilisez le stockage vSAN, le nombre de serveurs Bare Metal que vous pouvez commander peut désormais être supérieur à quatre. Cela s'applique à toutes les instances vCenter Server, vCenter Server with Hybridity et vCenter Nerver with NSX-T.
* A partir de la version V3.0, une unité SSD M.2 est commandée avec votre instance de stockage vSAN. Vous pouvez commander jusqu'à 10 disques de capacité ou un total de 12 disques de capacité si vous sélectionnez l'option **Hautes performances avec Intel Optane**.

Pour plus d'informations, voir la section *Paramètres de stockage* dans :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [Commande d'instances vCenter Server with NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Mises à jour apportées aux services complémentaires
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

Dans l'édition en cours, HyTrust CloudControl 5.5 est installé sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de HyTrust CloudControl 5.5, voir [What's New in HyTrust CloudControl Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

L'édition en cours installe HyTrust DataControl 4.3 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de HyTrust DataControl 4.3, voir [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

L'édition en cours installe HyTrust KeyControl 4.3 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions de HyTrust KeyControl 4.3, voir [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

L'édition en cours installe {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 avec {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 sur toutes les instances nouvellement déployées.

Pour plus d'informations sur les nouvelles fonctions de {{site.data.keyword.cloud_notm}} Private v3.1.2, voir [Nouveautés de {{site.data.keyword.cloud_notm}} Private v3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
Pour plus d'informations sur les nouvelles fonctions de {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, voir [Nouveautés de {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Deux nouveaux noeuds finaux sont désormais disponibles à Londres et dans la région Est des Etats-Unis pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Configuration du service KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

L'édition en cours installe IBM Spectrum Protect™ Plus V10.1.3 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.3, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

Vous pouvez désormais ajouter Zerto on {{site.data.keyword.cloud_notm}} sur des instances uniquement privées. Si vous choisissez d'installer Zerto sur des instances uniquement privées, vous devez configurer votre propre serveur proxy ainsi que la fonction Call Home pour Zerto. Pour plus d'informations, voir [Commande de Zerto on {{site.data.keyword.cloud_notm}} pour les instances appartenant uniquement au réseau privé](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## Documentation nouvelle et mise à jour

* Une documentation est désormais disponible pour vous aider à mettre à niveau les composants {{site.data.keyword.vmwaresolutions_short}} vers VMware vSphere 6.7. Cette mise à niveau est nécessaire si vous voulez continuer de bénéficier de l'automatisation {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Mise à niveau du logiciel vCenter Server vSphere de VMware vSphere 6.5 à 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* Une documentation de référence est maintenant disponible pour vous fournir les identifiants utilisateur que {{site.data.keyword.vmwaresolutions_short}} maintient pour une utilisation par l'automatisation {{site.data.keyword.cloud_notm}}. Vous pouvez également consulter les éventuels messages qui s'affichent dans les journaux d'historique de votre instance. Pour plus d'informations, voir [ID utilisateur IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) et  [Messages de l'historique d'instance](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* L'autorisation **Reboot/Control** a été ajoutée au tableau décrivant les autorisations requises pour le compte d'infrastructure IBM Cloud. Pour plus d'informations, voir [Autorisations pour le compte d'infrastructure {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions).
* Une nouvelle documentation de référence est disponible pour les API suivantes. Pour plus d'informations, voir [API reference](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * Répertorier tous les messages d'historique pour une instance VMware vCenter Server spécifiée
  * Ajouter des stockages partagés à un cluster spécifié
  * Supprimer les stockages NFS d'un cluster spécifié

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v30-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notes sur l'édition pour la version 3.1
{: #relnotes_v31}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Instances Single-node Trial for Data Protection and Disaster Recovery
{: #relnotes_v31-dr-bundle}

Single-node Trial for Data Protection and Disaster Recovery est un moyen rapide de tester le lecteur {{site.data.keyword.cloud_notm}} pour migrer et récupérer les charges de travail VMware dans {{site.data.keyword.cloud_notm}}. Cette version d'évaluation est une version de VMware vCenter Server sur IBM Cloud, une plateforme VMware à service exclusif pouvant être gérée à l'aide des mêmes outils courants que les environnements sur site. Cette version d'évaluation inclut les services Veeam sur {{site.data.keyword.cloud_notm}}, VMware HCX sur {{site.data.keyword.cloud_notm}} et Zerto sur {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir [Présentation de Single-node Trial for Disaster Recovery](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview).

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

Vous pouvez désormais faire appel à IBM Expert Services pour travailler avec votre équipe interne afin de déployer, migrer et gérer votre propre solution {{site.data.keyword.cloud_notm}}, de la planification à la modernisation, ou à n’importe quel stade intermédiaire. 

Vous pouvez ajouter {{site.data.keyword.cloud_notm}} Expert Services à votre commande d'instance à tout moment en demandant une consultation à partir de la page **Getting Started**. Pour plus d'informations, voir [Demande d'{{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices).

## Intégration à l'Estimateur de coût IBM Cloud 

Vous pouvez maintenant estimer le coût de vos ressources {{site.data.keyword.vmwaresolutions_short}} dans l'outil d'estimation unifié fourni par la structure {{site.data.keyword.cloud_notm}}. Avec cette fonction, vous pouvez enregistrer un instantané des ressources dans {{site.data.keyword.cloud_notm}} Catalog et les stocker dans un seul fichier PDF que vous pouvez télécharger pour le consulter ultérieurement. L'estimateur de coût n'est pas un contrat ou un devis ferme, mais seulement une estimation de votre coût total.

Pour plus d'informations sur l'estimateur de coûts, voir [Estimation des coûts](/docs/billing-usage?topic=billing-usage-cost).

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v31-vcs}

Cette version applique les mises à niveau et améliorations suivantes pour les instances, clusters et hôtes récemment déployés :

* vSphere ESXi 6.5 Update 2 (build 6.5.0-13635690)
* vCenter Server Appliance 6.5 Update 2g (build 6.5.0-13638625)

Pour plus d'informations, voir [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Configuration alternative du serveur ESXi pour les clusters 
{: #relnotes_v31-esxi-config}

Vous pouvez maintenant ajouter de nouveaux serveurs ESXi à un cluster existant en sélectionnant une configuration existante ou une autre configuration que les hôtes existants du cluster. Lorsque vous commandez de nouveaux serveurs à partir de la fenêtre **Ajout de serveur**, vous pouvez sélectionner instantanément une configuration existante dans le cluster ou choisir une nouvelle configuration de	{{site.data.keyword.baremetal_short_sing}}. Cela s'applique à toutes les instances vCenter Server, vCenter Server with Hybridity et vCenter Nerver with NSX-T.

Pour éviter les problèmes de performances ou de stabilité, il est recommandé que les clusters utilisent la même configuration ou une configuration similaire en ce qui concerne le processeur, la mémoire vive et le stockage. Cette fonctionnalité est utile pour les mises à jour matérielles au sein du même cluster.

Pour plus d'informations, voir [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers).

### Mises à jour des configurations de règles
{: #relnotes_v31-policy-config}

Le mot de passe vCenter généré pour les instances principales de vCenter Server est maintenant composé de 15 caractères et comporte les configurations de règles de mot de passe et de verrouillage suivantes : 

* La longueur minimale de règle de mot de passe vCenter est maintenant de 15 caractères. 
* La règle de verrouillage de vCenter autorise désormais un maximum de 3 tentatives de connexion infructueuses. 
* La règle de verrouillage de vCenter autorise désormais un intervalle de temps de 900 secondes entre les échecs. 

Le mot de passe NSX Manager généré pour les instances principales de vCenter Server est maintenant composé de 15 caractères. Auparavant, le mot de passe généré comportait huit caractères. 

 Pour plus d'informations, voir [Informations de conformité relatives aux instances vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config).

## Mises à jour apportées aux services complémentaires
{: #relnotes_v31-services}

### Renouvellement automatique des licences HyTrust 
{: #relnotes_v31-services-ht}

{{site.data.keyword.vmwaresolutions_short}} prend désormais en charge le renouvellement automatique des licences HyTrust pour lesquelles la fonctionnalité Call Home est activée. Ce support est fourni à partir de : 

* HyTrust CloudControl 5.5.1 et versions ultérieures
* HyTrust DataControl 4.3.2 et versions ultérieures
* HyTrust KeyControl 4.3.2 et versions ultérieures

Vous devez effectuer la procédure permettant d'activer l'accès à Internet pour vos machines virtuelles (VM) HyTrust afin de garantir le renouvellement automatique de votre licence. Si vous n'effectuez pas cette procédure, votre licence expire chaque année.
{:important}

Pour plus d'informations, voir :

* [Activation de l'accès Internet pour les VM HyTrust CloudControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [Activation de l'accès Internet pour les VM HyTrust DataControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [Activation de l'accès Internet pour les VM HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

Dans la version actuelle, Veeam Availability Suite 9.5 est installé sur toutes les instances récemment déployées. De plus, un certain nombre de mises à jour sont apportées aux référentiels de configuration Veeam VSI et Veeam. Pour plus d'informations, voir [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations).

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

Pour les nouvelles instances déployées à partir de V3.1, les installations de Zerto on {{site.data.keyword.cloud_notm}} nécessitent un compte {{site.data.keyword.cloud_notm}} payant. Le coût de la réplication de la machine virtuelle utilise désormais un forfait payant {{site.data.keyword.cloud_notm}} au lieu de la facturation de l'infrastructure {{site.data.keyword.cloud_notm}}. 

Pour commander Zerto sur {{site.data.keyword.cloud_notm}}, votre compte {{site.data.keyword.cloud_notm}} doit répondre à des exigences spécifiques. Si vous disposez d'une installation Zerto on {{site.data.keyword.cloud_notm}} existante, vous pouvez convertir le type de facturation de VM Zerto en type facturable. Pour plus d'informations, voir [Facturation pour la réplication Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).

## Documentation nouvelle et mise à jour
{: #relnotes_v31-updated-doc}

* Les événements de gestion d'instance Activity Tracker et les événements pour le service KMIP for VMware sur IBM Cloud sont mis à jour. Pour plus d'informations, voir [Evénements Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).
* La documentation de référence sur l'ID utilisateur est mise à jour avec les ID utilisateur utilisés pour l'installation et la configuration des services par l'automatisation des services {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir la section *ID utilisateur du service* dans [ID utilisateur IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).
* Une documentation de référence est disponible pour la nouvelle API ``Retrieve the detailed network interface of a cluster``. Pour plus d'informations, voir [API reference](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
* Les documents techniques suivants sont nouveaux dans la section *Référence* de la documentation utilisateur :
  * [Gestion des opérations](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Procédures opérationnelles du jour 2](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v31-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :
* La page de détails **Clusters** affiche désormais le type de stockage utilisé par le cluster. 
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

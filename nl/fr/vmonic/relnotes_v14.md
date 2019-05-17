---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-08"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 1.4
{: #relnotes_v14}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Mises à jour de composants pour les instances Cloud Foundation
{: #relnotes_v14-vcf-comp}

Les composants suivants sont nouveaux ou ont été mis à jour :

* VC et PSC (vCenter et Platform Services Controller) 6.0U2a
* Outils VMware 10.1.0
* Gestionnaire SDDC (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Une instance de serveur virtuel Windows a été commandée pour les services Microsoft Active Directory (AD) et DNS (Domain Name System) requis pour la prise en charge des configurations multisite dans cette édition. Les spécifications de cette instance de serveur virtuel sont les suivantes : Windows 2012 R2 (8 Go de RAM / 2 coeurs d'UC / disque de 100 Go / liaisons montantes privées doubles de 1 Gbps).

## Mises à jour de composants pour les instances vCenter Server
{: #relnotes_v14-vcs-comp}

Les composants suivants sont nouveaux ou ont été mis à jour :

### VMware NSX for vSphere 6.2.4
{: #relnotes_v14-nsx}

VMware NSX for vSphere 6.2.4 est désormais installé par défaut sur toutes les instances vCenter Server (uniquement les instances sur Cloud Foundation précédemment).

Dans le cadre de l'installation de NSX, NSX Manager est installé et sous licence sur toutes les nouvelles instances déployées. De plus, un composant NSX Edge est créé pour la gestion des instances, mais vous pouvez, au besoin, créer vos propres composants NSX Edge. Pour plus d'informations sur le composant NSX Edge, voir la section _VMware NSX Edge_ sur cette page.

Le contrôleur NSX n'est pas installé sur les instances vCenter Server (comme il l'est sur les instances Cloud Foundation). Si vous utilisez VXLAN ou des routeurs logiques distribués pour vos instances vCenter Server, alors vous devez installer vous-même le contrôleur NSX.
{:note}

Pour plus d'informations sur les améliorations apportées à VMware NSX for vSphere 6.2.4, ses exigences et ses problèmes connus, voir [Notes sur l'édition pour NSX for vSphere 6.2.4](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge
{: #relnotes_v14-nsx-edge}

NSX Edge est désormais inclus dans les nouvelles commandes d'instance vCenter Server. NSX Edge offre des services de passerelle et de sécurité périphériques permettant d'isoler un réseau virtuel.

Lors du déploiement d'une instance, IBM déploie une passerelle VMware NSX ESG (Edge Services Gateway) de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation. La passerelle ESG est déployée de manière à inclure deux interfaces : une pour la connexion au réseau local virtuel {{site.data.keyword.cloud_notm}} privé et l'autre pour la connexion au réseau local virtuel {{site.data.keyword.cloud_notm}} public.

Pour garantir la sécurité, des règles de pare-feu sont instaurées afin d'autoriser uniquement les communications HTTPS sortantes initiées par les machines virtuelles de gestion. Cette passerelle ESG est déployée dans une Grande configuration et seul le support IBM est habilité à modifier la configuration. Pour plus d'informations, voir les rubriques suivantes :

* [Spécifications techniques de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)
* [La passerelle NSX Edge des services de gestion présente-t-elle un risque pour la sécurité ?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentation VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### Licence NSX
{: #relnotes_v14-nsx-license}

Une licence VMware NSX Base for Service Providers Edition par noeud est commandée.

### Nouveau bloc d'adresses de sous-réseau
{: #relnotes_v14-subnet}

Un bloc de sous-réseau de 16 adresses portables publiques par noeud est commandé.

## Mises à jour du modèle de frais de service
{: #relnotes_v14-svc-charge}

Le modèle de frais de service a été simplifié :

* Pour les instances Cloud Foundation, aucun frais n'est perçu pour l'_instance de service VMware Cloud Foundation_, le _service de stockage VMware Cloud Foundation_ et
   _VMware Solutions Hypervisor_.
* Pour les instances vCenter Server, aucun frais n'est perçu pour l'_instance VMware vCenter Server_ et _VMware Solutions Hypervisor_.
* Pour les deux types d'instance, une nouvelle charge pour _Support et Services_ a été instaurée. Elle est appliquée à chaque noeud et perçue mensuellement.

## Mises à jour de la topologie de réseau des instances
{: #relnotes_v14-netwok-topo}

Cette édition inclut les améliorations de topologie suivantes pour vos instances :

* Pour les instances Cloud Foundation et vCenter Server : configuration de réseau optimisée, à savoir que seules les adresses IP publiques et privées principales affectées par SoftLayer® sont associées aux serveurs ESXi. Les adresses privées portables ne sont plus déployées pour le trafic de gestion.
* Pour les instances Cloud Foundation uniquement : connexion unique Windows AD (Active Directory) et serveur de noms de domaine (DNS, Domain Name System)

En raison de ces modifications, vous ne pouvez pas utiliser vos instances existantes de version antérieure à 1.4 dans l'édition actuelle. Pour réutiliser la configuration vos instances existantes, vous devez procéder à leur mise à niveau vers la version actuelle.
{:note}

## Prise en charge de configuration multisite pour des instances Cloud Foundation
{: #relnotes_v14-vcf-multisite}

Vous pouvez désormais déployer soit une instance unique Cloud Foundation, comme dans les éditions précédentes, ou déployer en plus des instances secondaires associées à l'instance principale. Le modèle de configuration multisite utilise un concentrateur et une topologie en étoile (hub and spoke) avec un site principal et un maximum de sept sites secondaires.

## Améliorations au niveau du déploiement de la reprise après incident Zerto
{: #relnotes_v14-zerto}

* Pour les instances Cloud Foundation, le déploiement de la reprise après incident Zerto est automatisé et non géré via un ticket de demande de service. Tous les composants Zerto, tels qu'un sous-réseau portable privé, une instance de service virtuel Windows et les frais de licence Zerto sont répertoriés dans le coût estimé, de sorte que vous pouvez les vérifier avant de commander.
* Pour les instances vCenter Server, le déploiement de la reprise après incident Zerto s'effectue via un ticket de demande de service, comme dans l'édition précédente. Cependant, NSX Edge et le sous-réseau portable public ne sont plus nécessaires puisqu'ils sont désormais inclus dans le déploiement de base. Les frais afférents à un sous-réseau portable privé, une instance de service virtuel Windows et à la licence Zerto sont toujours applicables.

Pour plus d'informations, voir [Reprise après incident Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

## Processus de commande d'instance
{: #relnotes_v14-inst-order}

Le processus de commande d'instance a été grandement simplifié :

* Pour les instances Cloud Foundation et vCenter Server, la page des données d'identification SoftLayer ne s'affiche plus pendant le processus de commande. Les données d'identification SoftLayer définies sur la page Paramètres sont utilisée par défaut et vous n'êtes invité à les mettre à jour que si vous ne répondez pas aux exigences.
* De plus, pour les instances vCenter Server, seule l'option **Grande** du type **Matériel** et le paramètre **Double 10 Gbps** de **Vitesse de port de liaison montante** sont désormais disponibles, ce qui réduit le nombre de paramètres à renseigner lors de la commande.

Pour plus d'informations, voir [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Gestion d'instances
{: #relnotes_v14-inst-mgmt}

De nouvelles fonctions et améliorations ont été apportées au processus de gestion des instances :

* Pour les instances Cloud Foundation, vous pouvez afficher le nom d'utilisateur et les mots de passe de divers composants d'une instance dans la page des détails de l'instance.
* Pour les instances vCenter Server, vous pouvez désormais installer des mises à jour et des modules de correction de logiciel pour les composants IBM directement à partir de la console. Pour plus d'informations, voir [Application de mises à jour et de modules de correction à des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

## Notifications sur la console
{: #relnotes_v14-console-notif}

Vous pouvez désormais configurer des notifications de console sur la page **Paramètres**. Le paramètre est activé par défaut, ce qui signifie que vous recevez une notification sur la console pour tous les événements. Vous pouvez désactiver les notifications sur la console dans la page **Paramètres**.

Pour plus d'informations, voir les rubriques suivantes :

* [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Notifications](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)

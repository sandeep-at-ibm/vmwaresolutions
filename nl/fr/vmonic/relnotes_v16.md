---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# Notes sur l'édition pour la version 1.6

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Mises à jour des instances VMware Cloud Foundation

Les composants suivants sont nouveaux ou ont été mis à jour :

*  Gestionnaire SDDC 2.2.1
*  Composants de gestion IBM version 1.6
*  Nouvelles spécifications matérielles : **Petite** ou **Standard**, en fonction de vos besoins.
*  Nouveaux centres de données disponibles pour déploiement : **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Séoul**, **SNG01 - Singapour** et **SYD04 - Sydney**.

Pour la liste complète des composants, voir [Présentation de VMware Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Mises à jour des instances VMware vCenter Server

### Améliorations matérielles pour les instances vCenter Server

A compter de la version 1.6, plusieurs améliorations sont disponibles pour vos instances vCenter Server.

*  Implémentation totale de la spécification de la version 2.0 pour l'offre vCenter Server. Pour plus d'informations, voir l'[architecture de la solution VMware vCenter Server on IBM Cloud](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0).
*  Nouvelles spécifications matérielles : **Petite**, **Moyenne** ou **Grande**, en fonction de vos besoins.
*  Nouveaux centres de données disponibles pour déploiement : **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Séoul**, **SNG01 - Singapour** et **SYD04 - Sydney**.
*  Au moins deux serveurs ESXi dans votre commande d'instance, avec VMware vSphere DRS (Distributed Resource Scheduler, planificateur de ressources distribuées) et VMware HA (High Availability, haute disponibilité) activés par défaut.
*  Jusqu'à sept partages de fichiers NFS peuvent être ajoutés lorsque vous commandez des instances. Les composants de gestion (vCenter, PSC, gestionnaire NSX et contrôleurs, CloudDriver) s'exécutent désormais sur un partage de fichiers NFS pour une haute disponibilité.
*  Déploiement et configuration automatiques de la passerelle de services VMware NSX Edge gérée par le client.

En raison de ces modifications, vous ne pouvez pas utiliser en l'état (ou mettre à niveau) vos instances vCenter Server existantes de la version actuelle. Les instances vCenter Server antérieures à l'édition V1.6 sont toujours visibles sur la console {{site.data.keyword.vmwaresolutions_short}} en mode d'affichage uniquement. Dans l'interface utilisateur, la mention **Obsolète** apparaît pour ces instances avec une icône de symbole d'avertissement.

Les actions suivantes sont disponibles sur les instances vCenter Server antérieures à la version 1.6 :

*  Affichage des informations sur la page des détails de l'instance. Les informations affichées dans les propriétés d'instance correspondent aux données de la date d'édition de la version 1.6 et ne peuvent plus être actualisées.
*  Ouverture du client Web VMware vSphere et utilisation de l'instance dans vCenter.
*  Suppression de l'instance.

Toutes les autres actions des instances antérieures à la version 1.6 ne sont plus disponibles.

### Améliorations réseau des instances vCenter Server

*  Un sous-réseau public avec 16 adresses IP sur le VLAN public est commandé en votre nom pour permettre à vos machines virtuelles d'accéder à Internet.
*  Un sous-réseau privé avec 64 adresses IP sur le VLAN privé est commandé en votre nom pour permettre à vos machines virtuelles d'accéder au réseau interne SoftLayer.
*  Des contrôleurs NSX sont déployés avec des règles anti-affinité et s'exécutent sur des serveurs ESXi distincts dans une configuration de déploiement à 3 noeuds.
*  Une nouvelle passerelle de services VMware NSX Edge à l'usage du client.

   Une passerelle de services NSX ESG (Edge Services Gateway) supplémentaire est maintenant déployée dans le cadre des nouvelles instances vCenter Server que vous commandez.

   Cette passerelle ESG est destinée à être utilisée avec vos propres machines virtuelles pour permettre les communications entre les sous-réseaux privé et public qui sont commandés en votre nom et elle inclut deux interfaces, l'une d'elles est connectée au VXLAN virtualisé associé à vos machines virtuelles et l'autre est connectée au VLAN public. De plus, les paramètres suivants sont configurés :
   *  Règle de pare-feu pour autoriser l'intégralité du trafic sortant issu de la plage d'adresses IP du sous-réseau privé.
   *  Règle de conversion d'adresses réseau (désactivée par défaut) afin de convertir toutes les adresses IP du sous-réseau privé
   en une seule adresse IP sur le sous-réseau public.
   * VMware haute disponibilité est configuré de manière à utiliser un nouveau groupe de ports partagé entre la passerelle ESG de gestion et la passerelle ESG gérée
   par le client.

   Cette passerelle ESG est déployée pour tous les types matériel d'instance et les client peuvent modifier la configuration. Pour plus d'informations, voir les rubriques suivantes :
   *  [Configuration du réseau en vue d'utiliser la passerelle NSX Edge gérée par le client avec vos machines virtuelles](../vcenter/vc_esg_config.html)
   *  [Documentation VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Améliorations de la convivialité

Des améliorations ont été apportées à l'interface utilisateur, à savoir :

*  Le panneau de navigation principal de la console a été grandement amélioré via l'introduction du panneau de navigation de gauche avec accès à toutes les zones de l'interface utilisateur. Vous pouvez rapidement commander un nouvelle instance, afficher vos instances déployées, passer en revue les notifications système, modifier des paramètres et accéder à la documentation en ligne.
*  La nouvelle page **Initiation**, accessible depuis le panneau de navigation de gauche, affiche suffisamment de détails sur la console pour vous aider à prendre une décision éclairée concernant les composants de l'instance que vous commandez. Sur la page **Initiation**, vous êtes également guidé pas à pas dans le processus de commande d'une instance, de l'adéquation aux exigences liées à la commande d'une instance (par exemple, les comptes utilisateur requis) jusqu'à passation de la commande.
*  Les détails récapitulatifs des instances Cloud Foundation et vCenter Server sont regroupés sur une seule page, accessible depuis le menu **Instances déployées** du panneau de navigation de gauche. A partir de cette page, vous pouvez sélectionner l'onglet approprié pour filtrer les instances Cloud Foundation ou vCenter Server.
* Si la reprise après incident Zerto est installée sur votre instance, vous pouvez accéder directement à la console Zerto depuis la page des détails du service en un seul clic. Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html) and [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html).

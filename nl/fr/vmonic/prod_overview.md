---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# A propos d'IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_full}} permet d'intégrer ou de faire migrer rapidement et en toute transparence vos charges de travail VMware locales dans {{site.data.keyword.cloud_notm}} à l'aide de l'infrastructure {{site.data.keyword.cloud_notm}} haute performance sécurisée et de la technologie de virtualisation hybride VMware, leader de l'industrie.

Avec {{site.data.keyword.vmwaresolutions_short}} vous pouvez déployer facilement vos environnements virtuels VMware et gérer les ressources de l'infrastructure sur {{site.data.keyword.cloud_notm}}. Dans le même temps, vous pouvez toujours utiliser votre console habituelle du produit VMware pour gérer les charges de travail VMware.

## Avantages d'IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_short}} offre les avantages majeurs suivants :
* **Portée mondiale** : possibilité de développer la présence de votre cloud hybride jusqu'à 30 {{site.data.keyword.CloudDataCents_notm}} d'entreprise dans le monde entier.
* **Intégration en toute transparence** : intégration en toute transparence dans le cloud hybride avec l'infrastructure {{site.data.keyword.cloud_notm}}.
* **Mise à disposition rapide** : automatisation du déploiement et de la configuration de l'environnement VMware, de sorte que vous pouvez déployer rapidement un environnement d'entreprise VMware avec des serveurs {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} à la demande et des serveurs virtuels.
* **Simplification** : possibilité de consommer une plateforme cloud sans avoir à vous identifier, vous procurer, déployer et gérer l'infrastructure physique sous-jacente (calcul, stockage et réseau) et les licences logicielles.
* **Souplesse d'extension et de réduction** : possibilité d'étendre et de réduire facilement vos charges de travail VMware en fonction de vos besoins métier.
* **Console de gestion unique** : console unique pour déployer, accéder et gérer les environnements VMware sur {{site.data.keyword.cloud_notm}}.

## Offres de déploiement

{{site.data.keyword.vmwaresolutions_short}} offrent des choix de déploiements normalisés et personnalisables des environnements virtuels VMware. Les types de déploiement suivants sont proposés :
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** : l'offre vCenter Server vous permet de déployer un environnement virtuel VMware avec les ressources de calcul, de stockage et de réseau les mieux adaptées à vos besoins métier.
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle** : l'offre vCenter Server with Hybridity est un cloud privé hébergé qui vous permet de déployer rapidement et facilement votre infrastructure locale dans le cloud. L'environnement VMware est basé sur des licences SDDC (Software Defined Data Center) VMware fournies par IBM et inclut VMware Hybrid Cloud Extension (HCX). HCX vous permet de connecter un environnement vSphere 5.0+ local à des sites IBM Cloud de manière sécurisée pour obtenir une hybridité d'infrastructure transparente et une véritable mobilité d'application.
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}** : l'offre Cloud Foundation fournit un environnement virtuel VMware unifié avec les ressources de calcul, de stockage et de réseau {{site.data.keyword.cloud_notm}} standard dédiées à chaque déploiement utilisateur.
* **VMware vSphere on {{site.data.keyword.cloud_notm}}** : l'offre vSphere on {{site.data.keyword.cloud_notm}} fournit un service de virtualisation personnalisable qui combine des serveurs {{site.data.keyword.baremetal_short}} compatibles VMware, des composants matériels et des licences afin de générer votre propre environnement VMware hébergé sur IBM.
* **NetApp ONTAP Select** : l'offre NetApp ONTAP Select vous permet de déployer un cluster de stockage défini par les logiciels qui répond à vos besoins en matière de dispositif de stockage dédié à haute disponibilité basé sur NetApp ONTAP Select.
* **VMware Federal on {{site.data.keyword.cloud_notm}}** : l'offre VMware Federal on {{site.data.keyword.cloud_notm}} fournit la prise en charge permettant de commander une instance vCenter Server de base, fournit l'option de sécurisation des instances déployées et retire les informations sensibles et la connexion de gestion ouverte pour l'accès entrant à l'instance des fonctions de gestion.

## Services supplémentaires

{{site.data.keyword.vmwaresolutions_short}} vous permet d'ajouter divers services au moment où vous commandez une instance ou après le déploiement de l'instance. Les services suivants sont proposés :

### FortiGate Security Appliance on IBM Cloud

Ce service déploie une paire à haute disponibilité de dispositifs FortiGate Security Appliance (FSA) série 300 qui fournissent des services de pare-feu, de routage, de conversion d'adresses réseau (NAT) et de réseau privé virtuel (VPN) afin de protéger la connexion du réseau public à votre environnement.

Ce service est disponible uniquement pour les instances déployées en version 1.8 et éditions ultérieures.

Pour plus d'informations, voir [Gestion de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

Ce service déploie une paire à haute disponibilité de dispositifs FortiGate Virtual Appliance qui vous permettent de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle.

Ce service est disponible uniquement pour les instances déployées en version 2.0 et éditions ultérieures.

Pour plus d'informations, voir [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

Ce service optimise les performances et garantit la disponibilité et la sécurité des applications via F5 BIG-IP Virtual Edition (VE).

Ce service est disponible uniquement pour les instances déployées en version 1.9 et éditions ultérieures.

Pour plus d'informations, voir [Gestion de F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### IBM Spectrum Protect Plus on IBM Cloud

Ce service fournit une solution évolutive et efficace de protection, de réutilisation et de reprise des données pour les environnements virtuels. Vous pouvez l'implémenter en tant que solution autonome ou vous pouvez l'intégrer à votre environnement IBM Spectrum Protect&trade; Plus pour décharger des copies de stockage à long terme et pour la gouvernance des données.

**Remarques** :
* Ce service est disponible uniquement pour les instances déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures.
* Pour les instances déployées en version 2.3 ou dans des éditions ultérieures, IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fournit automatiquement un service de sauvegarde pour les machines virtuelles de gestion. 
* Pour les instances déployées en version 2.2, ce service assure la protection des données uniquement pour les machines virtuelles de charge de travail.

Pour plus d'informations, voir [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

Ce service s'intègre en toute transparence à votre environnement VMware pour vous aider à gérer la sauvegarde et la restauration de toutes les machines virtuelles de votre environnement, y compris la sauvegarde et la restauration des composants de gestion. Il peut fournir un objectif de point de reprise de moins de 15 minutes à partir de la configuration de vos données.

Ce service est configuré pour effectuer une sauvegarde des machines virtuelles de gestion immédiatement après le déploiement de votre instance.

Ce service est disponible uniquement pour les instances déployées en version 1.8 ou dans les éditions ultérieures.

Pour plus d'informations, voir [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

Ce service fournit des fonctions de réplication et de reprise après incident qui vous aident à protéger vos charges de travail. Pour plus d'informations, voir [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

### Services gérés issus d'IMI

Ces services activent IBM Integrated Managed Infrastructure (IMI) afin de distribuer des services de gestion à distance dynamique pour un large éventail d'infrastructures de cloud.

Ces services sont disponibles uniquement pour des instances Cloud Foundation.

Pour plus d'informations, voir [Demande de services gérés issus d'IMI](../services/managing_imi.html).

## Liens connexes

* [Initiation](../index.html)
* [Présentation de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)

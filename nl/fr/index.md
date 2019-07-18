---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Initiation à IBM Cloud for VMware Solutions
{: #getting-started}

Ce tutoriel d'initiation à {{site.data.keyword.vmwaresolutions_full}} écrit la procédure de commande d'une instance et de services complémentaires.
{:shortdesc}

## Avant de commencer
{: #getting-started-prereqs}

Avant de commencer à utiliser {{site.data.keyword.vmwaresolutions_short}}, examinez les informations importantes suivantes sur les exigences quant au navigateur, les comptes utilisateur, les options de déploiement et les services complémentaires.

### Navigateur nécessaire
{: #getting-started-browser-req}

Les navigateurs suivants sont pris en charge :
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer n'est pas pris en charge.
{:note}

Pour des conditions optimales de travail et d'affichage sur la console {{site.data.keyword.vmwaresolutions_short}}, définissez la résolution d'écran au minimum sur 1024 pixels de largeur et 500 pixels de hauteur.

### Comptes utilisateur
{: #getting-started-user-accts}

Vous aurez besoin d'un compte {{site.data.keyword.cloud_notm}} et d'un compte d'infrastructure {{site.data.keyword.cloud_notm}}. Ces comptes doivent se conformer à certaines exigences.

| Compte | Description |
|:------- |:---------- |
| IBMid | En utilisant l'**IBMid**, vous pouvez utiliser un seul et même nom d'utilisateur de connexion pour tous vos produits et services IBM, y-compris {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} est fourni en tant que solution d'infrastructure dans le catalogue {{site.data.keyword.cloud_notm}}. Pour accéder à la console {{site.data.keyword.vmwaresolutions_short}}, vous devez disposer d'un **IBMid**.<br><br>Afin d'utiliser votre **IBMid** pour vous connecter à la console {{site.data.keyword.vmwaresolutions_short}}, vous devez associer l'**IBMid** à un compte {{site.data.keyword.cloud_notm}}. Lors de votre première connexion à la console, vous avez le choix entre associer votre **IBMid** à un compte {{site.data.keyword.cloud_notm}} existant ou souscrire à un nouveau compte {{site.data.keyword.cloud_notm}}. Le nouveau compte {{site.data.keyword.cloud_notm}} est automatiquement associé à votre **IBMid**. Ce processus n'est à effectuer qu'une seule fois.<br><br>En cas de problème lors de l'association de votre **IBMid** à un compte {{site.data.keyword.cloud_notm}}, voir [Traitement des incidents liés à l'accès à {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-accessing#accessing). |
| Compte IBM Cloud | Pour commander et utiliser des services {{site.data.keyword.cloud_notm}}, un compte {{site.data.keyword.cloud_notm}} est requis. Les informations de facturation sont associés au compte {{site.data.keyword.cloud_notm}}. Les coûts d'infrastructure physique et virtuelle ainsi que des licences associées sont facturés sur votre compte {{site.data.keyword.cloud_notm}}. |
| Compte d'infrastructure IBM Cloud | Pour plus d'informations sur les exigences auxquelles un compte d'infrastructure {{site.data.keyword.cloud_notm}} doit répondre, voir [Exigences concernant le compte d'infrastructure {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).<br><br>Vous pouvez lier vos comptes d'infrastructure {{site.data.keyword.cloud_notm}} à des comptes {{site.data.keyword.cloud_notm}} afin d'utiliser des ressources IaaS (Infrastructure as a Service) et PaaS (Platform as a Service). Vous pouvez ensuite accéder à des ressources IaaS et à des ressources PaaS à partir d'une seule connexion. La liaison de vos comptes permet également l'émission d'une facture unique pour toutes les ressources PaaS et IaaS que vous utilisez : <br>Si vous ne disposez d'aucun compte d'infrastructure {{site.data.keyword.cloud_notm}}, demandez-en un en suivant la procédure décrite dans [Inscription à un compte d'infrastructure IBM Cloud](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra), puis liez votre compte d'infrastructure {{site.data.keyword.cloud_notm}} à votre compte {{site.data.keyword.cloud_notm}} en suivant la procédure décrite dans [Passage à l'IBMid et liaison des comptes](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).<br>Si vous disposez d'un compte d'infrastructure {{site.data.keyword.cloud_notm}}, vous pouvez le lier à votre compte {{site.data.keyword.cloud_notm}} en suivant la procédure décrite dans [Passage à l'IBMid et liaison des comptes](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).
{: caption="Tableau 1. Comptes utilisateurs requis" caption-side="top"}

### Offres de déploiement
{: #getting-started-depl-offerings}

Examinez et sélectionnez votre offre de déploiement.

| Offre de déploiement | Description |
|:------------------- |:----------- |
| [VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview) | L'offre vCenter Server vous permet de déployer un environnement virtuel VMware avec les ressources de calcul, de stockage et de réseau les mieux adaptées à vos besoins métier.
| [VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview) | L'offre vCenter Server with Hybridity est un cloud privé hébergé qui vous permet de déployer rapidement et facilement votre infrastructure locale dans le cloud. L'environnement VMware est basé sur des licences SDDC (Software Defined Data Center) VMware fournies par IBM et inclut VMware Hybrid Cloud Extension (HCX). HCX vous permet de connecter un environnement vSphere 5.0+ local à des sites {{site.data.keyword.cloud_notm}} de manière sécurisée pour obtenir une hybridité d'infrastructure transparente et une véritable mobilité d'application.
| [VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview) | L'offre vSphere on {{site.data.keyword.cloud_notm}} fournit un service de virtualisation personnalisable qui combine des serveurs {{site.data.keyword.baremetal_short}} compatibles VMware, des composants matériels et des licences afin de générer votre propre environnement VMware hébergé sur IBM. |
| [NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview) | L'offre NetApp ONTAP Select vous permet de déployer un cluster de stockage défini par les logiciels qui répond à vos besoins en matière de dispositif de stockage dédié à haute disponibilité basé sur NetApp ONTAP Select. |
{: caption="Tableau 2. Offres de déploiement" caption-side="top"}

### Services complémentaires
{: #getting-started-add-on-services}

Examinez et sélectionnez des services complémentaires pour votre offre de déploiement.

| Nom de service | Description |
|:------------ |:----------- |
| [F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | Le service F5 on {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) fournit des services intelligents d'équilibrage de charge L4-L7 et de gestion du trafic à l'échelle locale et globale, une protection maximale via pare-feu des applications Web et réseau et un accès sécurisé aux applications fédérées. |
| [FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) |Le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} déploie une paire de dispositifs FortiGate Security Appliance (FSA) série 300 en mode haute disponibilité, qui fournissent des services de pare-feu, de routage, de conversion d'adresses réseau (NAT) et de réseau privé virtuel (VPN) afin de protéger tous les serveurs et machines virtuelles sur le VLAN public de vos instances.|
| [FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | Le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} déploie dans votre environnement une paire de dispositifs FortiGate Virtual Appliance qui vous permettent de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle. |
| [HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | Le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}} applique et contrôle la conformité par rapport aux normes de sécurité standard et fournit un contrôle d'accès à base de rôles et des fonctions d'approbation et d'audit. Combiné à HyTrust DataControl, le service garantit que les machines virtuelles et les données de charge de travail ne quittent pas une région, un cluster ou un serveur ESXi donnés au sein de l'{{site.data.keyword.CloudDataCent_notm}}. |
| [HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations) | Le service HyTrust DataControl on {{site.data.keyword.cloud_notm}} offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service peut fournir un chiffrement au niveau du système d'exploitation et au niveau des données, ce qui signifie que n'importe quel répertoire, dossier ou fichier d'une charge de travail peut être chiffré et déchiffré.|
| [HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | Le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}} simplifie la gestion des charges de travail chiffrées en automatisant et en simplifiant le cycle de vie des clés de chiffrement. Le service peut facilement gérer les clés de chiffrement à l'échelle à l'aide du chiffrement compatible avec FIPS 140-2. |
| [IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | Le service {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} fournit la puissance des microservices et des conteneurs à votre environnement VMware sur {{site.data.keyword.cloud_notm}}. Grâce à ce service, vous pouvez déployer dans {{site.data.keyword.cloud_notm}} le modèle opérationnel et les outils VMware et {{site.data.keyword.cloud_notm}} Private auxquels vous êtes habitués dans votre environnement local.|
| [IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | Le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} fournit une solution évolutive et efficace de protection, de réutilisation et de récupération des données pour les environnements virtuels. Vous pouvez implémenter le service en tant que solution autonome ou vous pouvez l'intégrer à votre environnement IBM Spectrum Protect Plus pour décharger des copies de stockage à long terme et pour la gouvernance des données. |
| [KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | Le service KMIP for VMware sur {{site.data.keyword.cloud_notm}} offre une haute disponibilité permettant de gérer les clés de chiffrement qu'utilise VMware dans {{site.data.keyword.cloud_notm}}. Il propose une fonction d'exécution qui permet aux clients de créer, extraire, activer, révoquer et détruire des clés de chiffrement. Il offre également une fonction de gestion des associations entre les données d'identification du client et les clés de chiffrement. |
| [Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | Le service Veeam on {{site.data.keyword.cloud_notm}} s'intègre directement et en toute transparence à vos hyperviseurs VMware afin d'aider votre entreprise à obtenir la haute disponibilité requise. Il peut fournir des objectifs de point et de temps de reprise pour vos applications et vos données. Les objectifs de point et de temps de reprise peuvent être fournis moins de 15 minutes après la fin de la configuration. Ce service vous permet de contrôler directement à la fois la sauvegarde et la restauration de toutes les machines virtuelles de votre infrastructure depuis la console Veeam. |
| [VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | Le service HCX on {{site.data.keyword.cloud_notm}} peut en toute transparence étendre les réseaux des centres de données local dans {{site.data.keyword.cloud_notm}}, ce qui permet de migrer les machines virtuelles vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.|
| [Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | Le service Zerto on {{site.data.keyword.cloud_notm}} fournit des fonctions de réplication et de reprise après incident, qui peuvent être intégrées aux offres de déploiement de manière à assurer la protection et la récupération des données dans votre environnement virtuel VMware sur {{site.data.keyword.cloud_notm}}. |
{: caption="Tableau 3. Services complémentaires disponibles pour les offres de déploiement" caption-side="top"}

## Etape 1 : Accès à la console IBM Cloud for VMware Solutions
{: #getting-started-step1}

La console {{site.data.keyword.vmwaresolutions_short}} est l'interface via laquelle vous commandez et gérez vos déploiements. Chaque déploiement est géré en tant qu'instance dans la console. La console est une interface utilisateur autonome distincte du portail client de l'infrastructure {{site.data.keyword.cloud_notm}}.

Pour accéder à la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
1. Accédez à https://cloud.ibm.com/infrastructure/vmware-solutions/console.
2. Connectez-vous à la console avec votre **IBMid**.

## Etape 2 : Configuration de votre compte utilisateur et des paramètres
{: #getting-started-step2}

Avant de commander une instance, vous devez entrer le nom d'utilisateur et la clé d'API de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres** de la console.

Pour plus d'informations sur la configuration de votre compte utilisateur et des paramètres, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Etape 3 : Commande d'une instance
{: #getting-started-step3}

Après avoir sélectionné une offre de déploiement, laquelle est gérée en tant qu'instance dans la console, lancez la procédure de commande.

Pour plus d'informations sur la commande d'une instance, reportez-vous aux rubriques suivantes en fonction de l'offre de déploiement que vous avez sélectionnée :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Commande d'instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Etape 4 : Examen de l'instance
{: #getting-started-step4}

Après avoir passé une commande d'instance à l'**étape 3**, le déploiement de l'instance démarre automatiquement. Vous pouvez vérifier le statut du déploiement en affichant les détails de l'instance. Une fois le déploiement de l'instance achevé, vous pouvez également examiner le récapitulatif et les informations détaillées de l'instance et de ses services complémentaires sur la page des détails de l'instance.

Pour plus d'informations sur l'affichage de l'instance que vous avez commandée, voir les rubriques suivantes :
* [Affichage des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Affichage des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Affichage des instances NetApp ONTAP Select](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)

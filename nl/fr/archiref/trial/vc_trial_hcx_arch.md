---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Conception d'architecture HCX on IBM Cloud pour la version d'essai à noeud unique vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

VMware HCX on {{site.data.keyword.cloud}} avec la version d'essai à noeud unique pour VMware vCenter Server on {{site.data.keyword.cloud_notm}} est une nouvelle offre qui permet une connexion ininterrompue entre des instances {{site.data.keyword.vmwaresolutions_short}} et un centre de données virtuel VMware sur site. Alors que la recommandation pour vCenter Server est de trois noeuds au minimum, cette version d'essai à noeud unique permet d'expérimenter à moindres frais les avantages d'une implémentation de cloud hybride.

{{site.data.keyword.vmwaresolutions_short}} inclut des déploiements rapides et entièrement automatisés des configurations vCenter Server dans {{site.data.keyword.cloud_notm}}. L'offre de version d'essai à noeud unique pour vCenter Server complète l'infrastructure sur site et permet aux charges de travail existantes et futures de s'exécuter dans {{site.data.keyword.cloud_notm}} sans conversion. L'offre utilise les mêmes outils, compétences et processus que ceux utilisés sur site. Pour plus d'informations sur les offres {{site.data.keyword.vmwaresolutions_short}}, voir [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

Le service HCX on {{site.data.keyword.cloud_notm}} mélange les instances vCenter Server avec des centres de données virtuels sur site existants, et en permettant la création d'extensions réseau ininterrompues et la migration bidirectionnelle de charges de travail. Les composants HCX on IBM Cloud, qui sont déployés en tant que machines virtuelles sur le site cible {{site.data.keyword.cloud_notm}} VMware, permettent l'établissement d'une connexion avec les composants HCX on {{site.data.keyword.cloud_notm}} qui sont installés sur le site source local de l'homologue.

Figure 1. Architecture HCX

![Architecture HCX](hcx-architecture.svg "Architecture HCX")

Les informations suivantes concernent la conception d'une implémentation du service HCX on {{site.data.keyword.cloud_notm}}. Celle-ci inclut à la fois les composants sur l'instance {{site.data.keyword.vmwaresolutions_short}} côté cible et les composants qui sont déployés sur la source, sur site.

## Présentation de HCX on IBM Cloud
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} s'intègre en toute transparence aux réseaux vSphere vCenter locaux dans les déploiements {{site.data.keyword.vmwaresolutions_short}}. La mise en réseau hybride s'étend aux réseaux vSphere vCenter locaux dans {{site.data.keyword.cloud_notm}}, en prenant en charge la mobilité de machine virtuelle bidirectionnelle.

HCX détient les processus de chiffrement et déchiffrement source et destination, en garantissant une sécurité cohérente et l'admission de flux de travaux hybrides comme la migration de machine virtuelle et l'extension de réseau. Cette offre crée un réseau WAN optimisé, défini par les logiciels pour l'augmentation des performances de réseau étendu, avec des performances proches de celles de la vitesse d'un réseau local. HCX permet la migration de la charge de travail bidirectionnelle et de la politique de sécurité VMware NSX vers {{site.data.keyword.cloud_notm}}, s'intègre à vSphere vCenter et est géré depuis le client Web vSphere.

### Extension de réseau de couche 2
{: #vc_trial_hcx_arch-layer-2-extension}

HCX permet à un site existant en local vSphere d'étendre en toute sécurité un réseau depuis son site vCenter local vers un {{site.data.keyword.CloudDataCent_notm}} exécutant VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} ou vCenter Server. Les éléments suivants permettent d'activer cette fonction :

* HCX fournit un dispositif qui est appelé Concentrateur de couche 2 (L2C).
* Les réseaux étendus se relient aux dispositifs {{site.data.keyword.cloud_notm}} NSX Edge déployés dans vCenter Server.
* Possibilité de déployer plusieurs concentrateurs de couche 2 pour atteindre l'évolutivité et un débit accru depuis le site vCenter local.
* Les machines virtuelles qui sont migrées via la passerelle cloud et sur la couche 2 étendue peuvent conserver leurs adresses IP et MAC.

### Migration de machine virtuelle
{: #vc_trial_hcx_arch-vm-mig}

HCX propose les trois méthodes suivantes pour le déplacement des machines virtuelles :

* Migration avec peu d'interruption
* Migration vSphere vMotion
* Migration à froid

#### Migration avec peu d'interruption
{: #vc_trial_hcx_arch-low-downtime-mig}

La migration avec peu d'interruption repose sur la réplication vSphere, qui est une technologie distribuée mise en oeuvre dans l'hyperviseur VMware ESX ou VMware ESXi. Le déploiement HCX local crée une réplique d'une machine virtuelle réelle dans {{site.data.keyword.cloud_notm}}, et effectue un basculement pour mettre hors tension la machine virtuelle source et mettre sous tension la machine virtuelle migrée. Le chemin de migration est toujours via la passerelle cloud. Le transport peut être Internet, un réseau étendu de couche 2, ou une ligne de connexion directe. Vous pouvez migrer une machine virtuelle plusieurs fois dans les deux sens.

#### Migration vSphere vMotion
{: #vc_trial_hcx_arch-vmotion-mig}

Vous pouvez transférer des machines virtuelles à l'aide de la migration vSphere vMotion sur un réseau étendu à {{site.data.keyword.cloud_notm}}. La migration vMotion est également appelée migration sans interruption ou vMotion entre clouds.

#### Migration à froid
{: #vc_trial_hcx_arch-cold-mig}

Avec la migration à froid, vous pouvez transférer une machine virtuelle hors tension vers {{site.data.keyword.cloud_notm}} via un réseau étendu qui est créé à l'aide du concentrateur de couche 2.

#### Fonctions de migration communes
{: #vc_trial_hcx_arch-common-feat}

Les fonctions suivantes sont disponibles sur les trois types de migration :

* Optimisation de réseau WAN définie par les logiciels qui accroît le débit et la vitesse de migration.
* Planification de votre migration à une heure spécifique.
* Conservation du nom d'hôte et/ou du nom de machine virtuelle.

### Mise en réseau
{: #vc_trial_hcx_arch-network}

Les fonctions de mise en réseau suivantes sont intégrées à la passerelle cloud et aux concentrateurs de couche 2.

#### Intelligent Flow Routing
{: #vc_trial_hcx_arch-intel-flow}

Cette fonction sélectionne automatiquement les meilleures connexions d'après le chemin Internet, par un envahissement efficace de la connexion entière de sorte que les charges de travail soient déplacées aussi vite que possible. Lorsque des flux plus importants, comme la sauvegarde ou la réplication, entraînent un conflit d'UC, des flux plus petits sont routés vers des UC moins occupées, ce qui améliore les performances d'un trafic interactif.

#### Routage de proximité
{: #vc_trial_hcx_arch-prox-routing}

Le routage de proximité garantit que l'acheminement entre les machines virtuelles qui sont connectées aux réseaux étendus et routés, à la fois en local et dans le cloud, est symétrique. Cette fonction nécessite des services réseau avancés avec un routage dynamique configuré entre le site client local et le cloud.

Lorsque des utilisateurs étendent leurs réseaux au cloud, la connectivité de couche 2 est étendue sur les réseaux {{site.data.keyword.cloud_notm}}. Toutefois, sans optimisation de route, les demandes de communication de couche 3 doivent retourner vers l'origine du réseau local pour être routées. Ce trajet retour est appelé "tromboning" ou "hairpinning". Le trajet de type Tromboning est inefficace car les paquets doivent transiter entre l'origine du réseau et le cloud, même lorsque les machines virtuelles source et destination résident dans le cloud.

Si le chemin d'acheminement inclut des pare-feux sans état, ou d'autres équipements en ligne qui doivent voir les deux côtés de la connexion, la communication peut échouer. Une défaillance de communication de machine virtuelle (sans optimisation de route) se produit lorsque le chemin d'entrée qui quitte le cloud peut être le réseau de couche 2 étendu ou le réseau routé de l'organisation. Le réseau local ne connaît pas le "raccourci" du réseau étendu. Ce problème est appelé routage asymétrique. La solution est d'activer le routage de proximité de sorte que le réseau local puisse apprendre les routes depuis {{site.data.keyword.cloud_notm}}.

La passerelle cloud gère un inventaire des machines virtuelles dans le cloud. Elle comprend également les états de machine virtuelle suivants :

* Machine virtuelle transférée vers {{site.data.keyword.cloud_notm}} avec vMotion (migration sans interruption)
* Machine virtuelle migrée vers le cloud à l'aide de la réplication basée sur un hôte (migration avec peu d'interruption)
* Machine virtuelle créée dans le cloud (sur un réseau étendu)

#### Sécurité
{: #vc_trial_hcx_arch-sec}

La passerelle cloud offre un déchargement AES-GCM avec IKEv2, compatible Suite B, AES-NI et un contrôle d'admission basé sur les flux. HCX détient les processus de chiffrement et déchiffrement source et destination, en garantissant une sécurité cohérente et l'administration de flux de travaux hybrides comme la migration de machine virtuelle et l'extension de réseau. Vous pouvez migrer les politiques de sécurité qui sont définies et affectées à une machine virtuelle locale dans {{site.data.keyword.cloud_notm}}.

Les conditions suivantes doivent être remplies pour la migration de politique :

* Le centre de données local exécute NSX V6.2.2 ou supérieur.
* Dans vSphere, la politique de sécurité est une section NSX unique qui peut contenir un grand nombre de règles.
* Vous pouvez nommer un ensemble d'adresses IP ou d'adresses MAC qui participeront à la politique.
* Le nom de l'ensemble de règles MAC ou IP ne peut pas dépasser 218 caractères.
* Les règles prises en charge indiquent des adresses IP de couche 3 ou des ensembles d'adresses IP, ou encore des adresses Mac de couche 3 ou des ensembles d'adresses MAC comme source ou destination.

### Composants HCX
{: #vc_trial_hcx_arch-hcx-comp}

Le service HCX on {{site.data.keyword.cloud_notm}} déploie quatre dispositifs virtuels qui sont installés et configurés à la fois sur le centre de données local et la cible IBM Cloud. Les informations suivantes décrivent chacun des quatre dispositifs virtuels requis. Il peut arriver que des unités de périphérie soient nécessaires selon la conception de l'implémentation.

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

Le dispositif virtuel HCX Manager est une extension du vCenter local. Il est déployé en tant que machine virtuelle et sa structure de fichier contient les autres dispositifs virtuels de service hybride. HCX Manager supervise le déploiement et la configuration de la passerelle cloud, des concentrateurs de couche 2 et du dispositif virtuel d'optimisation de réseau WAN à la fois en local et au sein d'{{site.data.keyword.cloud_notm}}.

#### Passerelle de cloud hybride
{: #vc_trial_hcx_arch-hcg}

La passerelle de cloud hybride gère un canal sécurisé entre le site vSphere local et {{site.data.keyword.cloud_notm}}. HCX utilise un chiffrement renforcé pour amorcer une connexion entre sites à {{site.data.keyword.cloud_notm}}. Le canal sécurisé entre vSphere et {{site.data.keyword.cloud_notm}} évite les problèmes de sécurité "middle mile" de mise en réseau. La passerelle cloud incorpore également la technologie de réplication vSphere pour effectuer une migration bidirectionnelle.

#### Optimisation du réseau WAN
{: #vc_trial_hcx_arch-wan-opt}

Le dispositif d'optimisation du réseau WAN est le composant qui effectue un conditionnement de réseau WAN pour réduire les effets de latence. Il incorpore également la correction d'erreur en aval (Forward Error Correction) pour annuler les scénarios de perte de paquet, et le dédoublonnage de modèles de trafic redondant. Ensemble, tout cela réduit l'utilisation de bande passante et garantit la meilleure utilisation de la capacité réseau disponible pour l'expédition du transfert de données vers et depuis {{site.data.keyword.cloud_notm}}.

La migration de machine virtuelle repose sur la combinaison d'une passerelle cloud et d'un dispositif d'optimisation du réseau WAN pour atteindre une mobilité sans égale entre vSphere en local et {{site.data.keyword.cloud_notm}}. De plus, l'extension de couche 2 bénéficie d'une optimisation de réseau WAN lorsque le chemin de données est routé via la passerelle cloud.
{:important}

#### Concentrateurs de couche 2
{: #vc_trial_hcx_arch-layer-2-conc}

Les dispositifs de concentrateurs de couche 2 (L2C) permettent l'extension d'un réseau de couche 2 depuis le centre de données vSphere local vers {{site.data.keyword.cloud_notm}}.

Les concentrateurs de couche 2 sont dotés des interfaces suivantes :

* **Interface de jonction interne** Gère le trafic de machines virtuelles en local pour les réseaux étendus à l'aide d'un mappage de pont de traduction vers un réseau étendu correspondant dans IBM Cloud. Cette interface gère le trafic de machine virtuelle sur site pour les réseaux étendus à l'aide d'un mappage de pont de traduction vers un réseau étendu correspondant dans {{site.data.keyword.cloud_notm}}.
* **Interface de liaison montante ** HCX utilise cette interface pour envoyer le trafic de superposition encapsulé vers et depuis {{site.data.keyword.cloud_notm}}. Les données d'application transitent via cette interface de liaison montante.

### Architecture de déploiement
{: #vc_trial_hcx_arch-deployment}

Pour plus d'informations sur le déploiement de HCX on {{site.data.keyword.cloud_notm}}, voir [VMware HCX on {{site.data.keyword.cloud_notm}}
Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).

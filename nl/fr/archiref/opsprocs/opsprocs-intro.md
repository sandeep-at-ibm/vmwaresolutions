---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# Introduction
{: #opsprocs-intro}

De nombreuses sociétés informatiques documentent leurs procédures opérationnelles dans un dossier d'exploitation. Un dossier d'exploitation est un ensemble de documents, de références et de procédures normalisés qui expliquent les tâches informatiques communes récurrentes. Le personnel informatique se réfère au dossier d'exploitation pour trouver la meilleure façon d'effectuer son travail. Les dossiers d'exploitation améliorent l'efficacité de l'organisation grâce à la standardisation et facilitent l'intégration des employés. Il existe généralement deux types de dossiers d'exploitation :

1. Documentation générale utilisée pour saisir les procédures, les guides et les tâches. Elles ont tendance à être de nature générale et renvoient à la documentation existante fournie par les fournisseurs.
2. Documentation spécialisée rédigée pour l'entreprise. Cette documentation est spécifique à un système, une application ou une suite d'applications et n'est pas couverte par la documentation des fournisseurs. Lorsque vous documentez votre documentation spécialisée, nous vous conseillons la structure suivante :

 * Présentation - Un aperçu du service avec des sections qui décrivent :
    * En quoi consiste le service et pourquoi l'entreprise a-t-elle besoin du service
    * Qui sont les contacts principaux du service 
    * Comment signaler des problèmes avec le service
 * Développement - Cette section est principalement axée sur les équipes de développement et les principaux composants logiciels du service, ainsi que sur la façon dont le service est construit. Elle contient des informations sur les produits logiciels, l'emplacement des OVA, les supports de distribution ou l'emplacement du code source. Elle inclut également les étapes nécessaires au conditionnement ou à la distribution de la version ainsi que toutes les instructions nécessaires à une prise en main par un nouveau développeur.
 * Déploiement - Cette section est principalement axée sur l'équipe d'exploitation et la façon de déployer le logiciel. Elle inclut des détails sur le matériel et l'infrastructure virtualisée ainsi que sur la façon de construire les machines virtuelles, y compris les exigences en matière de vCPU, RAM et disque, la version et la configuration du système d'exploitation, ou les logiciels intermédiaires ou paquets à installer.
 * Procédures - Instructions étape par étape pour la réalisation de tâches courantes comme les opérations d'ajout, de modification et de suppression, solutions aux problèmes communs et conseils de dépannage.
 * Dépannage - Une liste des alertes courantes du système de surveillance, y compris les tâches étape par étape pour ces alertes, ainsi que des conseils généraux sur le dépannage du service.
 * Plans et procédures de reprise après incident - Détails sur la façon de restaurer le service dans un autre emplacement suite à un incident survenu à l'emplacement principal.
 * Accord sur les niveaux de service - Les paramètres de service convenus tels que les accords sur les niveaux opérationnels, les indicateurs clés de performance, les objectifs de disponibilité, les objectifs de points de reprise, les objectifs de temps de reprise.

La plupart des organisations informatiques ont plusieurs dossiers d'exploitation qui servent de manuels de référence. Cette série de documentation est conçue pour être utilisée comme un dossier d'exploitation général pour votre organisation qui utilise des instances vCenter Server. Bien que le contenu de chaque dossier d'exploitation soit spécifique aux besoins de l'organisation, la méthodologie de création d'un dossier d'exploitation est assez standard et se déroule en deux étapes :

1. La première étape consiste à décider quelles procédures doivent être documentées et, lorsqu'elles sont répertoriées, à documenter chacune d'entre elles avec suffisamment de détails.
2. La deuxième étape est continue et consiste à maintenir, mettre à jour et corriger ces procédures, ajouter de nouvelles procédures et retirer des procédures qui ne sont plus nécessaires.

{{site.data.keyword.vmwaresolutions_full}} vous permet de tirer parti des compétences, des outils et des dossiers d'exploitation existants de votre équipe pour gérer vos instances dans {{site.data.keyword.cloud_notm}}. Cependant, nous avons créé la documentation générale suivante pour saisir les instructions, tâches et procédures communes :

* Tâches de configuration - Ces tâches sont des activités courantes que les administrateurs système doivent exécuter pour adapter l'environnement aux besoins de l'entreprise et répondre aux demandes de service telles que l'ajout de nouvelles machines virtuelles et l'augmentation de capacité. Elles sont regroupées dans la structure suivante :
 * Recommandations générales
 * Procédures de machines virtuelles
 * Procédures vCenter
 * Procédures relatives aux hôtes vSphere ESXi
 * Procédures de stockage
 * Procédures de réseau
* Alarmes - vSphere inclut un sous-système d'événements et d'alarmes qui suit les événements se produisant dans l'environnement vSphere et rend ces informations disponibles dans vCenter. Cette section décrit ce sous-système et explique comment activer et utiliser les alarmes dans votre entreprise.
* Contrôles quotidiens proactifs - Ces contrôles permettent aux administrateurs système de maintenir un environnement sain. S'il sont effectués au quotidien, ils devraient éviter que de nombreux problèmes courants liés à la capacité et aux performances n'aient un impact sur vos charges de travail.
* Dépannage - Même lorsque vous effectuez des vérifications quotidiennes proactives, des problèmes peuvent se produire et affecter votre charge de travail, et vous devez résoudre le problème sous-jacent le plus rapidement possible. Ces guides de dépannage et certains scénarios de dépannage courants aident les administrateurs système à identifier et à résoudre rapidement ces problèmes.
* Conformité - Le guide de conformité donne un aperçu du maintien de la conformité de l'environnement par rapport à un régime de conformité réglementaire ou aux meilleures pratiques de l'industrie. Ce guide se concentre sur le guide de renforcement VMware, qui contient des listes de bonnes pratiques documentées pour un environnement VMware.

Plusieurs des tâches ci-dessus sont automatisées dans la gestion des opérations sur {{site.data.keyword.cloud_notm}}, et pour les tâches qui ne le sont pas, cet outil rend les processus manuels beaucoup plus faciles pour vos administrateurs système. Il est impératif que les composants principaux de l'environnement VMware soient surveillés. Dans la gestion des opérations sur {{site.data.keyword.cloud_notm}}, la procédure est la suivante :

## Gestion des opérations sur IBM Cloud
{: #opsprocs-intro-ops-mgmt}

Vous disposez peut-être d'outils d'entreprise que vous pouvez utiliser pour surveiller et gérer votre instance vCenter Server. Le tableau 1 décrit les principaux composants de l'environnement vCenter Server, explique pourquoi ils doivent être surveillés et comment ils le sont à l'aide de la gestion des opérations sur {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir la documentation de l'architecture de référence.

Tableau 1. Composants principaux de l'environnement vCenter Server

| Composant | Pourquoi le surveiller | Surveillé par  |
|---|---|---|
| vCenter | vCenter est le composant de gestion de l'infrastructure qui gère les hôtes vSphere et gère les constructions virtualisées telles que les clusters. vSAN est surveillé à travers vCenter. Les réseaux vSphere tels que les commutateurs distribués et les groupes de ports sont surveillés via vCenter. | vRealize Operations Manager (vROps) et le pack VMware SDDC Health Management Pack. vRealize Log Insights (vRLI) collecte les données de journal de vCenter et le pack de contenus de vSphere ajoute une interprétation spécifique aux journaux et envoie à son tour des alertes à vROPs. |
| Hôtes vSphere | Les hôtes vSphere fournissent l'unité centrale, la mémoire RAM et le réseau virtualisés aux machines virtuelles de calcul. | vROps via vCenter. vRLI collecte les données de journal |
| vSAN | vSAN fournit un magasin de données en consolidant le stockage dans les hôtes pour l'utilisation par les machines virtuelles. Les problèmes qui affectent la capacité et la performance ont un effet sur les applications exécutées sur ces machines virtuelles. |vROps et le pack de gestion de vSAN fournissent des tableaux de bord additionnels qui vous aident dans la surveillance de vSAN. Les bilans de santé de vCenter vSAN sont collectés via vROps. vRLI collecte les données de journal de vCenter. |
| NSX | NSX fournit les composants réseau virtualisés utilisés par les machines virtuelles de calcul. Toute défaillance du réseau peut avoir un impact sur les applications fonctionnant sur ces machines virtuelles. | vROps et le pack vROps Management Pack for VMware NSX offrent une visibilité de la topologie du réseau. vRLI collecte les données de journal des composants NSX tels que les contrôleurs, les passerelles ESG et les commutateurs logiques. vRealize Network Insight (vRNI) fournit des services de dépannage en profondeur des problèmes réseau. |

En plus de la surveillance, la gestion des opérations sur {{site.data.data.keyword.cloud_notm}}, fournit une assistance pour la configuration, la conformité et plusieurs des tâches proactives détaillées dans cette documentation.


## Liens connexes
{: #opsprocs-intro-links}

* [Surveillance vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [VMware security hardening guide](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Gestion des opérations sur {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

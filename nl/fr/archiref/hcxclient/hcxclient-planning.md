---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Préparation de l'environnement d'installation
{: #hcxclient-planning-prep-install}

L'installation de VMware HCX on IBM Cloud exige la configuration logicielle suivante :
* vSphere 5.5 U3 ou vSphere 6.0u2 ou supérieur.
* Si NSX est utilisé, version 6.2.2 ou supérieure. NSX est requis pour la migration de politique.
* Pour utiliser une migration vMotion entre clouds, les mêmes restrictions d'affinité s'appliquent entre les clouds comme c'est le cas en local. Pour plus d'informations, voir [Foire aux questions relatives à la compatibilité entre VMware EVC et UC](https://kb.vmware.com/s/article/1005764).

## Configuration de la connectivité du réseau
{: #hcxclient-planning-config-net}

HCX doit traverser l'Internet public et des lignes privées, et se connecter à des composants de centre de données, comme des réseaux, des commutateurs et des groupes de ports.
* La section [Accès aux ports requis](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req) répertorie les ports qui doivent être ouverts afin que des dispositifs virtuels HCX puissent être installés.
* L'environnement vSphere local et l'environnement VCS HCX Cloud doivent permettre une synchronisation des horloges NTP (Network Time Protocol) entre les unités vSphere locales et les unités VCS HCX. Le port UDP 123 doit être accessible aux dispositifs virtuels et aux réseaux HCX.

## Environnement local
{: #hcxclient-planning-on-prem-env}

Avant d'installer HCX, vérifiez que votre environnement peut prendre en charge les tâches que vous voulez accomplir. L'environnement local doit prendre en charge les tâches suivantes pour que HCX puisse être installé.
* Virtual Center avec vSphere 5.5 Update 3 ou 6.0 Update 2.
* Les fonction de migration vMotion et de politique nécessitent NSX version 6.2.2 ou supérieure.
* Un compte de service vSphere avec le rôle système de Administrator vCenter Server.
* Dans vCenter, espace disque suffisant pour l'installation des dispositifs HCX.
* Nombre d'adresses IP suffisant pour les machines virtuelles en local mises à disposition durant l'installation.
* Ports et pare-feux ouverts, comme indiqué dans la section Accès aux port requis.
* Si le serveur SSO est distant, l'URL du vCenter, du serveur SSO externe, ou le contrôleur PSC (Platform Services Controller) qui exécute le service de recherche externe doivent être identifiés. Lorsque HCX Manager est enregistré auprès de vCenter, cette URL doit être fournie.
* Si un vCenter n'a pas sa propre instance interne du service de recherche, cela doit être dû à l'une des raisons suivantes :
  * vCenter 6.0u2 exécute un contrôleur de service de plateforme externe.
  * vCenter est en mode lié (dans lequel le vCenter secondaire utilise le service SSO depuis le vCenter principal ou un service SSO externe).

## Vérification de l'environnement d'installation de couche 2
{: #hcxclient-planning-verify-layer-2-inst}

L'extension de réseau de couche 2 doit respecter les règles suivantes :
* vSphere édition Enterprise Plus.
* vSphere vCenter doit respecter les exigences suivantes pour prendre en charge une extension de couche 2 :
  * Licence vSphere Enterprise Plus
  * vSphere Distributed Switch (vDS) Obligatoire. Ce commutateur distribué est fourni avec vSphere Enterprise Plus Edition.
  * Une fois installé, le dispositif de service du concentrateur local de couche 2 doit avoir accès à un port vNIC et aux réseaux VLAN à étendre.
  * Si le réseau doit être étendu sur l'Internet public ou un réseau VPN (dans un chemin secondaire), la machine virtuelle L2C dans VCS requiert une adresse IP. L'adresse IP distante est obligatoire pour configurer le concentrateur de couche 2.
  * Si plusieurs concentrateurs de couche 2 sont nécessaires, chacun doit avoir une adresse IP en local et dans le cloud.

## Planification de prédéploiement
{: #hcxclient-planning-predepl}

Une grande partie du temps consacré au déploiement du HCX correspond à la phase de pré-déploiement. Alors que les projets de migration des systèmes d'information prennent généralement plusieurs mois voire plusieurs années, HCX permet une migration rapide et un début de connectivité du réseau vers le cloud immédiatement après le déploiement.

Etant donné que le déploiement de HCX pour un client au niveau de l'entreprise implique généralement des équipes de sécurité, de réseau, de stockage et d'infrastructure vSphere, il est logique d'impliquer ces équipes dans la preuve de concept si possible. Une gestion de projet efficace et l'inclusion précoce des parties prenantes sont essentielles pour assurer la rapidité du déploiement et de l'exploitation du HCX.

## Eviter la paralysie d'analyse
{: #hcxclient-planning-avoiding}

La plupart des obstacles et du temps nécessaire à la migration d'une machine virtuelle ou d'un groupe de machines virtuelles sont dus à la nécessité de modifier certaines parties de l'environnement d'application, à la conception de ces changements et à la programmation des temps d'arrêt nécessaires pour effectuer ces changements. Une fois ces changements apportés, la migration devient difficile à annuler, ce qui accentue la paralysie de l'analyse. Essayer de saisir tous les aspects de la migration, de coordonner les différentes équipes et de changer les principaux intervenants peut retarder la réalisation du projet.

HCX permet la migration croisée d'instances vSphere d'une machine virtuelle ou d'un groupe de machines virtuelles qui représentent une application composite partielle ou complète, sans aucune modification de l'application. Pour cette raison, abandonner une migration signifie déplacer les machines virtuelles vers l'arrière ou redéployer les réseaux. Cela élimine la nécessité d'une grande partie de la planification de la migration et permet un certain parallélisme dans le processus de planification. Après avoir sélectionné les applications à déplacer et créé une conception de réseau de haut niveau, les applications peuvent commencer la migration avec une configuration minimale sur l'instance de cloud pendant que la connectivité et la conception finales du réseau sont élaborées.

## Réseaux étendus
{: #hcxclient-planning-stretched-net}

Les composants d'extension du réseau de la flotte HCX sont très stables. Chez un client particulier ayant plus de 20 VLANs répartis dans le {{site.data.keyword.cloud}} sur un réseau WAN de 1 Gbit/s partagé avec d'autres tunnels de trafic et de migration HCX, il n'y a aucun problème applicatif attribué au réseau. Les liaisons réseau ont une durée de vie supérieure à 6 mois de cette façon.

D'autres réseaux étendus ont été ajoutés et supprimés sans problème. Le choix d'un {{site.data.keyword.CloudDataCent_notm}} à proximité immédiate (latence <6 ms pour ce client particulier) joue également un rôle dans la stabilité réseau d'un réseau étendu. Laisser les réseaux étendus à long terme ne devrait pas être un facteur négatif dans votre conception étant donné que vous disposez d'une bande passante suffisante et d'une latence suffisamment faible pour vos applications.

## Cycle de vie de la migration
{: #hcxclient-planning-mig-lifecycle}

Les sections suivantes décrivent les phases d'un cycle de migration HCX typique, en indiquant où des flux de travail peuvent être effectués en parallèle.

## Inventaire vSphere
{: #hcxclient-planning-vsphere-planning}

- Evaluation grossière des machines virtuelles au sein d'une application à migrer. Ce processus implique la compréhension des machines virtuelles qui participent à une application, sans entrer dans les détails.
- Si vous prévoyez de migrer de nombreuses machines virtuelles et que la bande passante réseau est limitée entre les sites source et cloud, regroupez les machines virtuelles par VLAN ou VXLAN si NSX est utilisé à la source. Cela permet un plan de migration HCX en cascade où les groupes de machines virtuelles par VLAN sont migrés et les réseaux L2 sur lesquels ils résident ne sont étendus que jusqu'au point où les VLAN sont libérés.

Cela signifie que le groupe initial de réseaux étendus L2 connexes ne peut être libéré que lorsque la conception du réseau côté cloud est finalisée et déployée. Le déblocage implique de faire basculer le trafic VXLAN particulier vers l'infrastructure NSX de l'instance de cloud.

## Configuration réseau de base
{: #hcxclient-planning-baseline-net-config}

Créez un réseau de périmètre sécurisé dans l'instance vSphere côté cloud. Il s'agit généralement d'un appareil NSX DLR ou Edge. Si vous utilisez le routage de proximité HCX, il n'est pas nécessaire de créer de règles de pare-feu ou de topologie de liaison montante, car il peut être exécuté ultérieurement ou simultanément sans affecter le trafic L2 étendu.

## Extension de réseau
{: #hcxclient-planning-net-extension}

Etendre le réseau signifie simplement prendre le VLAN ou VXLAN existant de l'environnement vSphere source, représenté par un groupe de ports de commutateur distribué virtuel (vDS), et l'étendre à un VXLAN NSX sur le côté cloud du HCX.

## Tests pré-implémentation
{: #hcxclient-planning-preflight-tests}

Les tests pré-implémentation consistent à effectuer une migration HCX avec la fonction vMotion et la fonction de migration en bloc afin d'établir un taux de transfert de base.

## Migration des applications de non-production
{: #hcxclient-planning-mig-non-prod-apps}

La migration des machines virtuelles commence avec les vagues prévues de machines virtuelles moins critiques. Le développement, les tests, etc., utilisent la connectivité Internet pour la migration et le trafic L2 étendu.

## Début de la conception et de l'implantation du réseau cloud
{: #hcxclient-planning-cloud-net-begins}

Pendant que les migrations se poursuivent, les conceptions de réseau côté cloud sont finalisées et implémentées dans l'instance vSphere côté cloud.

## Autres considérations relatives à la connectivité du réseau
{: #hcxclient-planning-connect-considerations}

Pendant que les migrations se poursuivent, la connectivité du réseau WAN privé est commandée, car il faut généralement de quelques semaines à quelques mois pour établir une connexion avec le fournisseur de cloud. Une fois la connectivité réseau privée terminée, HCX peut être configuré pour utiliser à la fois la liaison réseau privée dédiée et Internet pour la migration et le trafic L2 étendu.

## Serveurs physiques
{: #hcxclient-planning-physical-servers}

Lorsque l'objectif est la migration du centre de données dans le cloud, tous les serveurs physiques qui interagissent avec les machines virtuelles en cours de migration peuvent être évalués pour la migration dans {{site.data.keyword.cloud_notm}} en tant que machines virtuelles (P2V), bare metal ou rester à la source. Si le serveur physique doit rester à la source, et HCX ne sera utilisé que pendant la migration jusqu'à ce qu'un réseau dédié soit établi, il est important de comprendre s'il réside sur un réseau qui est étendu dans le cloud avec HCX. Dans ce scénario, HCX permet non seulement aux machines virtuelles, mais à l'ensemble du sous-réseau d'être migrés dans le cloud.

Pour supprimer HCX à la fin de la migration, le sous-réseau ne peut pas exister dans la source et la destination si la connexion entre les dispositifs physiques et les machines virtuelles migrées doit être maintenue. Cela implique que tous les dispositifs physiques laissés sur le site source qui existent sur des réseaux L2 étendus doivent être migrés vers un autre sous-réseau du réseau qui pourrait être routé vers le côté cloud. L'exception à cette règle est l'utilisation d'une autre technologie L2 étendue, telle que le VPN NSX L2, pour remplacer les noeuds finaux L2 étendus de HCX.

## Migration de la production et des applications complexes
{: #hcxclient-planning-mig-prod-complex-app}

Les machines virtuelles avec des VMDK partagés en mode d'écriture multiple telles que les clusters Oracle RAC ou MS Exchange/SQL ou les machines virtuelles avec des mappages de périphériques bruts sont des exemples de machines virtuelles qui nécessitent une attention particulière avant la migration.

## Basculement du réseau
{: #hcxclient-planning-net-swing}

Un basculement du réseau se produit une fois que l'évacuation des machines virtuelles des réseaux côté source est terminée et que la conception et l'implémentation du réseau est terminée côté cloud. Configurer HCX pour débloquer les réseaux liés aux machines virtuelles achevées dans les vagues de migration permet aux machines virtuelles migrées de router le trafic réseau en utilisant l'infrastructure NSX côté cloud.

## Plateformes client prises en charge
{: #hcxclient-planning-client-platforms}

Pour l'extension du réseau, seuls les groupes de ports avec un commutateur distribué virtuel (vDS) vSphere sont pris en charge. Cela implique également que les hôtes ESXi autonomes ne sont pas pris en charge car vous ne pouvez avoir un vDS que lorsque les hôtes ESXi sont gérés par vCenter.
- vSphere 5.1 (ligne de commande uniquement pour vCenter 5.1 via API)
- vSphere 5.5 (interface utilisateur client Web prise en charge sur vCenter 5.5u3 et les versions ultérieures)
- vSphere 6.0
- vSphere 6.5 (vDS doit être au niveau 6.0)

## Plateformes cloud prises en charge
{: #hcxclient-planning-cloud-platforms}

Le côté cloud de HCX est fournit par l'automatisation {{site.data.keyword.cloud_notm}}.

## Options de connectivité
{: #hcxclient-planning-connect-options}

### Connectivité HCX standard
{: #hcxclient-planning-standard-connect}

Déployée par l'automatisation {{site.data.keyword.vmwaresolutions_short}}, l'installation du côté cloud de HCX est configurée par défaut pour se connecter à l'internet public.

## Liens connexes
{: #hcxclient-planning-related}

* [Glossaire des composants et des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Déploiement du client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Maillage de services sur site HCX ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Traitement des incidents dans HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

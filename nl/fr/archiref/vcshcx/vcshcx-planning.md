---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Planification de prédéploiement
{: #vcshcx-planning}

Une grande partie du temps consacré au déploiement du HCX correspond à la phase de pré-déploiement.
Alors que les projets de migration des systèmes d'information prennent généralement plusieurs mois voire plusieurs années, HCX permet des migrations et une connectivité du réseau vers le cloud immédiatement après le déploiement. Etant donné que le déploiement de HCX pour un client au niveau de l'entreprise implique généralement des équipes de sécurité, de réseau, de stockage et d'infrastructure vSphere, il est logique d'impliquer ces équipes dans la preuve de concept si possible. Une gestion de projet efficace et l'inclusion précoce des parties prenantes sont essentielles pour assurer la rapidité du déploiement et de l'exploitation du HCX.

## Eviter la paralysie d'analyse
{: #vcshcx-planning-avoiding}

La plupart des obstacles et du temps nécessaire à la migration d'une machine virtuelle ou d'un groupe de machines virtuelles sont dus à la nécessité de modifier certaines parties de l'environnement d'application, à la conception de ces changements et à la programmation des temps d'arrêt nécessaires pour effectuer ces changements. Une fois ces changements apportés, la migration devient difficile à annuler, ce qui accentue la paralysie de l'analyse. Essayer de saisir tous les aspects de la migration, de coordonner les différentes équipes et de changer les principaux intervenants dans les délais requis pour finaliser le plan peut retarder ou contraindre la réalisation du projet.

HCX permet la migration croisée d'instances vSphere d'une machine virtuelle ou d'un groupe de machines virtuelles qui représentent une application composite partielle ou complète, sans aucune modification de l'application. Pour cette raison, abandonner une migration signifie déplacer les machines virtuelles vers l'arrière ou redéployer les réseaux. Cela élimine la nécessité d'une grande partie de la planification de la migration et permet un certain parallélisme dans le processus de planification. Après avoir sélectionné les applications à déplacer et créé une conception de réseau de haut niveau, les applications peuvent commencer la migration avec une configuration minimale sur l'instance de cloud pendant que la connectivité et la conception finales du réseau sont élaborées.

## Réseaux étendus
{: #vcshcx-planning-stretched-net}

Les composants d'extension du réseau de la flotte HCX sont très stables. Chez un client particulier ayant plus de 20 VLANs répartis dans le {{site.data.keyword.cloud}} sur un réseau WAN de 1 Gbit/s partagé avec d'autres tunnels de trafic et de migration HCX, il n'y a aucun problème applicatif attribué au réseau.
Les liaisons réseau ont une durée de vie supérieure à 6 mois de cette façon.
D'autres réseaux étendus ont été ajoutés et supprimés sans problème.
Le choix d'un {{site.data.keyword.CloudDataCent_notm}} à proximité immédiate (latence < 6 ms pour ce client particulier) joue également un rôle dans la stabilité réseau d'un réseau étendu. Laisser les réseaux étendus à long terme ne devrait pas être un facteur négatif dans votre conception étant donné que vous disposez d'une bande passante suffisante et d'une latence suffisamment faible pour vos applications.


## Cycle de vie de la migration
{: #vcshcx-planning-mig-lifecycle}

Les sections suivantes décrivent les phases d'un cycle de migration HCX typique, en indiquant où des flux de travail peuvent être effectués en parallèle.

## Inventaire vSphere
{: #vcshcx-planning-vsphere-planning}

- Utilisez une application telle que [RVTOOLS](https://www.robware.net/rvtools/) pour télécharger l'inventaire du ou des vCenter(s) source sous forme de feuille de calcul.
- Evaluation grossière des machines virtuelles au sein d'une application à migrer.
Ce processus implique la compréhension des machines virtuelles qui participent à une application, sans entrer dans les détails.
- Si vous prévoyez de migrer de nombreuses machines virtuelles et que la bande passante réseau est limitée entre les sites source et cloud, regroupez les machines virtuelles par VLAN ou VXLAN si NSX est utilisé à la source. Cela permet un plan de migration HCX en cascade où les groupes de machines virtuelles par VLAN sont migrés et les réseaux L2 sur lesquels ils résident ne sont étendus que jusqu'au point où les VLAN sont évacués. Cela signifie que le groupe initial de réseaux étendus L2 connexes ne peut être libéré que lorsque la conception du réseau côté cloud est finalisée et déployée. Le déblocage implique de faire basculer le trafic VXLAN particulier vers l'infrastructure NSX de l'instance de cloud.


## Configuration réseau de base
{: #vcshcx-planning-baseline-net-config}

Créez un réseau de périmètre sécurisé dans l'instance vSphere côté cloud. Il s'agit généralement d'un appareil NSX DLR ou Edge. Si vous utilisez le routage de proximité HCX, il n'est pas nécessaire de créer de règles de pare-feu ou de topologie de liaison montante, car il peut être exécuté ultérieurement ou simultanément sans affecter le trafic L2 étendu.

## 	Extension de réseau
{: #vcshcx-planning-net-extension}

Etendre le réseau signifie simplement prendre le VLAN ou VXLAN existant de l'environnement vSphere source, représenté par un groupe de ports de commutateur distribué virtuel (vDS), et l'étendre à un VXLAN NSX sur le côté cloud du HCX.

## Tests pré-implémentation
{: #vcshcx-planning-preflight-tests}

Les tests pré-implémentation consistent à effectuer une migration HCX avec la fonction vMotion et la fonction de migration en bloc afin d'établir un taux de transfert de base.

## Migration des applications de non-production
{: #vcshcx-planning-mig-non-prod-apps}

A ce stade, la migration des machines virtuelles commence avec les vagues prévues de machines virtuelles moins critiques. Le développement, les tests, etc., utilisent la connectivité Internet pour la migration et le trafic L2 étendu.


## Début de la conception et de l'implantation du réseau cloud
{: #vcshcx-planning-cloud-net-begins}

Pendant que les migrations se poursuivent, les conceptions de réseau côté cloud sont finalisées et implémentées dans l'instance vSphere côté cloud.

## Autres considérations relatives à la connectivité du réseau
{: #vcshcx-planning-connect-considerations}

Pendant que les migrations se poursuivent, la connectivité du réseau WAN privé est commandée, car il faut généralement de quelques semaines à quelques mois pour établir une connexion avec le fournisseur de cloud. Une fois la connectivité réseau privée terminée, HCX peut être configuré pour utiliser à la fois la liaison réseau privée dédiée et Internet pour la migration et le trafic L2 étendu.

## Serveurs physiques
{: #vcshcx-planning-physical-servers}

Lorsque l'objectif est la migration du centre de données dans le cloud, tous les serveurs physiques qui interagissent avec les machines virtuelles en cours de migration peuvent être évalués pour la migration dans {{site.data.keyword.cloud_notm}} en tant que machines virtuelles (P2V), bare metal ou rester à la source. Si le serveur physique doit rester à la source, et HCX ne sera utilisé que pendant la migration jusqu'à ce qu'un réseau dédié soit établi, il est important de comprendre s'il réside sur un réseau qui est étendu dans le cloud avec HCX. Dans ce scénario, HCX permet non seulement aux machines virtuelles, mais à l'ensemble du sous-réseau de migrer dans le cloud. Pour supprimer HCX à la fin de la migration, le sous-réseau ne peut pas exister dans la source et la destination si la connexion entre les dispositifs physiques et les machines virtuelles migrées doit être maintenue. Cela implique que tous les dispositifs physiques laissés sur le site source qui existent sur des réseaux L2 étendus doivent être migrés vers un autre sous-réseau du réseau qui pourrait être routé vers le côté cloud. L'exception à cette règle est l'utilisation d'une autre technologie L2 étendue, telle que le VPN NSX L2, pour remplacer les noeuds finaux L2 étendus de HCX.

## Migration de la production et des applications complexes
{: #vcshcx-planning-mig-prod-complex-app}

Les machines virtuelles avec des VMDK partagés en mode d'écriture multiple telles que les clusters Oracle RAC ou MS Exchange/SQL ou les machines virtuelles avec des mappages de périphériques bruts sont des exemples de machines virtuelles qui nécessitent une attention particulière avant la migration.

## Basculement du réseau
{: #vcshcx-planning-net-swing}

Un basculement du réseau se produit une fois que l'évacuation des machines virtuelles des réseaux côté source est terminée et que la conception et l'implémentation du réseau est terminée côté cloud. Configurer HCX pour débloquer les réseaux liés aux machines virtuelles achevées dans les vagues de migration, permet aux machines virtuelles migrées de router le trafic réseau en utilisant l'infrastructure NSX côté cloud.

## Plateformes client prises en charge
{: #vcshcx-planning-client-platforms}

Pour l'extension du réseau, seuls les groupes de ports avec un commutateur distribué virtuel (vDS) vSphere sont pris en charge. Cela implique également que les hôtes ESXi autonomes ne sont pas pris en charge car vous ne pouvez avoir un vDS que lorsque les hôtes ESXi sont gérés par vCenter.
- vSphere 5.1 (ligne de commande uniquement pour vCenter 5.1 via API)
- vSphere 5.5 (interface utilisateur client Web prise en charge sur vCenter 5.5u3 et les versions ultérieures)
- vSphere 6.0
- vSphere 6.5 (vDS doit être au niveau 6.0)

## Plateformes cloud prises en charge
{: #vcshcx-planning-cloud-platforms}

Le côté cloud de HCX est fournit par l'automatisation d'{{site.data.keyword.cloud_notm}}.

## Options de connectivité
{: #vcshcx-planning-connect-options}

### Connectivité HCX standard
{: #vcshcx-planning-standard-connect}

Déployée par l'automatisation d'{{site.data.keyword.vmwaresolutions_short}}, l'installation du côté cloud de HCX est configurée par défaut pour se connecter à l'internet public.

### Connectivité facultative
{: #vcshcx-planning-optional-connect}

La connexion sur le réseau privé {{site.data.keyword.cloud_notm}} peut être sélectionnée au moment de la commande.

## Liens connexes
{: #vcshcx-planning-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

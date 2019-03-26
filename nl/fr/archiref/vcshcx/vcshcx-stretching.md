---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

# Extension du réseau et migration des machines virtuelles
{: #vcshcx-stretching}

## Extension du réseau
{: #vcshcx-network-stretching}

### Concepts et pratiques recommandées pour l'extension du réseau
{: #vcshcx-stretching-best-practices-network}

L'élément de jonction qui relie le réseau côté client au VXLAN côté cloud est un VPN multi-tunnel sophistiqué qui consiste en une technologie HCX propriétaire. Il n'est pas basé sur NSX, mais fonctionne avec NSX et étend ses capacités. Ce processus est contrôlé par l'interface utilisateur Web vCenter côté client et automatise le déploiement et l'affichage des points finaux côté client et côté cloud. La sélection du réseau à étendre se fait individuellement ou par lots.

En outre, dans le cadre du flux de travail de l'extension du réseau, NSX du côté cloud est autorisé à construire un VXLAN qui est ensuite connecté à une interface créée sur le périphérique L3 spécifié côté cloud (DLR ou ESG laissé dans un état non connecté) et le dispositif L2C côté cloud.

Généralement, lorsque vous migrez une application particulière, tous les réseaux utilisés par les machines virtuelles applicables doivent être étendus à l'ensemble de l'instance {{site.data.keyword.cloud}}.

Pourquoi généralement et pas toujours ? Il peut être avantageux de déconnecter certains trafics du côté client après la migration de la machine virtuelle. Par exemple, les clients de sauvegarde invités des machines virtuelles, qui peuvent entraîner une utilisation importante de la bande passante lorsqu'ils sont déplacés vers le cloud. Le client de sauvegarde invité n'est pas nécessaire lors de la migration de la machine virtuelle car il est automatiquement récupéré par une sauvegarde plus moderne au niveau du bloc côté cloud.

L'adaptateur réseau de sauvegarde du client n'est pas connecté car cela reviendrait à accéder à chaque machine virtuelle pour fermer le programme de sauvegarde du client invité. Par conséquent, si un réseau de sauvegarde est utilisé, la sauvegarde risque d'échouer. Il s'agit d'une situation temporaire jusqu'à ce que toutes les machines virtuelles puissent être atteintes après la migration pour désactiver le client de sauvegarde invité.

La bande passante d'un seul L2C est théoriquement de 4 Gbit/s, mais cela peut être la limite pour tous les réseaux étendus au sein d'une seule paire L2C et n'est pas réalisable avec un seul réseau étendu. Un seul réseau étendu peut atteindre environ 1 Gbits/s étant donné qu'il y a suffisamment de bande passante sous-jacente allouée et que la latence est faible (<~10 ms).

### Processus d'extension d'un réseau
{: #vcshcx-stretching-process-stretch}

Pour étendre un réseau (VLAN ou VXLAN) avec HCX, suivez les étapes suivantes à partir de l'interface web vCenter côté client.

1. Pour la sélection individuelle des groupes de ports, naviguez jusqu'à l'onglet **Networks** dans l'interface utilisateur Web vCenter, faites un clic droit sur le réseau à étendre et sélectionnez **Hybridity Actions-> Extend Networks to the Cloud**.
2. Côté cloud, sélectionnez le périphérique L3 à connecter et le dispositif L2C qui sera utilisé. Tapez la passerelle par défaut actuelle et le masque de sous-réseau au format CIDR.
3. Cliquez sur **Stretch** au bas de l'écran pour lancer le flux d'extension du réseau.

La progression du réseau est surveillée dans le panneau des tâches du client vCenter.

### Option de routage de proximité
{: #vcshcx-stretching-prox-routing}

Sans aucun type d'optimisation des routes, les réseaux étendus retournent vers le côté client pour tout accès L3. Ce phénomène de trombone introduit un modèle de trafic inefficace car les paquets doivent faire la navette entre le client (source) et le cloud, même dans les cas où les machines virtuelles source et de destination se trouvent dans le cloud. La fonction de routage de proximité du HCX a été conçue pour répondre à ce problème et à l'évacuation locale du trafic.

## vMotion
{: #vcshcx-stretching-vmotion}

La fonctionnalité vMotion de HCX étend la capacité de vSphere vMotion pour fonctionner sur différentes versions de vSphere, des domaines SSO distincts et divers types de connectivité réseau sur Internet. HCX suppose que le réseau sur lequel il se connecte n'est pas sécurisé et transfère toujours le trafic dans des tunnels cryptés, quel que soit le type de connectivité utilisé.

### Concepts et pratiques recommandées pour vMotion
{: #vcshcx-stretching-best-practices-vmotion}

HCX est essentiellement un proxy bidirectionnel vMotion. Chaque instance de HCX émule un seul hôte ESXi dans le centre de données vSphere, en dehors de tout cluster qui est lui-même un "front" pour le composant de flotte de la passerelle de cloud (CGW). Un hôte proxy apparaît pour chaque site HCX qui est lié au site actuellement consulté. Lorsqu'une vMotion est initiée vers un hôte distant, l'hôte ESXi local va transférer cette machine virtuelle vers l'hôte ESXi proxy local qui fait face à la passerelle CGW et qui maintient également un tunnel crypté avec la passerelle CGW du côté distant.

En même temps, une migration vMotion est lancée de l'hôte proxy ESXi distant vers l'hôte ESXi physique vSphere de destination, alors qu'il reçoit les données de la passerelle CGW source via le tunnel. Lorsqu'une migration vMotion est utilisée, contrairement à l'option de migration en bloc, une seule opération de migration de machine virtuelle est exécutée à la fois. Pour cette raison, en cas de migration d'un grand nombre de machines virtuelles, il est recommandé de ne l'utiliser que lorsque les temps d'arrêt ne sont pas envisageables ou lorsqu'il existe un risque de redémarrage de la machine virtuelle. Cependant, comme pour la vMotion standard, la machine virtuelle peut être sous tension pendant le processus.

Il a été constaté qu'une seule vMotion peut atteindre environ 1,7 Gbits/s sur le LAN et 300 à 400 Mbits/s sur le WAN grâce à l'optimiseur de réseau WAN. Cela ne signifie pas que 1,7 Gbits/s sur le réseau LAN équivaut à 400 Mbits/s sur le réseau WAN grâce à l'optimiseur de réseau WAN, mais uniquement que ces valeurs maximales ont été observées dans des environnements spécifiques. L'environnement sur lequel cela a été observé consistait en un réseau LAN vMotion de 10 Go et une liaison Internet montante de 1 Go, partagés avec le trafic Web de production.

Utilisez vMotion lorsque :
- La machine virtuelle est difficile à éteindre, à démarrer ou le temps de fonctionnement peut être long et présenterait un risque en l'éteignant.
- Une application de type cluster nécessite des UUID de disque, comme les clusters Oracle RAC. Notez que vMotion ne change pas les UUID de disque sur la destination.
- Vous souhaitez déplacer une seule machine virtuelle le plus rapidement possible.
- Une migration programmée n'est pas nécessaire.

### Fonctionnement
{: #vcshcx-stretching-operation}

Utilisez le portail snap-in de l'interface Web HCX ou les menus d'extension contextuels du client vSphere Web Client pour initier une migration vMotion entre clouds. Dans les deux cas, le même assistant de migration démarre. Dans les menus contextuels, une seule machine virtuelle est sélectionnée pour les opérations de migration. Dans le portail, plusieurs machines virtuelles peuvent être sélectionnées.

La migration inverse des machines virtuelles n'est possible qu'à partir du portail de l'interface utilisateur Web, en cochant la case **Reverse migration** dans l'assistant de migration HCX.

## Migration en bloc
{: #vcshcx-stretching-bulk-mig}

### Concepts et pratiques recommandées pour la migration en bloc
{: #vcshcx-stretching-best-practices-bulk-mig}

La fonction de migration en bloc de HCX utilise la réplication vSphere pour migrer les données du disque tout en recréant la machine virtuelle sur l'instance vSphere HCX de destination. Une migration d'une machine virtuelle implique les actions suivantes :
- Création d'une nouvelle machine virtuelle du côté de la destination et de ses disques virtuels correspondants.
- Réplication des données de machine virtuelle sur la nouvelle machine virtuelle. La réplication démarre dès que l'assistant termine, indépendamment du basculement de la planification.
- Mise hors tension de la machine virtuelle d'origine.
- Durant la période de mise hors tension, la réplication finale de toutes les modifications de données se produit.
- Mise sous tension de la nouvelle machine virtuelle du côté de la destination.
- Changement de nom et déplacement de la machine virtuelle d'origine vers le dossier de cloud vers lequel elle a été déplacée. 

Les avantages de la migration en bloc par rapport à la migration vMotion sont les suivants :
- Migration simultanée de plusieurs machines virtuelles.
- Utilisation plus cohérente de la bande passante. La migration vMotion peut générer des fluctuations dans l'utilisation de la bande passante qui seraient visibles sous forme de pics et de creux dans les outils de surveillance du réseau ou dans l'interface utilisateur de l'optimiseur de réseau WAN.
- La migration en bloc permet d'obtenir une utilisation globale de la bande passante du réseau supérieure à celle d'une migration vMotion.
- La migration en bloc peut être programmée pour basculer vers les machines virtuelles nouvellement migrées au cours d'une interruption de service programmée.
- Possibilité de migrer des machines virtuelles qui utilisent des fonctions d'unités centrales virtuelles différentes de celles du côté cloud. La migration vMotion pourrait échouer dans ces cas-là. 

Les inconvénients de la migration en bloc par rapport à la migration vMotion sont les suivants :
- La migration des machines virtuelles individuelles est plus lente qu'avec la migration vMotion.
- La machine virtuelle subit un bref temps d'arrêt lorsque la nouvelle machine virtuelle clonée est affichée du côté de la destination.
- Les machines virtuelles qui dépendent de l'ordre des disques et des UUID de disque (Oracle RAC) peuvent avoir des problèmes et avoir des disques qui apparaissent différemment lorsque les UUID sont modifiées, ce qui peut modifier les chemins d'accès du système d'exploitation vers les périphériques de disque virtuel.

## Pratiques recommandées pour chaque type de migration
{: #vcshcx-stretching-mig-type-best-practices}

### Clusters à disque partagé
{: #vcshcx-stretching-shared-disk-clusters}

Les clusters Oracle RAC, MS Exchange et MS-SQL sont des exemples d'applications où deux machines virtuelles ou plus participent à un cluster qui nécessite un disque partagé entre toutes les machines virtuelles ou noeuds de cluster. L'indicateur d'écriture multiple de VMware doit être activé sur tous les noeuds des machines virtuelles pour les disques qui font partie du cluster d'applications (disques virtuels autres que ceux du système d'exploitation). Les machines virtuelles dont l'indicateur d'écriture multiple est activé pour tous les disques virtuels ne sont pas prises en charge.

Migration d'un cluster ayant activé les disques virtuels à écriture multiple :
- vMotion est utilisée car les mappages d'origine du disque de machine virtuelle et de l'UUID sont maintenus.
- Le cluster reste à l'état dégradé (noeud unique) durant la migration.
- Le cluster subit un temps d'arrêt avant le début de la migration et après que la migration soit terminée pour réassembler la configuration d'écriture multiple entre les machines virtuelles du cluster.

Effectuez les opérations suivantes pour migrer un cluster avec disque à écriture multiple activé :
1. Mettez hors tension le cluster et tous les noeuds conformément aux pratiques recommandées de l'application.
2. Prenez note de l'ordre des disques, si l'application l'exige, dans chaque noeud de machine virtuelle pour les disques virtuels configurés en écriture multiple.
3. Pour Oracle et toute autre application qui utilise la fonctionnalité UUID du disque virtuel, connectez-vous à un hôte ESXi particulier et exécutez la commande `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` pour obtenir l'UUID de chaque fichier de disque virtuel nécessitant que l'indicateur d'écriture multiple soit défini pour le cluster.
  Ceci est nécessaire lorsqu'il est conseillé d'aligner l'ordre des disques sur l'affichage du chemin dans le système d'exploitation. vMotion peut réorganiser les disques (disque 1, disque 2, disque 3) mais les UUID restent les mêmes.
  Une fois la migration terminée, utilisez l'UUID noté pour mapper les informations de disque, pour recréer l'ordre de nommage des disques, et l'ID SCSI, si besoin. L'application doit fonctionner d'une manière comme de l'autre. On l'utilise lorsqu'une instance Oracle possède un grand nombre de disques virtuels mappés, pour le dépannage de l'application.
4. Retirez les disques virtuels de toutes les machines virtuelles de cluster, à l'exception de celles du cluster principal. 
5. Supprimez l'indicateur d'écriture multiple de la machine virtuelle du cluster principal qui devrait être la seule à posséder les disques du cluster actuellement.
6. Mettez sous tension le cluster principal, si nécessaire pour réduire au minimum les temps d'arrêt.
7. Migrez tous les noeuds de cluster avec vMotion. Commencez par migrer le cluster principal. Faites migrer tous les autres noeuds après les avoir mis hors tension. 
8. Lorsque le noeud propriétaire du disque principal termine la migration, mettez-le hors tension.
9. Si nécessaire, remappez l'ordre des disques avec l'UUID de disque et l'ID SCSI appropriés. Le remappage n'est pas nécessaire pour que l'application fonctionne.
10. Ré-activez l'indicateur d'écriture multiple sur le noeud principal.
11. Démarrez le noeud principal et vérifiez le fonctionnement.
12. Mappez les disques et activez l'indicateur d'écriture multiple sur toutes les autres machines virtuelles du cluster et mettez-les sous tension.
13. Vérifiez le fonctionnement de tous les autres clusters. 

### Machines virtuelles générales
{: #vcshcx-stretching-general-vms}

Une fois que la confiance s'est construite autour du fonctionnement de HCX, la migration en bloc doit être utilisée. La migration en bloc est nécessaire en cas d'applications redondantes. Par exemple, en cas de serveurs Web et lorsque plusieurs centaines ou plusieurs milliers de machines virtuelles doivent être migrées.

### Machines virtuelles utilisant un serveur d'accès au réseau direct
{: #vcshcx-stretching-vms-direct-nas}

La technologie NFS est généralement utilisée pour partager des données sur de nombreux serveurs, tels que des contenus de serveurs Web. La technologie iSCSI peut être utilisée sur tous les noeuds de machine virtuelle qui comprennent un cluster d'applications comme la messagerie ou les SGBDR, et elle est généralement plus sensible à la latence que NFS.

Dans un cas comme dans l'autre, si la latence peut être maintenue faible dans {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms pour iSCSI et ce que l'application tolère pour NFS) et si l'application fonctionne avec un débit de 1 Gbits/s ou inférieur, alors le réseau NAS peut être étendu avec HCX à un emplacement {{site.data.keyword.clou_notm}}. Après cela, les machines virtuelles peuvent être migrées / transférées via vMotion avec HCX comme d'habitude.

Après la migration, les volumes iSCSI peuvent être dupliqués avec le système d'exploitation vers une autre solution de stockage en cloud local et les données NFS peuvent être répliquées vers n'importe quelle solution de cloud. Les considérations suivantes doivent être prises en compte :
- Latence (iSCSI ou tolérance d'application pour NFS)
- Bande passante (~1 Gbits/s pour un réseau étendu)
- Bande passante sous-jacente de la liaison

Après le cycle de vie de la migration, testez les applications de développement ou de préproduction avant de passer en production. La QoS peut être utilisée pour le trafic tunnel sous-jacent (udp 500/4500) entre les dispositifs L2C de HCX qui prennent en charge des réseaux L2 étendus sensibles à la latence.

## Basculement du réseau
{: #vcshcx-stretching-network-swing}

Si le but est d'évacuer le centre de données dans {{site.data.keyword.cloud_notm}}, alors l'avant-dernière étape avant la suppression du HCX est le basculement du réseau. Le basculement du réseau permet une migration du sous-réseau du réseau qui héberge les machines virtuelles migrées du centre de données source vers un réseau dissocié NSX dans {{site.data.keyword.cloud_notm}}.

Pour procéder au basculement du réseau, procédez comme suit :
- Vérifiez que le réseau est libéré de toutes les charges de travail et que tous les périphériques qui ne sont pas des machines virtuelles sur le réseau sont déplacés vers un autre réseau, migrés fonctionnellement vers le cloud ou dépréciés.
- Vérifiez que toute topologie NSX ou toute topologie de réseau prenant en charge {{site.data.keyword.cloud_notm}} est compatible avec le basculement de réseau. Par exemple, les protocoles de routage dynamique et les pare-feu.
- Exécutez un flux de travail de réseau non étendu HCX dans l'interface utilisateur et sélectionnez l'appareil NSX de routage approprié pour prendre le contrôle de la passerelle par défaut du réseau non étendu.
- Exécutez tout changement de routage externe. Par exemple, insérez un routage modifié pour les réseaux qui ont été migrés, supprimez les routes au site source dans le réseau migré, et assurez-vous que le routage vers le sous-réseau migré sur tout le réseau WAN fonctionne toujours pour les applications non migrées. 
- Réalisez un test d'application propriétaire sur toutes les applications migrées depuis tous les points d'accès possibles : internet, intranet et VPN.

Imaginons que vous souhaitiez effectuer le basculement réseau d'une application spécifique dont toutes les machines virtuelles sont complètement migrées vers le cloud. Par exemple :
- Vous utilisez un pare-feu Vyatta sur le réseau privé pour insérer des routes dans votre cloud MPLS et créer un tunnel vers les dispositifs de routage de périphérie sur le MPLS afin d'éviter tout espace d'adresse IP dans {{site.data.keyword.cloud_notm}}. 
- Votre compte est défini en tant que compte VRF {{site.data.keyword.cloud_notm}}.
- Certaines applications se trouvent derrière une adresse IP virtuelle avec équilibrage de charge réseau. Ces adresses IP virtuelles se trouvent sur votre sous-réseau propriétaire qui réside sur un F5 virtuel derrière Vyatta.

Même si l'ajout d'un routage plus spécifique dans le MPLS pour les réseaux qui sont basculés vers {{site.data.keyword.cloud_notm}} via HCX fonctionne bien pour les autres réseaux, elle ne fonctionne pas pour les adresses IP virtuelles individuelles car une route /32 est ajoutée.

Solution : il est courant pour les fournisseurs WAN de filtrer les routes /32 qui sont ajoutées. Travaillez avec le fournisseur de réseau WAN pour permettre cela.

Tenez compte des considérations et implications suivantes :
- Les applications qui partagent un sous-réseau, un réseau vLAN et un réseau VXLAN doivent être déplacées ensemble.
- Les applications se trouvant derrière un équilibreur de charge utilisant une adresse IP interne routable peuvent nécessiter des changements au niveau du routage si elles ne peuvent pas être déplacées ensemble ou s'il n'est pas souhaitable de le faire. Par exemple, si le fait d'impliquer un trop grand nombre d'applications dans un seul basculement représente un risque trop important.
- Les administrateurs VMware, les administrateurs de réseau (y compris les clients/fournisseurs de WAN) et les propriétaires d'applications doivent être impliqués, même s'il n'y a aucun impact prévu sur un système ou un équipement réseau spécifique. 

## Liens connexes
{: #vcshcx-stretching-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

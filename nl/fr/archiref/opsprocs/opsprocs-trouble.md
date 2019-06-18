---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# Dépannage
{: #opsprocs-trouble}

Pour dépanner les problèmes de votre instance vCenter Server, vos administrateurs système doivent identifier les symptômes du problème, déterminer quels composants de la solution sont affectés, rechercher et proposer une correction ou une solution de contournement, et tester le correctif.

* Identification des symptômes - Un certain nombre de causes potentielles peuvent conduire à la sous-performance ou à la non-performance de votre instance. La première étape d'un dépannage efficace consiste à identifier exactement ce qui ne va pas. Ces symptômes peuvent être signalés par les événements et les alarmes vSphere, la gestion des opérations dans	{{site.data.keyword.cloud}} ou via votre centre de services par l'un de vos utilisateurs.
* Isoler les composants affectés - Après avoir identifié les symptômes du problème, vous devez identifier les composants logiciels ou matériels qui sont affectés et qui pourraient causer le problème et ceux qui ne sont pas impliqués. Des outils tels que vCenter Operations Management dans {{site.data.keyword.cloud_notm}} vous assistent dans cette étape.
* Proposer un correctif ou une solution de contournement - Une fois que vous avez compris les symptômes et isolé les composants, vous pouvez rechercher des correctifs et des solutions de contournement possibles. Vos administrateurs système utilisent également le portail {{site.data.keyword.cloud_notm}}, y compris les scénarios de dépannage de ce document ainsi que IBM ServiceNow et la base de connaissance VMware. En outre, il existe de nombreux wikis et blogues qui peuvent vous aider. Pour des résolutions encore plus rapides, la gestion des opérations dans {{site.data.keyword.cloud_notm}} inclut un certain nombre de mesures correctives pour les problèmes identifiés.
* Tester les solutions possibles - Lorsque vous connaissez les symptômes du problème, les composants impliqués et que vous avez proposé une solution, vos administrateurs système testent systématiquement les solutions jusqu'à ce que le problème soit résolu.

vSphere comprend un sous-système d'événements et d'alarmes configurables par l'utilisateur qui suit les événements qui se produisent dans l'environnement vSphere et stocke les données dans des fichiers journaux et dans la base de données vCenter. Ce sous-système permet également aux administrateurs système de spécifier les conditions dans lesquelles les alarmes sont déclenchées. Les alarmes changent d'état, passant d'avertissements à des alertes plus graves au fur et à mesure que l'état du système change, et peuvent déclencher des actions d'alarme automatisées telles que l'envoi d'un courrier électronique à l'équipe d'administrateurs système. Cette fonctionnalité est utile lorsque vous souhaitez être informé ou prendre des mesures immédiates lorsque certains événements ou certaines conditions surviennent pour un objet d'inventaire ou un groupe d'objets spécifique. 

Des outils supplémentaires tels que ceux incorporés dans la gestion des opérations sur l'architecture {{site.data.keyword.cloud_notm}} vous offrent en outre une aide complémentaire pour identifier les symptômes, isoler les composants affectés et proposer une correction ou une solution de contournement.

## Directives
{: #opsprocs-trouble-guidelines}

Les directives suivantes sont considérées comme les meilleures pratiques pour le dépannage de vos problèmes dans {{site.data.keyword.vmwaresolutions_short}} :
* Abordez le dépannage et la résolution de problèmes de façon systématique.
* Les symptômes sont-ils liés à la disponibilité, à l'utilisation ou à la configuration ? 
 *  Disponibilité - Ces symptômes sont liés à la disponibilité des composants matériels et logiciels et se caractérisent par une absence de réponse. Souvent, la conception haute disponibilité masque ces problèmes afin qu'ils n'aient pas d'impact direct sur votre charge de travail et vos utilisateurs.
 * Utilisation - Ces symptômes sont liés à la capacité et à la performance et se caractérisent par un fonctionnement lent ou une incapacité de chargement. Une gestion proactive de la capacité réduit considérablement ces problèmes.
 * Configuration - Ces problèmes sont généralement découverts lors de la fourniture de nouveaux services ou lors de l'application d'un changement. Des réglages incorrects peuvent apparaître comme des symptômes de disponibilité ou d'utilisation. Par exemple, une adresse IP incorrecte s'affiche comme un problème de disponibilité, alors que les paramètres de RAM de la machine virtuelle étant trop bas, des symptômes d'utilisation apparaissent.
* Essayez de rattacher le problème à un composant de l'environnement.
* Prenez des notes afin de pouvoir suivre vos démarches.
* Localisez et documentez vos versions de logiciels.
* Documentez l'utilisation de vos sous-réseaux et de vos adresses IP, y compris les adresses VIP et NAT.
* Obtenez des diagrammes de votre réseau. Vous avez besoin d'un certain nombre de diagrammes qui montrent la couche physique (sous-couche) et la couche logique (superposition).
* Prenez connaissance de tout changement récent dans l'environnement.
* Faites des recherches sur l'impact du correctif, ne vous fermez pas l'accès aux interfaces de gestion.
* Assurez-vous d'avoir des sauvegardes de tous les composants clés, au cas où ils auraient besoin d'être rechargés ou réinitialisés.
* Ne changez pas plus d'une chose à la fois.
* Documentez chaque changement et son résultat.
* Lorsque vous présentez une demande de support, assurez-vous de bien la documenter et de fournir des informations pertinentes. Soyez très clair dans les symptômes que vous voyez et identifiez les composantes que vous croyez être en cause. Assurez-vous d'utiliser la bonne terminologie. Essayez de minimiser toute confusion ou ambiguïté dans votre choix de mots.
* Les fichiers de configuration de vSphere ESXi et vCenter Server contrôlent le comportement du système, comprennent où ils se trouvent. La plupart des paramètres du fichier de configuration sont définis pendant l'installation, mais peuvent être modifiés après l'installation.
* Les fichiers journaux capturent les messages générés par le noyau et les différents sous-systèmes et services. Les services vSphere ESXi et vCenter maintiennent des fichiers journaux séparés, comprennent où ils se trouvent et comment y accéder.
* Comprenez comment utiliser les outils d'administration système les plus répandus pour vous aider dans le diagnostic.

Pour plus d'information, voir [Troubleshooting Guidelines KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}.

## Dépannage avec les fichiers journaux
{: #opsprocs-trouble-logs}

Les fichiers journaux sont une excellente source d'information pour dépanner les problèmes, mais dans la pratique, le nombre de fichiers journaux et le grand nombre d'entrées dans chaque journal rendent la tâche difficile. Le document [Troubleshooting with Log Files KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} décrit où se trouvent ces fichiers journaux dans l'environnement VMware. En raison du nombre de fichiers journaux et du grand nombre d'entrées dans chaque journal, envisagez de faire appel aux outils de la gestion des opérations sur {{site.data.keyword.cloud_notm}} pour vous aider à capturer et à analyser des journaux des événements.

## Dépannage des scénarios courants
{: #opsprocs-trouble-common}

Afin de mieux isoler les composants affectés, cette documentation sur le dépannage de scénarios courants a été classée comme suit :

* Machines virtuelles - ces rubriques de dépannage fournissent des conseils sur les problèmes potentiels sur les machines virtuelles.
* Hôtes - ces rubriques de dépannage fournissent des conseils sur les problèmes rencontrés sur les hôtes vSphere ESXi.
* Cluster - ces rubriques de dépannage fournissent des conseils sur la disponibilité et la gestion des ressources.
* Stockage - ces rubriques de dépannage fournissent des conseils sur la résolution des problèmes de stockage liés à vSAN et NFS.
* Réseau - ces rubriques de dépannage fournissent des conseils sur la résolution des problèmes de réseau.
* vCenter - ces rubriques de dépannage fournissent des conseils sur la résolution des problèmes liés à vCenter.
* Licences - ces rubriques de dépannage fournissent des conseils pour résoudre les problèmes de licence. Ceux-ci concernent généralement les clients qui ont apporté leurs propres licences dans {{site.data.keyword.cloud_notm}}.

### Machines virtuelles
{: #opsprocs-trouble-common-vm}

Tableau 1. Dépannage des machines virtuelles

| Titre | Description |
|---|---|
| Dépannage générique des machines virtuelles | Pour plus d'informations, voir [Dépannage des machines virtuelles](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}. |
| Problèmes de performances des machines virtuelles | Pour plus d'informations sur le dépannage des symptômes des problèmes de performances des machines virtuelles, y compris le démarrage lent des systèmes d'exploitation invités, les mauvaises performances des applications, les délais de lancement ou la non réactivité des applications, voir [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}. |
| Récupération des machines virtuelles orphelines | Pour plus d'informations sur la récupération des machines virtuelles orphelines, qui sont des machines virtuelles qui existent dans la base de données vCenter, mais ne sont pas reconnues par l'hôte vSphere ESXi, voir [Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}. |
| La machine virtuelle ne s'allume pas | Pour plus d'informations, voir [Troubleshooting a virtual machine that is unable to power on (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}. |
| La machine virtuelle ne s'allume pas après le clonage ou le déploiement à partir d'un modèle | [L'article VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window} examine les problèmes qui affectent une machine virtuelle après qu'elle a été clonée ou déployée à partir d'un modèle. |
| Les outils VMware sont obsolètes ou ne sont pas installés - Les outils VMware doivent être installés sur les machines virtuelles et tenus à jour. | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} fournit des conseils sur ces tâches. |
| Dispositifs réseau de machines virtuelles anciens | Si les dispositifs réseau de machines virtuelles ne sont pas tenus à jour, les performances du réseau et, par conséquent, les performances des applications peuvent être affectées. Pour plus d'informations sur le déploiement d'un nouveau pilote et dispositif de réseau virtuel, voir [Choosing a network adapter for your virtual machine (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}. |
| Limite de mémoire de la machine virtuelle | Les limites de mémoire sont souvent utilisées, cependant, si un système d'exploitation invité ne peut pas accéder à la mémoire dont il a besoin, les applications à l'intérieur du système d'exploitation invité peuvent présenter de mauvaises performances. Pour plus d'informations sur la résolution du problème, voir [Configuring Resource Allocation Settings](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}. |
| Instantanés de machines virtuelles | Bien que les instantanés soient très utiles, la quantité et l'âge des instantanés d'une machine virtuelle ont un impact direct sur la performance de la machine virtuelle. Pour plus d'informations sur la résolution du problème, voir [Consolidate Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}. |
| Consignation des machines virtuelles | Si la consignation n'a pas été configurée correctement, la capacité du magasin de données pourrait être affectée de manière négative. Pour plus d'informations sur la résolution du problème, voir [Configuring Logging Levels for the Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}. |
| Dépannage des problèmes de connexion réseau | Les symptômes peuvent inclure l'échec de la connexion de la machine virtuelle au réseau ou l'absence de connectivité réseau vers ou depuis une machine virtuelle donnée. Pour plus d'informations sur la résolution du problème, voir [Troubleshooting virtual machine network connection issues (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}.  |
| Déterminer si plusieurs unités centrales virtuelles causent des problèmes de performance | Pour en savoir plus sur le dépannage des machines virtuelles rencontrant des problèmes de performances lorsqu'elles sont configurées avec plusieurs unités centrales, voir [Determining if multiple virtual CPUs are causing performance issues (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. Ces problèmes peuvent inclure des vitesses de transfert médiocres lors de la copie de données vers ou à partir d'une machine virtuelle, le dépassement du délai de sauvegarde ou des tâches très lentes, ou des performances insuffisantes d'une machine virtuelle.  |
| Une machine virtuelle a été mise hors tension ou redémarrée | Pour plus d'informations sur la résolution du problème, voir [Determining why a virtual machine was powered off or restarted (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. |
| Une ou plusieurs de vos machines virtuelles ont un temps de réponse faible | Pour plus d'informations sur l'isolement d'un problème de performance sur un hôte vSphere ESXi, voir [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Les problèmes de performance peuvent être causés par des contraintes de l'unité centrale, une surcharge mémoire, une latence du stockage ou une latence du réseau. |

### Hôtes vSphere ESXi
{: #opsprocs-trouble-common-host}

Tableau 2. Dépannage typique des hôtes vSphere ESXi

| Titre | Description |
|---|---|
| Commandes ESXI |Pour obtenir un aperçu des interfaces de ligne de commande dans vSphere, des commandes ESXi Shell et des commandes vCLI (VMware vSphere Command-Line Interface), voir [Getting Started with vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}. |
| Etat de l'hôte vSphere HD | Si vCenter signale un état de l'hôte vSphere HD qui indique une condition d'erreur sur l'hôte, il convient d'y remédier car ce problème peut empêcher vSphere HA de redémarrer les machines virtuelles après une panne. Pour plus d'informations, voir [Troubleshooting vSphere HA Host States](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}. |
| L'hôte vSphere ESXi est dans un état de non-réponse | Pour obtenir des informations sur le dépannage d'un hôte vSphere ESXi affichant un état de non-réponse ou de déconnexion ou lorsque les machines virtuelles présentes sur l'hôte sont grisées dans vCenter, voir [ESX/ESXi hosts do not respond and is grayed out (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}. |
| Lors de la mise sous tension d'une machine virtuelle, vous voyez une erreur Fichier non trouvé | Pour plus d'informations sur la recréation d'un fichier descripteur de disque virtuel perdu (VMDK), voir [Recreating a missing virtual machine disk descriptor file (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}. |
| Problèmes de performances de la machine virtuelle | Pour plus d'informations sur l'isolement d'un problème de performance sur un hôte vSphere ESXi, voir [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Les problèmes de performance peuvent être causés par des contraintes de l'unité centrale, une surcharge mémoire, une latence du stockage ou une latence du réseau. |
| Le serveur bare metal est en panne | Si le Bare Metal Server exécutant vSphere ESXi ne répond pas ou est éteint, connectez-vous à l'interface utilisateur ou à la console de gestion d'{{site.data.keyword.cloud_notm}} et vérifiez le statut. Si nécessaire, ouvrez un cas pour obtenir de l'aide avec votre serveur bare metal. Pour plus d'informations, voir [Utilisation de cas de support](/docs/get-support?topic=get-support-open-case#open-case){:new_window}.|
| L'hôte vSphere ESXi est déconnecté ou ne répond pas | Pour plus d'informations, voir [Troubleshooting an ESXi/ESX host in non responding state (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}. |
| PSOD (Purple screen of death)  | Le Purple Screen of Death (PSOD) est une panique du noyau. Le noyau vSphere ESXi (vmkernel) déclenche cette mesure de sécurité en réponse à un événement ou à une erreur qui est irrécupérable et signifierait que la poursuite du fonctionnement poserait un risque élevé pour les services et les machines virtuelles. Lorsque la panique se produit et que l'hôte vSphere ESXi tombe en panne, il met fin à tous les services qui s'exécutent sur lui et à toutes les machines virtuelles hébergées. Les machines virtuelles ne sont pas éteintes en douceur, mais mises hors tension de façon subite. Si l'hôte fait partie d'un cluster et que vous avez configuré la haute disponibilité, ces machines virtuelles sont redémarrées sur les autres hôtes du cluster. Pour plus d'informations, voir [Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}. |

### Stockage
{: #opsprocs-trouble-common-storage}

Tableau 3. Dépannage typique du stockage

| Titre | Description |
|---|---|
| Dépannage du stockage | Pour plus d'informations sur les performances lentes, les pannes imprévisibles, la corruption de disque ou la corruption des machines virtuelles, voir [Troubleshooting storage issues when using VMware products (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}. |
| Dépannage du réseau de stockage virtuel | Pour plus d'informations, voir [Failure Handling in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}.  |
| Défaillance du disque du réseau de stockage virtuel  | Pour plus d'informations sur l'identification d'un disque défectueux et la demande de remplacement, voir [A hard disk/magnetic disk in a VMware vSAN disk group fails (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}. |
| Elimination des problèmes de santé du réseau de stockage virtuel | Des alertes et des avertissements concernant des problèmes liés à l'état de santé du réseau de stockage virtuel peuvent s'afficher sur la page Moniteur du client Web VMware vSphere. Pour obtenir des informations sur l'élimination de ces problèmes, voir [Avertissements et alertes concernant l'état de santé du SAN virtuel](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}.|
| Rééquilibrage du réseau de stockage virtuel | Si les disques signalent des erreurs dans le bilan de santé indiquant que le cluster est déséquilibré et qu'il y a des disques qui utilisent beaucoup d'espace alors que d'autres sont très peu utilisés, vous devriez procéder à un rééquilibrage proactif. Ceci déclenche manuellement un rééquilibrage des objets dans un cluster vSAN. Pour plus d'informations sur le rééquilibrage proactif du réseau de stockage virtuel et quand il peut être applicable, voir [vSAN proactive rebalance (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}. |
| Lancement du test de santé du réseau de stockage virtuel | Si vous pensez qu'il y a un problème avec vSAN, vous pouvez lancer un test de santé pour vérifier que les composants du cluster fonctionnent comme prévu. L'exécution du test de création de machine virtuelle crée une machine virtuelle sur chaque hôte du cluster, puis la supprime. Si ces tâches aboutissent, les composants du cluster fonctionnent comme prévu et le cluster est fonctionnel. Le test de performance réseau est ensuite utilisé pour détecter et diagnostiquer les problèmes de connectivité, et pour s'assurer que la bande passante réseau entre les hôtes est adéquate. Pour plus d'informations, voir [Proactive Tests](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}. |
| Surveillance de la performance du réseau de stockage virtuel | Pour plus d'informations, voir [Monitoring vSAN Performance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}. Des tableaux de performances sont disponibles pour les clusters, les hôtes, les disques physiques, les machines virtuelles et les disques virtuels. |
| Dépannage du réseau de stockage virtuel | Pour plus d'informations, voir [Handling Failures and Troubleshooting vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}. |


### Réseau
{: #opsprocs-trouble-common-network}

Tableau 4. Dépannage typique du réseau

| Titre | Description |
|---|---|
| La partition /var/log de NSX Edge est pleine sur le serveur de périphérie actif | Pour plus d'informations sur une solution de contournement si vous êtes averti que le disque du serveur de périphérie se remplit et découvrez que la partition /var/log est saturée, voir [NSX Edge /var/log is getting full on active Edge (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}.  |
| Test de la bande passante HCX  | Pour plus d'informations sur l'utilisation de 'tests de performance' pour trouver la bande passante disponible dans les tunnels HCX si vous pensez avoir un problème de bande passante réseau avec HCX, voir [Steps to Run Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}. Des essais bidirectionnels sont effectués pour chaque test de performance. Pour la paire de passerelles, l'un s'effectue à l'intérieur du centre de données source, que nous appelons OnPrem et l'autre dans {{site.data.keyword.cloud_notm}}. Pour le test de performance, l'expéditeur d'essayer d'envoyer aussi vite que le lien le permet. Par conséquent, pour chaque test, vous verrez un taux "expéditeur" plus élevé que le taux "récepteur" et vous pouvez prendre le taux "récepteur" comme résultat de débit unidirectionnel. |
| Traitement des incidents dans HCX | Pour plus d'informations, voir [Traitement des alarmes dans HCX](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-troubleshooting#vcshcx-troubleshooting){:new_window}. |
| Etat de synchronisation avec une progression de 0 % et 0 octets et erreur de statut dans HCX | Pour plus d'informations, voir [HCX replication are in Syncing state with 0% progress and 0 bytes with status Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}. |
| Faible performance du réseau de machines virtuelles | Passez en revue les paramètres de la carte réseau virtuelle des machines virtuelles. VMware recommande les cartes réseau virtuelles VMXNET 3 pour les machines virtuelles car il s'agit de la dernière génération de cartes réseau paravirtualisées conçues dès le départ pour la performance. Vérifiez la compatibilité de VMXNET 3 à l'aide de la liste de compatibilité VMware et, si elle est prise en charge, modifiez la carte réseau virtuelle pour améliorer les performances du réseau. Pour plus d'informations, voir [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

Tableau 5. Dépannage typique de vCenter

| Titre | Description |
|---|---|
| Accès à la console de machine virtuelle | Pour plus d'informations, voir [Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}. |
| Le nouveau certificat de vCenter Server ne semble pas se charger | Après le remplacement des certificats vCenter Server par défaut, il se peut que les nouveaux certificats ne semblent pas se charger. Pour plus d'informations, voir [New vCenter Server Certificate Does Not Appear to Load](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}. |
| vCenter Server n'arrive pas à se connecter aux hôtes gérés | Après le remplacement des certificats vCenter Server par défaut et le redémarrage du système, vCenter Server ne peut plus se connecter aux hôtes gérés. Pour plus d'informations, voir [vCenter Server Cannot Connect to Managed Hosts](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}. |
| Impossible de configurer vSphere HA lors de l'utilisation de certificats SSL personnalisés | Après l'installation des certificats SSL personnalisés, les tentatives d'activation de vSphere High Availability (HA) échouent. Pour plus d'informations, voir [Cannot Configure vSphere HA When Using Custom SSL Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}. |

### Licences
{: #opsprocs-trouble-common-licenses}

Tableau 6. Traitement typique des incidents liés aux licences

| Titre | Description |
|---|---|
|  Configuration de licence incompatible ou incorrecte | Pour plus d'informations, voir [Résolution des problèmes de licence d'hôte](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}. |
| La machine virtuelle ne s'allume pas | Il peut y avoir un problème de licence si vous ne pouvez pas mettre sous tension une machine virtuelle sur un hôte vSphere ESXi et que vous recevez le message ``
La période d'évaluation de 60 jours de l'hôte a expiré ou la licence de l'hôte a expiré``. Pour plus d'informations, voir [Impossible de mettre sous tension une machine virtuelle](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}. |
| Une fonctionnalité n'est pas disponible ou ne permet pas de modifier une configuration  | Pour plus d'informations, voir [Impossible de configurer ou d'utiliser une fonction](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}.  |


## Liens connexes
{: #opsprocs-trouble-links}
* [Contacter le support IBM](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [Troubleshooting Guidelines - KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}
* [Troubleshooting with Log Files - KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window}
* [Gestion des opérations sur {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [Support Log Gathering](https://kb.vmware.com/s/article/1010705){:new_window}
* [Surveillance des événements, des alarmes et actions automatiques](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere System Log Files](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

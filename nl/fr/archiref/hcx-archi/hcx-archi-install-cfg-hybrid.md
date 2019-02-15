---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Installation et configuration de services hybrides

Le programme d'installation met à disposition et configure une machine virtuelle pour chaque dispositif virtuel de service. Les machines virtuelles sont déployées à la fois sur site et dans le cloud.

## Prérequis

* HCX Manager doit être installé sur site et enregistré auprès d'un noeud final du cloud compatible VCF/VCS HCX.
* Le centre de données virtuel cible doit disposer de ressources suffisantes.

## Présentation de la configuration

Le procédure de configuration suppose que tous les dispositifs virtuels de service sont configurés. Ils ne sont cependant pas tous requis.
* La passerelle de cloud hybride est obligatoire.
* L'installation d'une optimisation WAN s'effectue en sélectionnant l'option relative au service d'optimisation WAN durant l'installation. Vous n'avez pas d'autre étape de configuration à effectuer.
* Pour configurer le service d'extension réseau, voir la section _Configuration du service d'extension réseau_. Le déploiement du dispositif est facultatif et peut être reporté en revenant à la page des services hybrides et en installant le dispositif ultérieurement.

## Démarrage de l'installation et de la configuration du dispositif virtuel de service hybride

Une simple interface Web est utilisée pour installer les dispositifs virtuels de service et configurer d'autres concentrateurs de couche 2.

### Prérequis pour l'installation et la configuration du dispositif virtuel de service hybride

HCX Manager doit être installé et enregistré auprès du noeud final du cloud compatible VCF/VCS HCX.

### Procédure pour l'installation et la configuration du dispositif virtuel de service hybride

1. Connectez-vous au client Web vSphere.
2. Sous l'onglet **Accueil**, cliquez sur l'icône **Hybrid Cloud Services**.
3. Cliquez sur l'onglet **Hybrid Services**.
4. Cliquez sur **Install Service**.
5. Sur la page **Choose Hybrid Services**, sélectionnez les services à installer, puis cliquez sur **Next**.

### Etape suivante

1. L'étape suivante consiste à configurer la passerelle de cloud hybride si nécessaire.
2. Un concentrateur de couche 2 peut être ajouté à une installation existante à tout moment si des ressources suffisantes sont disponibles pour prendre en charge l'extension.

## Configuration de la passerelle de cloud hybride

Configurez le dispositif virtuel de service de passerelle de cloud hybride.

### Prérequis pour la configuration de la passerelle de cloud hybride

Suivez les étapes de la section _Démarrage de l'installation et de la configuration du dispositif virtuel de service hybride_ et vérifiez la passerelle de cloud hybride.

### Procédure pour la configuration de la passerelle de cloud hybride

Sur la page **Hybrid Cloud Gateway**, fournissez les valeurs suivantes et cliquez sur **Next**:
* **Network** - Commutateur qui connecte l'interface de gestion de la passerelle de cloud hybride. Dans les cas d'utilisation 1 et 2, il peut s'agir d'un commutateur virtuel standard ou d'un commutateur virtuel distribué. Pour une configuration qui utilise l'extension de couche 2, il doit s'agir d'un commutateur distribué virtuel.
* **Cluster/Host** - Sélectionnez le cluster ou l'hôte où la passerelle cloud doit être déployée.
* **Datastore** - Sélectionnez le magasin de données où déployer la passerelle cloud.
* **VM/Hostname** - Cette valeur est facultative.
* Fournissez l'adresse IP/le CIDR, la passerelle par défaut, ainsi que le serveur DNS à utiliser pour l'interface de gestion de la passerelle cloud.
* Pour entrer plusieurs adresses pour le serveur DNS, séparez-les par des virgules.
* Sous **Extended (optional)**, choisissez le réseau vMotion si applicable, et définissez les mots de passe **admin** et **root**. Ces mots de passe sont spécifiques au dispositif de passerelle de cloud hybride. Le nom d'utilisateur et le mot de passe ne doivent pas être identiques à ceux configurés pour le dispositif Services cloud hybrides.

## Configuration du service d'extension réseau

Configurez un service d'extension réseau pour un déploiement à chemin unique, ou pour une extension réseau autonome sur un chemin secondaire.

### Prérequis pour la configuration du service d'extension réseau

Sélectionnez le service d'extension réseau. Si la configuration à chemin unique est installée, **Network Extension** est la seule option proposée.

### Procédure pour la configuration du service d'extension réseau

1. Sur la page **Network Extension Service**, sélectionnez un commutateur distribué virtuel dans le menu **Distributed Switch**. Lorsque vous installez un concentrateur de couche 2, l'option **Route stretched networks via Hybrid Cloud Gateway** peut être sélectionnée. Ce n'est pas le cas pour L2C haut débit.
2. Si **Route stretched networks via Hybrid Cloud Gateway** est sélectionné, le programme d'installation détermine un emplacement raisonnable pour le concentrateur de couche 2 (en fonction du commutateur) et remplit les informations de placement. Dans le cas contraire, les informations de placement doivent être entrées manuellement à l'étape suivante.
3. Définissez la route pour le placement du concentrateur L2. Si **Route stretched networks via Hybrid Cloud Gateway** a été sélectionné, ces valeurs ne peuvent pas être éditées.
  * **Network** - Réseau de déploiement pour l'interface de gestion du concentrateur de couche 2.
  * **Compute** - Cluster ou hôte de déploiement pour le concentrateur de couche 2.
  * **Datastore** - Magasin de données de déploiement pour le concentrateur de couche 2.
  * **VM/Hostname** - Cette valeur est facultative.
4. Indiquez les paramètres réseau pour le concentrateur de couche 2 local.
  * Si cette option est désactivée, utilisez les paramètres par défaut qui sont fournis par le programme d'installation.
  * Si le groupe de ports sélectionné dans le menu **Network** de la page Hybrid Cloud Gateway ne fait pas partie du commutateur distribué, sélectionnez **Specify the Network Parameters for the local Layer 2 Concentrator** et éditez les zones de texte **Extended Configurations**.
5. (Facultatif) **Extended Configurations** - Définissez les mots de passe **admin** et **root** pour ce concentrateur de couche 2 spécifique.
6. Cliquez sur **Next**. Sur la page **Ready to complete**, passez en revue les informations, puis cliquez sur **Finish**.

## Surveillance du déploiement du dispositif de service

La console de tâches peut être utilisée pour surveiller la progression du déploiement d'une machine virtuelle de service.

### Procédure pour la surveillance du déploiement d'un dispositif de service

1. Connectez-vous au client Web vSphere. Sous l'onglet **Accueil**, cliquez sur l'icône **Hybrid Cloud Services**.
2. Dans le panneau **Hybrid Cloud Services**, cliquez sur l'ongle **Hybrid Services**. Le déploiement de dispositif virtuel peut être surveillé depuis la console des tâches.
3. Accédez au panneau **Recent Tasks** et consultez **All Users’ Tasks**.
4. Cliquez sur **More Tasks** pour ouvrir la console des tâches.
5. Dans la console des tâches, examinez les tâches de déploiement.
6. Une fois toutes les tâches exécutées, accédez à la liste d'inventaire et cliquez sur **Hybrid Cloud Services**.
7. Dans le panneau central, cliquez sur l'onglet **Hybrid Services**.
8. Passez en revue le récapitulatif de configuration pour les dispositifs virtuels de service hybride.

## Affichage de l'état du tunnel

Affichez l'état du tunnel de la passerelle cloud.

### Prérequis pour l'affichage de l'état du tunnel

Le service d'extension réseau doit être préalablement opérationnel pour que l'extension d'un réseau soit possible.

### Procédure pour l'affichage de l'état du tunnel

1. Pour vérifier l'état du tunnel depuis le client Web, sélectionnez **Hybrid Cloud Services** dans l'inventaire, puis cliquez sur l'onglet **Hybrid Services**.
2. Pour confirmer la création d'un tunnel de passerelle de cloud hybride, vérifiez que l'état de CGW (acronyme de Hybrid Cloud Gateway) est **Active**, et complètement à droite, que le tunnel est de couleur verte.

## Extension d'un réseau de couche 2 dans IBM Cloud

Etendez un réseau de couche 2 depuis le centre de données sur site vers un cloud compatible VCF/VCS HCX.

### Prérequis pour l'extension d'un réseau de couche 2 dans IBM Cloud

* Seuls peuvent être étendus les groupes de ports marqués VLAN (autres que le type VLAN None, ou ID VLAN 0). Les réseaux VXLAN sont considérés comme des réseaux VLAN.
* Cette procédure utilise l'assistant d'**extension réseau**. Cet assistant doit être exécuté à partir de la vue d'inventaire réseau du client Web vSphere®. Bien que cet assistant soit visible depuis d'autres vues, il doit être exécuté depuis le contexte d'inventaire pour obtenir les informations correctes.

### Procédure pour étendre un réseau de couche réseau 2 dans IBM Cloud

1. Connectez-vous au client Web vSphere. Sous l'onglet **Home** du panneau central, cliquez sur l'icône **Networking** dans la liste **Inventories**.
2. Dans la hiérarchie **Networking**, identifiez le groupe de ports du réseau à étendre.
3. Cliquez avec le bouton droit de la souris sur le groupe de ports, et dans le menu sélectionnez **Hybridity Actions**, puis **Extend Network**.
4. Sur la page **Select source port groups**, confirmez les informations du groupe de ports et entrez l'**adresse IP de passerelle** ainsi que le préfixe du réseau. Cliquez sur **Next**.
5. Sur la page **Select destination gateway**, effectuez les opérations suivantes :
  1. Sélectionnez VCF/VCS Hybrid Cloud Services Cloud Organization dans le menu **Organization**.
  2. Sélectionnez le centre de données virtuel VCF/VCS Hybrid Cloud Services Cloud dans le menu.
  3. Laissez l'option **Proximity Routing** désactivée afin de forcer une machine virtuelle au sein du cloud VCF/VCS Hybrid Cloud Services afin de pouvoir toujours utiliser la passerelle sur site pour accéder à Internet. Par défaut, le trafic en provenance d'une machine virtuelle dans un cloud compatible VM in VCF/VCS Hybrid Cloud Services traverse le chemin de données de couche 2 vers le centre de données sur site et sort par la passerelle par défaut. Si l'option **Proximity Routing** est sélectionnée, une machine virtuelle au sein du cloud compatible VCF/VCS Hybrid Cloud Services peut accéder à Internet sans avoir à traverser le chemin de données de couche 2 vers vSphere.
  4. Sélectionnez la passerelle de destination distante dans la liste des passerelles en cliquant sur la ligne correspondante. Cliquez sur **Next**.
6. Sur la page **Ready to complete**, passez en revue toutes les valeurs fournies. Cliquez sur **Finish**.
7. Pour suivre la progression de l'extension réseau, accédez à la fenêtre **Recent Tasks**, cliquez sur l'onglet **All**, puis consultez **All Users’ Tasks**.
8. Pour ouvrir la console des tâches, cliquez sur **More Tasks**. L'extension réseau est effectuée lorsque la tâche **Extend Network** est à l'état **Completed**.

### Liens connexes

* [Modification ou désinstallation de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-mod-uninstall.html)

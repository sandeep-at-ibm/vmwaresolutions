---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Glossaire des composants et des termes HCX
{: #vcshcx-components}

HCX se compose d'un côté cloud (cible) et d'un ou de plusieurs clients (source). Une instance de HCX doit être déployée par vCenter, même si les vCenters sur lesquels HCX est déployé sont liés dans le même domaine SSO sur le côté client ou sur le côté cloud. Les configurations qui sont prises en charge par HCX sont : un à un, un à plusieurs, plusieurs à un et plusieurs à plusieurs.

## Côté cloud et côté client
{: #vcshcx-components-cloud-client-side}

HCX utilise le concept de côté cloud (cible) et de côté client (source).
- Côté cloud - vCenter Server on 	{{site.data.keyword.cloud}} with Hybridity Bundle. Le côté cloud de HCX est l'instance esclave d'une relation client-cloud dans HCX. Il est contrôlé par le côté client.
- Côté client - Toute vSphere répondant aux prérequis d'installation et d'opération. Le côté client de HCX est le maître qui contrôle l'instance esclave côté cloud via le snap-in d'interface utilisateur de son client web vCenter.

## HCX Manager
{: #vcshcx-components-hcx-manager}

- Le gestionnaire HCX du côté cloud est le premier composant d'une installation HCX déployée sur le côté cloud par l'automatisation de {{site.data.keyword.vmwaresolutions_short}}.
Il s'agit initialement d'un fichier image OVA déployé unique spécifique au côté cloud et d'un équilibreur de charge/pare-feu NSX Edge qui est configuré spécifiquement pour le rôle HCX. Le gestionnaire HCX est configuré pour écouter les enregistrements entrants côté client, la gestion et le contrôle du trafic.
- Le gestionnaire HCX côté client est un fichier image OVA spécifique au côté client qui fournit la fonctionnalité de l'interface utilisateur pour gérer et faire fonctionner HCX. Le gestionnaire HCX du côté client est responsable de l'enregistrement auprès du gestionnaire HCX du côté cloud et de la création d'un plan de gestion entre le côté client et le côté cloud. De plus, il est responsable de déployer des composants de flotte sur le côté client et de demander au côté cloud de faire la même chose.

## Composants de flotte
{: #vcshcx-components-fleet}

Les composants de flotte HCX sont responsables de la création des données et des plans de contrôle entre le côté client et le côté cloud. Déployés en tant que machines virtuelles dans des paires en miroir, la flotte se compose des composants suivants :

- Cloud Gateway (CGW) - La passerelle Cloud Gateway est un composant facultatif responsable de la création de tunnels chiffrés prenant en charge le trafic VMotion et la réplication (migration en bloc). Une seule paire existe par site HCX lié.
- Concentrateur de couche 2 (L2C) - Le concentrateur de couche 2 est un composant facultatif responsable de la création de tunnels chiffrés pour les données et le plan de contrôle correspondant au trafic de couche 2. Chaque paire de L2C peut traiter jusqu'à 4096 réseaux étendus. Des paires L2C supplémentaires sont déployées en cas de nécessité. La capacité de bande passante est limitée à environ 4 Gbits/s, de sorte que si la capacité de bande passante externe est supérieure à 4 Gbits/s, l'utilisation de paires de L2C supplémentaires permet une plus grande utilisation du réseau sous-jacent.
- Optimiseur de réseau WAN - HCX inclut un dispositif d'optimisation de réseau WAN, Silver Peak™, que vous pouvez déployer en option. Il est déployé en tant que dispositif de machine virtuelle. Lorsqu'il est déployé, le trafic du tunnel de la passerelle CGW est redirigé pour traverser l'optimiseur de réseau WAN. Etant donné que l'optimiseur de réseau WAN réduit drastiquement le trafic à l'intérieur du réseau WAN (une réduction de 3:1 à 6:1 est généralement observée) tout en augmentant la fiabilité de la connexion, il est recommandé de toujours déployer l'optimiseur de réseau WAN avec la passerelle CGW. Un autre avantage du déploiement de l'optimiseur de réseau WAN est la limitation de la bande passante du réseau WAN consommée par le trafic de migration de machine virtuelle. L'interface de gestion de l'optimiseur WAN n'est pas configurée par défaut.
- Hôte ESX de proxy - Lorsque la passerelle CGW est configurée pour se connecter au site HCX du côté cloud, un hôte ESXi de proxy apparaît dans le vCenter en dehors de tout cluster. L'hôte ESXi possède la même adresse IP vMotion et de gestion que le dispositif CGW correspondant. Ceci permet à l'environnement vSphere du côté client et du côté cloud de fonctionner comme pour une vMotion locale. Les avantages de cette méthode sont les suivants :
    - Les plages d'adresses IP de gestion des deux côtés peuvent se chevaucher sans perte de fonctionnalité.
    - Le côté cloud n'a pas de visibilité vSphere sur le côté client, ce qui le rend plus sûr.

## Portails utilisateurs de HCX
{: #vcshcx-components-hcx-user-portals}

- Interface utilisateur Web client - Le portail Web client de HCX est la principale interface utilisateur de HCX. Une fois que le gestionnaire HCX du côté client est installé, il s'affiche sous forme de snap-in dans l'interface utilisateur Web vCenter. Il contrôle l'enregistrement de HCX dans le cloud distant (appariement de site), le déploiement des composants de flotte, l'extension du réseau et la migration des machines virtuelles vers et depuis le cloud.

- Interface utilisateur côté cloud – L'interface utilisateur de HCX côté cloud est accessible via l'URL d'enregistrement public fournie lors de l'enregistrement du client HCX. Par défaut, elle utilise la connexion SSO vSphere côté cloud (` administrator@vsphere.local`). Elle est généralement utilisée pour mettre à niveau l'installation et pour modifier certaines configurations du réseau. Il est également utilisée pour générer des réseaux virtuels au sein de HCX.

- Interface de gestion du dispositif HCX Manager client/cloud - L'accès à l'interface utilisateur de gestion du dispositif du côté cloud ou du côté client s'effectue à travers l'adresse IP privée de la machine virtuelle, telle qu'affichée dans vCenter.`https://<hcxmanager_IP>:9443`. L'ID (généralement “admin”) et le mot de passe sont fournis via le portail {{site.data.keyword.vmwaresolutions_short}}. L'interface utilisateur de gestion est utilisée pour démarrer et arrêter les services de HCX Manager, pour configurer la surveillance des journaux, pour la configuration de réseau de base, pour les mises à niveaux manuelles, la collecte des journaux de support lorsque l'interface utilisateur Web ne fonctionne pas, l'enregistrement auprès des composants vSphere (vCenter, PSC, NSX Manager) et pour la gestion des certificats.

## Liens connexes
{: #vcshcx-components-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   

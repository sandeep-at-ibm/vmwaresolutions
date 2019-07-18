---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

subcollection: vmware-solutions


---

# Glossaire des composants et des termes HCX
{: #hcxclient-components}

HCX se compose d'un côté cloud (cible/environnement VCD) et d'un ou de plusieurs clients (source). Une instance de HCX doit être déployée par vCenter, même si les vCenters sur lesquels HCX est déployé sont liés dans le même domaine SSO sur le côté client ou sur le côté cloud. Les configurations qui sont prises en charge par HCX sont : un à un, un à plusieurs, plusieurs à un et plusieurs à plusieurs.

## Côté cible et côté client
{: #hcxclient-components-cloud-client-side}

HCX utilise le concept de côté cloud (cible/environnement VCD) et de côté client (source).

- Côté cible - HCX Cloud Manager est pré-déployé et configuré avec le réseau et les profils de calcul sont prêts pour la création d’un maillage de service.  
- Côté client - Toute instance vSphere répondant aux prérequis d'installation et d'opération. Le côté client de HCX est le maître qui contrôle l'instance esclave côté cloud via le snap-in d'interface utilisateur de son client web vCenter.

## Gestionnaires HCX
{: #hcxclient-components-hcx-manager}

- Côté cloud - Le gestionnaire HCX Cloud est configuré pour écouter le trafic entrant d'enregistrement, de gestion et de contrôle côté client.
- Côté client - HCX Enterprise Manager est un fichier image OVA spécifique au client qui fournit la fonctionnalité d’interface utilisateur pour la gestion et l’exploitation de HCX. Le gestionnaire HCX du côté client est responsable de l'enregistrement auprès du gestionnaire HCX du côté cloud et de la création d'un plan de gestion entre le côté client et le côté cloud. En outre, il est chargé de déployer un maillage de services côté client et de demander au côté cloud de faire de même.

## Composants du maillage de services
{: #hcxclient-components-fleet}

Les composants du maillage de services HCX sont responsables de la création des données et des plans de contrôle entre le côté client et le côté cloud. Déployés en tant que machines virtuelles dans des paires en miroir, le maillage de services se compose des composants suivants :

- Interconnect Appliance (HCX-IX) - Le dispositif d'interconnexion crée des tunnels chiffrés prenant en charge le trafic vMotion et le trafic de réplication (migration en masse).
- WAN Optimizer Appliance (HCX-WAN) - HCX comprend un dispositif d’optimisation Silver Peak ™ WAN déployé en option. Il est déployé en tant que dispositif de machine virtuelle. Lorsque ce dispositif est déployé, le trafic du tunnel de la passerelle CGW est redirigé pour traverser l'optimiseur de réseau WAN. Etant donné que l'optimiseur de réseau WAN réduit drastiquement le trafic à l'intérieur du réseau WAN (une réduction de 3:1 à 6:1 est généralement observée) tout en augmentant la fiabilité de la connexion, il est recommandé de toujours déployer l'optimiseur de réseau WAN avec la passerelle CGW. Un autre avantage du déploiement de l'optimiseur de réseau WAN est la limitation de la bande passante du réseau WAN consommée par le trafic de migration de machine virtuelle. L'interface de gestion de l'optimiseur WAN n'est pas configurée par défaut.
- Network Extension (HCX-NE) - Fournit les capacités d'extension réseau de couche 2, permettant des migrations entre l'emplacement sur site et l'environnement vSphere avec la nécessité de réaffecter des adresses IP aux machines virtuelles. 
- Hôte ESXi de proxy - Chaque fois que le HCX-IX est configuré pour se connecter au site HCX côté cloud, un hôte ESXi de proxy apparaît dans le vCenter en dehors de tout cluster. L'hôte ESXi possède la même adresse IP vMotion et de gestion que le dispositif HCX-IX correspondant. Ceci permet à l'environnement vSphere du côté client et du côté cloud de fonctionner comme pour une vMotion locale. Les avantages de cette méthode sont les suivants :
  - Les plages d'adresses IP de gestion des deux côtés peuvent se chevaucher sans perte de fonctionnalité.
  - Le côté cloud n'a pas de visibilité vSphere sur le côté client, ce qui le rend plus sûr.

## Portails utilisateurs de HCX
{: #hcxclient-components-hcx-user-portals}

- Interface utilisateur Web client - Le portail Web client de HCX est la principale interface utilisateur de HCX. Une fois que le gestionnaire HCX du côté client est installé, il s'affiche sous forme de snap-in dans l'interface utilisateur Web vCenter. Il contrôle l'enregistrement de HCX dans le cloud distant (appariement de site), le déploiement des composants de flotte, l'extension du réseau et la migration des machines virtuelles vers et depuis le cloud.
- Interface utilisateur côté cloud – L'interface utilisateur de HCX côté cloud est accessible via l'URL d'enregistrement public fournie lors de l'enregistrement du client HCX. Par défaut, elle utilise les données d'identification Admin de vCenter côté cloud `administrator@vsphere.local`. Elle est généralement utilisée pour mettre à niveau l'installation et pour modifier certaines configurations du réseau.

## Liens connexes
{: #hcxclient-components-related}

* [Conditions d'accès au port pour VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Déploiement du client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Maillage de services sur site HCX ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Traitement des incidents dans HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

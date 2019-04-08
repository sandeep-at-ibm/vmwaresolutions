---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# Préparation de l'environnement d'installation
{: #hcx-archi-prep-install}

L'installation de VMware HCX on IBM Cloud exige la configuration logicielle suivante :
* vSphere 5.5 U3 ou vSphere 6.0u2 ou supérieur.
* Si NSX est utilisé, version 6.2.2 ou supérieure. NSX est requis pour la migration de politique.
* Pour utiliser une migration vMotion entre clouds, les mêmes restrictions d'affinité s'appliquent entre les clouds comme c'est le cas en local. Pour plus d'informations, voir [Foire aux questions relatives à la compatibilité entre VMware EVC et UC](http://bit.ly/2vK6Sp5).

## Configuration de la connectivité du réseau
{: #hcx-archi-prep-install-config-net}

HCX doit traverser l'Internet public et des lignes privées, et se connecter à des composants de centre de données, comme des réseaux, des commutateurs et des groupes de ports.
* La section [Accès aux ports requis](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req) répertorie les ports qui doivent être ouverts afin que des dispositifs virtuels HCX puissent être installés.
* L'environnement vSphere local et l'environnement VCF/VCS HCX Cloud doivent permettre une synchronisation des horloges NTP (Network Time Protocol) entre les unités vSphere locales et les unités VCF/VCS HCX. Le port UDP 123 doit être accessible aux dispositifs virtuels et aux réseaux HCX.

## Environnement local
{: #hcx-archi-prep-install-on-prem-env}

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
{: #hcx-archi-prep-install-verify-layer-2-inst}

L'extension de réseau de couche 2 doit respecter les règles suivantes :
* vSphere édition Enterprise Plus.
* vSphere vCenter doit respecter les exigences suivantes pour prendre en charge une extension de couche 2 :
  * Licence vSphere Enterprise Plus
  * vSphere Distributed Switch (vDS) Obligatoire. Ce commutateur distribué est fourni avec vSphere Enterprise Plus Edition.
  * Une fois installé, le dispositif de service du concentrateur local de couche 2 doit avoir accès à un port vNIC et aux réseaux VLAN à étendre.
  * Si le réseau doit être étendu sur l'Internet public ou un réseau VPN (dans un chemin secondaire), la machine virtuelle L2C dans VCF/VCS requiert une adresse IP. L'adresse IP distante est obligatoire pour configurer le concentrateur de couche 2.
  * Si plusieurs concentrateurs de couche 2 sont nécessaires, chacun doit avoir une adresse IP en local et dans le cloud.

## Liens connexes
{: #hcx-archi-prep-install-related}

* [Installation et configuration de HCX sur la source](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [Foire aux questions relatives à la compatibilité entre VMware EVC et UC](http://bit.ly/2vK6Sp5)

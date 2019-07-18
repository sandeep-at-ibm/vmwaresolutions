---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---
# Conditions d'accès au port pour VMware HCX on IBM Cloud
{: #hcx-archi-port-req}

HCX doit traverser l'Internet public et des lignes privées, et se connecter à des composants de centre de données, comme des réseaux, des commutateurs et des groupes de ports.

Le tableau ci-après répertorie les ports qui doivent être ouverts de manière à permettre l'installation de dispositifs virtuels Services cloud hybrides. L'environnement vSphere et l'environnement IBM Cloud doivent permettre une synchronisation des horloges NTP (Network Time Protocol) entre les unités vSphere locales et les unités IBM Cloud. Le port UDP 123 doit être accessible aux dispositifs virtuels et aux réseaux Services cloud hybrides. Les serveurs NTP installés peuvent être spécifiés lors de l'installation des dispositifs de service Services cloud hybrides.

Table 1. Accès aux ports requis

| Source | Cible       | Port | Protocole | Objectif         | Services |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | DNS client | 53   | TCP/UDP  | Résolution nom | DNS      |
| HCX    | NSX LB dans IBM Cloud | 443 | TCP | Service d'enregistrement | HTTPS |
| HCX    | vCenter dans IBM Cloud | 443 | TCP | Service REST HCX | HTTPS |
| HCX    | PSC dans IBM Cloud | 443 | TCP | Service REST HCX | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Service d'enregistrement | HTTPS |
| Navigateur Web | HCX | 9443 | TCP | Interface de gestion de dispositif virtuel HCX pour la configuration système HCX | HTTPS |
| Réseau admin | HCX | 22 | SSH | Accès SSH administrateur aux Services cloud hybrides | SSH |
| HCX | Hôtes ESXi | 902 | TCP | Envoi d'instruction de gestion et de mise à disposition des hôtes HCX aux hôtes ESXi dans IBM Cloud. | Interne |
| HCX | Serveur SSO vCenter | 7444 | TCP | Service de recherche vSphere |  |
| HCX | Serveurs NTP | 123 | UDP | Synchronisation d'horloge | |
| HCX | Syslog |   | Configuré par l'utilisateur | Connexion entre HCX (le client) et le serveur Syslog. Les valeurs pour le port et le protocole Syslog sont spécifiées dans le client Web vSphere. Par exemple, le port 514 pour le protocole UDP. | |
| HCX | Passerelle cloud | 8123 | TCP | Envoi d'instructions de service de réplication basé sur l'hôte à la passerelle cloud hybride. | HTTP |
| HCX | Passerelle cloud | 9443 | TCP | Envoi d'instructions de gestion à la passerelle de cloud hybride à l'aide de l'API REST. | HTTP</br>HTTPS |
| Passerelle cloud | L2C | 443 | TCP | Envoi d'instructions de gestion de la passerelle cloud à L2C lorsque L2C utilise le même chemin que la passerelle de cloud hybride. | HTTP</br>HTTPS |
| Passerelle cloud | L2C | 8443 | TCP | Instructions de gestion bidirectionnelle de la passerelle cloud vers L2C, lorsque L2C utilise un autre chemin de données. | HTTP</br>HTTPS |
| L2C | L2C (distant) | 443 | TCP | Instructions de gestion bidirectionnelle de la passerelle cloud vers L2C, lorsque L2C utilise un autre chemin de données. | HTTP</br>HTTPS |
| Passerelle cloud | Hôtes ESXi | 80, 902  | TCP | Gestion et déploiement OVF | Interne |
| Hôtes ESXi | Passerelle cloud | 31031, 44046 | TCP | Trafic de réplication basée sur l'hôte interne | Interne |
| Passerelle cloud | Hôtes ESXi | 8000  | TCP | vMotion (migration sans interruption) |  |
| Passerelle cloud (locale) | Passerelle cloud </br>(distante) | 4500  | UDP | Echange de clés Internet (IKEv2) pour l'encapsulage des charges de travail pour le tunnel bidirectionnel | IPSEC |
| Passerelle cloud (locale) | Passerelle cloud </br>(distante) | 500  | UDP | Echange de clés Internet (ISAKMP) pour le tunnel bidirectionnel | IPSEC |

## Liens connexes
{: #hcx-archi-port-req-related}

* [Installation et configuration de HCX sur la source](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)

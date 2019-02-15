---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de HyTrust DataControl on IBM Cloud

Le service HyTrust DataControl on {{site.data.keyword.cloud}} offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service fournit un chiffrement au niveau du système d'exploitation et au niveau des données. Cela permet à n'importe quel répertoire, dossier ou fichier d'une charge de travail d'être chiffré et déchiffré.

Ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. La version de HyTrust DataControl qui est installée est la version 4.2.1.
{:note}

## Spécifications techniques relatives à HyTrust DataControl on IBM Cloud

Les composants suivants sont commandés et inclus dans le service HyTrust DataControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust DataControl
* UC : 2 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 20 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité
Deux dispositifs DataControl déployés dans une configuration active-active

### Licences et frais

Licence par hôte : une licence HyTrust DataControl est commandée pour chaque hôte de l'environnement

## Considérations à prendre en compte lorsque vous retirez HyTrust DataControl on IBM Cloud

Avant de retirer le service HyTrust DataControl on {{site.data.keyword.cloud_notm}}, dissociez tous les clients pour qu'il n'utilisent pas DataControl. Après avoir retiré le service, les clés peuvent être supprimées et vous risquez de ne plus pouvoir accéder à vos machines virtuelles.

### Liens connexes

* [Commande de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_ordering.html)
* [Gestion de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghtdc.html)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HyTrust KeyControl, HTKC, tech specs HTKC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de HyTrust KeyControl on IBM Cloud
{: #htkc_considerations}

Le service HyTrust KeyControl on {{site.data.keyword.cloud}} simplifie la gestion des charges de travail chiffrées. Ce service automatise et simplifie le cycle de vie des clés de chiffrement et comprend le stockage, la distribution, la rotation et la révocation des clés. Lorsqu'elles utilisent le chiffrement compatible FIPS 140-2, les entreprises peuvent facilement gérer des clés de chiffrement à grande échelle.

Ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.5 ou des éditions ultérieures. La version de HyTrust KeyControl qui est installée est la version 4.3.2.
{:note}

## Spécifications techniques relatives à HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-specs}

Les composants suivants sont commandés et inclus dans le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust KeyControl
{: #htkc_considerations-appliance}

* UC : 2 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 20 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité
{: #htkc_considerations-ha}

Par défaut, deux dispositifs KeyControl sont déployés dans une configuration en cluster active-active.

Vous pouvez éventuellement indiquer que deux dispositifs KeyControl doivent être déployés dans une configuration autonome autre qu'une configuration en cluster.

### Licences et frais
{: #htkc_considerations-licenses}

Une licence HyTrust KeyControl est commandée pour chaque installation d'instance.

## Remarques relatives au retrait de HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-remove}

Avant de retirer le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, prenez soin de dissocier tous les clients de l'utilisation de KeyControl. Après avoir retiré le service, les clés peuvent être supprimées et vous risquez de ne plus pouvoir accéder à vos machines virtuelles.

## Liens connexes
{: #htkc_considerations-related}

* [Commande de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [Gestion de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web HyTrust](https://www.hytrust.com/){:external}
